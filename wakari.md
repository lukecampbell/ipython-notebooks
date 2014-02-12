# Adventures with Wakari

Wakari is a cloud-hosted scientific python environment you can access via your browser.  And pretty reasonable size accounts are totally free.

A brief list of the packages we've got going and have been able to share with each other via custom-built environments:
scipy, numpy, matplotlib, pandas, netcdf4, shapely, OWSLib, lxml, suds, requests, SPARQLWrapper, ulmo, cartopy
We aren't listing the lower-level dependencies.

* Emilio has an environment that includes all of those packages except cartopy. [Emilio's shared notebooks and bundles](www.wakari.io/emayorga)

* Rich has one with cartopy, but not lxml, suds, requests, SPARQLWrapper, ulmo. [Rich's shared notebooks and bundles](www.wakari.io/rsignell)

* Rich is working on IRIS.

* paegan (and therefore pyoos) so far is a no go, but we haven't tried very hard.

##  IPython notebooks that you can access and run 

* Access this notebook bundle that will install my ulmo/OWSLib environment, and demonstrates ulmo, accessing USGS river level via CUAHSI HIS services.
https://www.wakari.io/sharing/bundle/emayorga/ulmo_usgsdata_viacuahsi

Once you have that env installed, you can run the following notebooks, just make sure to select the `ulmo_usgsdata_viacuahsi` environment 
when you run the notebook.  You can also make that environment your default environment.  See Wakari help.

* NDBC SOS access with OWSLib. Pretty basic, mostly following on Kyle's examples at the OWSLib site.
https://www.wakari.io/sharing/bundle/emayorga/OWSLibSOSAccess_Test1

* "Semantic" querying of the MMI-hosted IOOS Parameter Vocabulary, showing mapping to CF terms.
Taken directly from Sara Haines' github IPython notebook.
https://www.wakari.io/sharing/bundle/emayorga/SPARQLWrapper_MMI_IOOSParameterVocabTerm

* Access a CSW catalog and from there grab and plot data from a THREDDS server:
https://www.wakari.io/sharing/bundle/emayorga/CSW_Testing_ISO_Queryables-USGS-EM

* Run a simple Cartopy example (mapping)
https://www.wakari.io/sharing/bundle/rsignell/cartopy_test  
(for this notebook you need to use the supplied `cartopy_test` environment)

Even if you don't feel like signing up for a free Wakari account, you can still see the IPython statements and results for each of these notebooks.

