Here's what Emilio did to create his environment.

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

Rich did pretty much the same thing to install Cartopy, with a few differences.  One issue was creating static versions of libraries that were not on the system and had to built locally.  Luckily libgeos was not a problem because it was on the system, but proj4 required special treatment.  In a Wakari shell terminal, I did:

```
conda create -n ioos_env dateutil=1.5 pandas matplotlib netcdf4 ipython shapely cython pip pytz
```
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
python setup.py build
python setup.py install
```
