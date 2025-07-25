Online data query
=================
The Online Data Query Dialog provies an interface to query and retrieve astronomical catalog data and image data from remote services. Currently it supports catalog query from

* `SIMBAD <https://simbad.u-strasbg.fr>`_
* `VizieR <https://vizier.cds.unistra.fr>`_

and image data query from 

* `HiPS2FITS <https://alasky.cds.unistra.fr/hips-image-services/hips2fits>`_.

You can retrieve a catalog for visualization via the Catalog Widget (see :ref:`catalog_widget` for details) or retrieve an image for visualization in the Image Viewer.


SIMBAD catalog query
--------------------
With "SIMBAD" selected as the database in the Catalog tab, you can query the `SIMBAD <https://simbad.u-strasbg.fr>`_ database by providing

* (optional) Object name to be resolved for setting the search center
* Search radius
* Search center

The search radius can be defined by providing a value in degree, arcminute, or arcsecond.  Similarly, the search center can be defined by providing coordinates in the selected WCS reference frame (default is AUTO, refering to the definition in the image header of the active image).

The "Set to viewer" button will set the search radius *and* the search center to the current view in the Image Viewer, providing a convenient way to query the catalog data in the current view. The "Reset to current view center" button will set the search center coordinates to the current view center.

The "Max number of objects" input field allows you to limit the number of objects returned from the query. The default value is 1000. By clicking the "Query" button, the catalog data will be retrieved from the SIMBAD service and displayed in the Catalog Widget.


.. raw:: html

   <a href="_static/carta_fn_onlineDataQuery_SIMBAD.png" target="_blank">
       <img src="_static/carta_fn_onlineDataQuery_SIMBAD.png" 
           style="width:80%;height:auto;">
   </a>




VizieR catalog query
--------------------
With "VizieR" selected as the database in the Catalog tab, you can query the `VizieR <https://vizier.cds.unistra.fr>`_ database by providing

* (Optional) Keywords for searching catalog titles
* (Optional) Object name to be resolved for setting the search center
* Search radius
* Search center

The search radius can be defined by providing a value in degree, arcminute, or arcsecond.  Similarly, the search center can be defined by providing coordinates in the selected WCS reference frame (default is AUTO, refering to the definition in the image header of the active image).

The "Set to viewer" button will set the search radius *and* the search center to the current view in the Image Viewer, providing a convenient way to query the catalog data in the current view. The "Reset to current view center" button will set the search center coordinates to the current view center.

The "Max number of objects per catalog" input field allows you to limit the number of objects *per catalog* returned from the query. The default value is 1000. 

There are three steps to retrieve catalog data from the VizieR service after setting up the search parameters:

1. By clicking the "Query" button, a set of catalog titles will be retrieved. 
  
   .. raw:: html

     <a href="_static/carta_fn_onlineDataQuery_VizieR_step1.png" target="_blank">
       <img src="_static/carta_fn_onlineDataQuery_VizieR_step1.png" 
           style="width:80%;height:auto;">
     </a>

2. By clicking the "VizieR catalog" input field, you can select a set of catalogs from the list of retrieved catalog titles as the targets for the retrieving catalog data. 

   .. raw:: html

     <a href="_static/carta_fn_onlineDataQuery_VizieR_step2.png" target="_blank">
       <img src="_static/carta_fn_onlineDataQuery_VizieR_step2.png" 
           style="width:80%;height:auto;">
     </a>


3. Finally, by clicking the "Load selected" button, the catalog data will be retrieved from the VizieR service and displayed in the Catalog Widget. 

   .. raw:: html

     <a href="_static/carta_fn_onlineDataQuery_VizieR_step3.png" target="_blank">
       <img src="_static/carta_fn_onlineDataQuery_VizieR_step3.png" 
           style="width:80%;height:auto;">
     </a>



HiPS2FITS image query
---------------------
The "HiPS2FITS" tab provides an interface to query and retrieve image data from the `HiPS2FITS <https://alasky.cds.unistra.fr/hips-image-services/hips2fits>`_ service. You can query the HiPS2FITS service by providing

* A title of the HiPS survey: the input field accepts a string of the survey title (e.g., :code:`ESAVO/P/HERSCHEL/PACS100`, see `HiPS list <https://aladin.cds.unistra.fr/hips/list>`_) or select one from the dropdown list after entering a string for partial match.
* A center: either by an object name matching or by entering ICRS coordinates in degrees.
* Image size in pixels: note that for each dimension, at least 5 pixels are required. In total, the number of pixels must be less than 50 million pixels.
* A size of field of view in degrees. The corresponding angular size of a pixel is displayed as well.
* The output WCS coordinate system: ICRS or Galactic.
* A projection scheme. 
* A sky rotation angle in degrees.

Once all the parameters are set, you can click the "Query" button to retrieve the image data from the HiPS2FITS service. The retrieved image will be displayed in the Image Viewer.

.. raw:: html

   <a href="_static/carta_fn_onlineDataQuery_HiPS2FITS.png" target="_blank">
       <img src="_static/carta_fn_onlineDataQuery_HiPS2FITS.png" 
           style="width:80%;height:auto;">
   </a>

You can save the retrived image data in FITS or CASA format via the "File" -> "Save Image" menu. 