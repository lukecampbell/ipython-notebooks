## Installing binary libraries shareable with the environment
(From Rich) Install the binary libraries in the python lib directory for that custom env. So, the steps are:

1. Create "ioos" env
2. Install binary library:

```
./configure --prefix=/opt/anaconda/envs/ioos
make install
```

## Emilio's method to create an environment for `ulmo`
1. In Wakari, click the "Terminals" tab, then choose "Shell" from the left dropdown menu, and "np17py27-1.5" from the right dropdown menu.  Then click the "+Tab" button to create a np17py27-1.5 Shell in a new tab.

2. In this new terminal (should say "shell:np17py27-1.5:/user_home/<your username>" at the top), create a new conda environment with all the conda packages you need:
```
conda create -n ioos_em_2 python=2.7 numpy=1.7 dateutil=1.5 lxml=3.2.3 six=1.4.1 matplotlib pandas scipy netcdf4 shapely ipython pyzmq pyparsing requests pytz pip
```
3. Log out, log back in. 
4. Create a shell terminal using the new env, and then click the "gear" icon in the upper right and set your new env as the default env. 
5. Then install non-conda packages via PIP:
```
pip install OWSLib   # Successfully installed OWSLib
pip install SPARQLWrapper   # Successfully installed SPARQLWrapper rdflib isodate html5lib
pip install ulmo   # Successfully installed ulmo appdirs beautifulsoup4 mock suds
```

6. Create a notebook and select this new environment from the dropdown inside the notebook page.   When you then share this notebook (by clicking the "Share" button next to the notebook name in the file browser), you will have the opportunity to include the custom environment.

## Rich's method to create an environment for `Cartopy`
Rich did pretty much the same thing as Emilio with a few differences.  

* A different basic conda environment:

```
conda create -n ioos_env dateutil=1.5 pandas matplotlib netcdf4 ipython shapely cython pip pytz geos shapely
```

* Handling of addiitional library dependencies. 
Cartopy has a dependency on the proj4 library that was not on the system and had to built locally (can't just do sudo install libproj-dev) on wakari.
So with help from Ed Campbell, in a Wakari shell terminal, I did:

```
pip install pyshp
cd $HOME
mkdir proj4_static
mkdir ioos
cd ioos
wget http://download.osgeo.org/proj/proj-4.8.0.tar.gz
tar xvfz proj-4.8.0.tar.gz
cd proj4-4.8.0
CFLAGS=-fPIC ./configure --disable-shared --prefix=$HOME/proj4_static
make install
cd ..
git clone https://github.com/SciTools/cartopy.git
cd cartopy
python setup.py build_ext -L$HOME/proj4_static/lib -I$HOME/proj4_static/include
python setup.py install
```

Installing udunits

```
cd $HOME
wget ftp://ftp.unidata.ucar.edu/pub/udunits/udunits-2.1.24.tar.gz
tar xzf udunits-2.1.24.tar.gz
cd udunits
./configure --prefix=$HOME/udunits_shared
make install
cd $HOME && rm -rf udunits udunits-2.1.24.tar.gz
```

Installing Iris
```
pip install pyke
cd $HOME
git clone https://github.com/SciTools/iris.git
cd iris
cp lib/iris/etc/site.cfg.template lib/iris/etc/site.cfg
# **edit lib/iris/etc/site.cfg such that:**
cat lib/iris/etc/site.cfg
[System]
udunits2_path = /user_home/w_pelson/udunits_shared/lib/libudunits2.so

python setup.py std_names
# Remove the custom build_py command - it is failing for no good reason (bug in Iris/Distutils?)
python setup.py build
python setup.py install
```

# Rich Trying again with Iris:

Create a terminal using the np17py27-1.5 environment, and then in that terminal, type:
```
conda create -n iris dateutil=1.5 pandas matplotlib netcdf4 ipython shapely cython pip pytz scipy lxml nose sphinx hdf5 zlib curl distribute libpng
```
log out, log back in, create a terminal using the "iris" environment

click the gear icon and set the default environment to Iris.

Create a terminal in the "iris environment. 

Then do:
```
mkdir iris
cd iris
wget -O cartopy.v0.9.0.tgz https://github.com/SciTools/cartopy/archive/v0.9.0.tar.gz
tar xvfz cartopy.v0.9.9.tgz

wget http://download.osgeo.org/proj/proj-4.8.0.tar.gz
tar xvfz proj-4.8.0.tar.gz
cd proj-4.8.0
./configure --prefix=/opt/anaconda/envs/iris
make install
```



