Adventures with Wakari. 

Rich and We've made a lot of progress, but the path is littered with blood and tears. Fortunately for you, that's blood and tears we'll be sparing everyone else.

A brief list of the packages we've got going and have been able to share with each other via custom-built environments:
scipy, numpy, matplotlib, pandas, netcdf4, shapely, OWSLib, lxml, suds, requests, SPARQLWrapper, ulmo, cartopy
Here I didn't list lower-level dependencies.

I have an environment that includes all of those packages except cartopy. Rich has one with cartopy, but not lxml, suds, requests, SPARQLWrapper, ulmo. Rich is working on IRIS.

paegan (and therefore pyoos) so far is a no go, but we haven't tried very hard.

We have several public IPython notebooks that you can access and run if you have a Wakari account. 

With my environment ("ioos_em_2"):

1. Access this notebook bundle that will install my environment:
The notebook demos ulmo, accessing USGS river level via CUAHSI HIS services:
https://www.wakari.io/sharing/bundle/emayorga/ulmo_usgsdata_viacuahsi

Once you have that env installed, you can run these two notebooks (make sure to select the ioos_em_2 environment):

2. NDBC SOS access with OWSLib. Pretty basic, mostly following on Kyle's examples at the OWSLib site.
https://www.wakari.io/sharing/bundle/emayorga/OWSLibSOSAccess_Test1

3. "Semantic" querying of the MMI-hosted IOOS Parameter Vocabulary, showing mapping to CF terms.
Taken directly from Sara Haines' github IPython notebook.
https://www.wakari.io/sharing/bundle/emayorga/SPARQLWrapper_MMI_IOOSParameterVocabTerm

You can still see the IPython statements and results for each of these notebooks, even if you don't have a wakari account.

With my environment you can also run a notebook that Rich put together, accessing a CSW catalog and from there grabbing and plotting data from a THREDDS server:
https://www.wakari.io/sharing/bundle/emayorga/CSW_Testing_ISO_Queryables-USGS-EM
