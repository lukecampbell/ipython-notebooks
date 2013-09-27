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
