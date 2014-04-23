## Installing binary libraries shareable with the environment
(From Rich) Install the binary libraries in the python lib directory for that custom env. So, the steps are:

1. Create "ioos" env
2. Install binary library:

```
./configure --prefix=/opt/anaconda/envs/ioos
make install
```

## Rich and Ed Campbell's method to create a `scitools` environment for Cartopy and Iris
1. see https://github.com/esc24/installation-recipes/blob/78e4b70345c0d093bc2a68f747ad464f584f648e/wakari/install.txt for detailed instructions.
2. I created an Ipython Notebook demonstrating the use of Iris and Cartopy to access forecast model data from the US Integrated Ocean Observing System (US-IOOS) here:
https://www.wakari.io/sharing/bundle/rsignell/scitools

You should be able to just click the link, copy over the bundle with environment to their Wakari instance (5 min instructional video I made here, in case it's not clear: https://www.youtube.com/watch?v=4NyMWK4as-U)

## Emilio's steps to create an IOOS environment 
- *4/23/2014 update: After a major, disruptive Wakari update, I've now replaced the old conda package specs list with a new one called 'ioos_em_11.condaspec'. The instructions below have been updated.*
- *2/20/2014 update: I'm not sure if the environment name used internally is exposed in notebooks that bundle environments, but I've updated my Wakari environment to pyoos 0.6. The new env is called `ioos_em_11`; the build instructions below will still work, and the new env is bundled with the notebook at the end of this page.*

====================================


This Python 2.7 / Numpy 1.7 / Anaconda 1.5 Wakari environment includes:

- Base scientific packages: `numpy, scipy, matplotlib, basemap, pandas, netcdf4, hdf5`
- Base geospatial packages: `gdal/ogr, shapely, pyshp, geos, fiona`
- IOOS-relevant data and metadata access packages: `OWSLib, paegan, pyoos, ulmo,  SPARQLWrapper, rdfLib`
- Others (many brought in as dependencies): IPython (of course!), datetime handling (`dateutil, isotime, pytz`), `lxml, requests, suds, beautifulsoup4, html5lib, mock`

[Scitools](http://scitools.org.uk/) (IRIS, cartopy) is **the major gap** compared to Rich's environment. I would also like to add THREDDS catalog parsing libraries (https://github.com/Unidata/pyudl and/or https://github.com/asascience-open/thredds_crawler). I'm working on it...

To create the environment, I first created a baseline list of specific conda packages (with specific versions) based on an existing environment (`ioos_em_11`). Following Rich's instructions, I created [a conda package specs list](https://github.com/ioos/ipython-notebooks/blob/master/wakarispecs/ioos_em_11.condaspec) like this:
```
source activate ioos_em_11
conda list -e | tee ioos_em_11.condaspec
source deactivate
```
Then, to use [this specification](https://github.com/ioos/ipython-notebooks/blob/master/wakarispecs/ioos_em_11.condaspec) to create the new environment `ioos_em_10`:

1. Start a regular shell terminal. Create a new directory to store the environment and everything involving it. Use the spec file to install all conda packages:
```
mkdir $HOME/ioos_em_10_env
cd $HOME/ioos_em_10_env
wget https://raw2.github.com/ioos/ipython-notebooks/master/wakarispecs/ioos_em_11.condaspec
conda create --name ioos_em_10 --file $HOME/ioos_em_5.condaspec
```

2. Activate the new environment in the same shell terminal:
```
source activate ioos_em_10
```

3. `pip install` paegan and pyoos (will install other dependencies, including OWSLib). Ignore the many warnings that scroll by! Note these must be installed from their github repos.
```
pip install git+https://github.com/asascience-open/paegan.git
pip install git+https://github.com/asascience-open/pyoos.git
```

4. `pip install` other packages, from pypi:
```
pip install SPARQLWrapper
pip install ulmo
pip install pyshp pyke
```

That's it. Enjoy. Remember the environment is `ioos_em_10`, unless you changed the name. [You can install it on Wakari by running this notebook bundle that includes the environment](https://www.wakari.io/sharing/bundle/emayorga/pyoos_ioos_sos_demo1); but note (2014-4-23) there's a chance the environment bundled in that notebook is actually out of date!
