Appendix B: known issues
========================
CARTA has the following known issues for the release v2.0 (updated up to June 7, 2020). 

The CARTA development team plans to address these issues in coming releases.

Stability and performance
^^^^^^^^^^^^^^^^^^^^^^^^^
* `Optimize spatial matched catalog performance <https://github.com/CARTAvis/carta-frontend/issues/1432>`_
* `Optimize catalog map calculation <https://github.com/CARTAvis/carta-frontend/issues/1426>`_
* `frontend crash when loading a 1x1 pixel image <https://github.com/CARTAvis/carta-frontend/issues/1365>`_
* `Frontend chokes when loading region files with a large number of regions <https://github.com/CARTAvis/carta-frontend/issues/1252>`_
* `cursor update for profiles stops during zoom <https://github.com/CARTAvis/carta-frontend/issues/544>`_
* `performance impact of AST grid tolerance to wide field images <https://github.com/CARTAvis/carta-frontend/issues/451>`_
* `backend crash when enable multiple profile plot <https://github.com/CARTAvis/carta-backend/issues/825>`_
* `backend crash when attempting to load a per-plane-beam cube as new while the current one is animating <https://github.com/CARTAvis/carta-backend/issues/774>`_
* `CARTA hangs when attempting double-click to load an image with long header <https://github.com/CARTAvis/carta-backend/issues/768>`_
* `backend crash when cancelling moment calculations with per-plane-beam cube <https://github.com/CARTAvis/carta-backend/issues/652>`_
* `Regex causes seg fault with 6000-point polygon <https://github.com/CARTAvis/carta-backend/issues/649>`_


Spectral profiler
^^^^^^^^^^^^^^^^^
* `progress indicator of the spectral profiler <https://github.com/CARTAvis/carta-frontend/issues/1429>`_ 


Spectral line query
^^^^^^^^^^^^^^^^^^^
* `spectral line label off by one channel? <https://github.com/CARTAvis/carta-frontend/issues/1327>`_


Spatial profiler
^^^^^^^^^^^^^^^^
* `world coordinate offset in the spatial profiler <https://github.com/CARTAvis/carta-frontend/issues/1319>`_


File browser
^^^^^^^^^^^^
* `non-ideal state when we load another image from a folder with lots of files <https://github.com/CARTAvis/carta-frontend/issues/1425>`_
* `hdf5 header entry OBSGEO-X, OBSGEO-Y & OBSGEO-Z does not always match to fits header entry <https://github.com/CARTAvis/carta-backend/issues/779>`_
* `CARTA freezes when file browser is opened during file change <https://github.com/CARTAvis/carta-backend/issues/578>`_
* `Re-open image probably uses cache <https://github.com/CARTAvis/carta-backend/issues/579>`_
* `casacore processed headers when exceptions happen <https://github.com/CARTAvis/carta-backend/issues/460>`_
* `Hdf5 and CASA Images with a non-float main dataset are not supported <https://github.com/CARTAvis/carta-backend/issues/77>`_

Animator
^^^^^^^^
* `frame label and other info out of sync with image change when animating between frames <https://github.com/CARTAvis/carta-frontend/issues/815>`_
* `a flash with missing tiles then full image restored when we press stop to stop animation <https://github.com/CARTAvis/carta-frontend/issues/794>`_
* `incomplete contour rendering when stop animating <https://github.com/CARTAvis/carta-frontend/issues/579>`_
* `Synchronise contour and raster data when animating <https://github.com/CARTAvis/carta-frontend/issues/569>`_


Image viewer
^^^^^^^^^^^^
* `missing tiles when animation stops <https://github.com/CARTAvis/carta-frontend/issues/954>`_
* `missing raster image when zooming in edge pixels <https://github.com/CARTAvis/carta-frontend/issues/948>`_
* `show empty sky if no tile is requested when switching between spatially matched images <https://github.com/CARTAvis/carta-frontend/issues/819>`_
* `panning and zooming of spatially matched images is odd if image has very different FoV to reference <https://github.com/CARTAvis/carta-frontend/issues/719>`_
* `edge pixels artifacts on the right side <https://github.com/CARTAvis/carta-frontend/issues/666>`_
* `incorrect "AUTO" coordinate system when loading image as new <https://github.com/CARTAvis/carta-frontend/issues/582>`_


Stokes analysis
^^^^^^^^^^^^^^^
* `stokes scatter plot point indicator not working <https://github.com/CARTAvis/carta-frontend/issues/1313>`_


Region of interest
^^^^^^^^^^^^^^^^^^
* `region list: center transformation error for matched image and size conversion accuracy <https://github.com/CARTAvis/carta-frontend/issues/1293>`_
* `side control points of a region not at the middle of a side <https://github.com/CARTAvis/carta-frontend/issues/1278>`_
* `detached region control point for rotation <https://github.com/CARTAvis/carta-frontend/issues/1208>`_
* `region rendering precision at high(er) zoom level <https://github.com/CARTAvis/carta-frontend/issues/949>`_
* `Cannot import ICRS regions to FK5 image <https://github.com/CARTAvis/carta-backend/issues/528>`_
* `regions away from the reference pixel are distorted and give the wrong pixel count <https://github.com/CARTAvis/carta-backend/issues/389>`_

Catalog
^^^^^^^
* `Catalog overlay not updating after first 100K data chunk returned with Safari <https://github.com/CARTAvis/carta-frontend/issues/1417>`_


GUI
^^^
* `detached header search field <https://github.com/CARTAvis/carta-frontend/issues/1459>`_
* `layout with blank panel <https://github.com/CARTAvis/carta-frontend/issues/1387>`_
* `Popovers displayed on top of the splash screen <https://github.com/CARTAvis/carta-frontend/issues/1346>`_
* `workaround for BlueprintJS column resizing bug <https://github.com/CARTAvis/carta-frontend/issues/1304>`_
* `Safari only bug with CARTA icon in reconnection splash screen (when hosting frontend via backend) <https://github.com/CARTAvis/carta-frontend/issues/1296>`_
* `safari specific: spatial profiler not resized properly <https://github.com/CARTAvis/carta-frontend/issues/970>`_
* `keyboard event conflict between image viewer and drop down menu <https://github.com/CARTAvis/carta-frontend/issues/758>`_
* `floating widget cannot be moved to new location if its content is updating (spectral profile) <https://github.com/CARTAvis/carta-frontend/issues/482>`_
* `inconsistent spectralMatchingType in preferences schema and GUI <https://github.com/CARTAvis/carta-frontend/issues/1352>`_
* `rounding histogram widget axis value floating points <https://github.com/CARTAvis/carta-frontend/issues/985>`_
* `crowded indices of the frame axis in the animator <https://github.com/CARTAvis/carta-frontend/issues/940>`_
* `mis-aligned range index with current index in the animator <https://github.com/CARTAvis/carta-frontend/issues/399>`_
* `draggable marker should be stopped when out of chart <https://github.com/CARTAvis/carta-frontend/issues/152>`_


