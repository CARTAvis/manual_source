Appendix B: known issues
========================
CARTA has the following known issues for the release v3.0 (updated up to August 23rd, 2022). 

The CARTA development team plans to address these issues in coming releases.



Stability and performance
^^^^^^^^^^^^^^^^^^^^^^^^^
* `CARTA crashes when using beam tables with 64-bit floats <https://github.com/CARTAvis/carta-backend/issues/1166>`_
* `performance impact of AST grid tolerance to wide field images <https://github.com/CARTAvis/carta-frontend/issues/451>`_
* `backend crash when enable multiple profile plot <https://github.com/CARTAvis/carta-backend/issues/825>`_


Spectral profiler
^^^^^^^^^^^^^^^^^
* `unable to convert Jy/beam to K if the spectral axis is VRAD but converting to FREQ is possible <https://github.com/CARTAvis/carta-frontend/issues/1907>`_
* `cursor info of the spectral profiler widget when profile smoothing is enabled <https://github.com/CARTAvis/carta-frontend/issues/1880>`_



Spectral line query
^^^^^^^^^^^^^^^^^^^
* `spectral line label off by one channel? <https://github.com/CARTAvis/carta-frontend/issues/1327>`_


Spatial profiler
^^^^^^^^^^^^^^^^
* `backend crash related to spatial profiler <https://github.com/CARTAvis/carta-backend/issues/1102>`_
* `corrupted spatial profile when cursor is moving <https://github.com/CARTAvis/carta-frontend/issues/1602>`_
* `mean and rms do not update after smoothing <https://github.com/CARTAvis/carta-frontend/issues/1838>`
* `Show smoothed values in the cursor info of the spatial profiler when profile smoothing is applied <https://github.com/CARTAvis/carta-frontend/issues/1937>`_
* `world coordinate offset in the spatial profiler <https://github.com/CARTAvis/carta-frontend/issues/1319>`_


Vector overlay dialog
^^^^^^^^^^^^^^^^^^^^^
* `annoying text input fields in the vector rendering dialog <https://github.com/CARTAvis/carta-frontend/issues/1906>`_


File browser
^^^^^^^^^^^^
* `Cannot handle pixel values >~3e38 (v3.0.0-beta.2b) <https://github.com/CARTAvis/carta-backend/issues/1136>`_
* `rock n roll file header box <https://github.com/CARTAvis/carta-frontend/issues/1684>`_
* `Ability to render older AIPS cubes with FELO-HEL velocity axis <https://github.com/CARTAvis/carta-frontend/issues/1771>`_
* `Hdf5 and CASA Images with a non-float main dataset are not supported <https://github.com/CARTAvis/carta-backend/issues/77>`_
* `performance impact to the file browser when trying to export regions from a large set of regions <https://github.com/CARTAvis/carta-frontend/issues/1867>`_


Animator
^^^^^^^^
* `odd small pixel tiles seen in hdf5 image after animation stops <https://github.com/CARTAvis/carta-frontend/issues/1846>`_
* `animation playback with matched contour images and multi-panel view <https://github.com/CARTAvis/carta-frontend/issues/1860>`_
* `a flash with missing tiles then full image restored when we press stop to stop animation <https://github.com/CARTAvis/carta-frontend/issues/794>`_
* `incomplete contour rendering when stop animating <https://github.com/CARTAvis/carta-frontend/issues/579>`_
* `Synchronise contour and raster data when animating <https://github.com/CARTAvis/carta-frontend/issues/569>`_


Image viewer
^^^^^^^^^^^^
* `weird 4x4 patterns in raster image due to zfp compression <https://github.com/CARTAvis/carta-frontend/issues/1223>`_
* `Overlay's coordinate system should be independent between images <https://github.com/CARTAvis/carta-frontend/issues/1619>`_
* `Rotation of line region anchors on non-square pixel images <https://github.com/CARTAvis/carta-frontend/issues/1732>`_
* `spatial matching error seen in sub-milliarcsecond scale images <https://github.com/CARTAvis/carta-frontend/issues/1734>`_
* `jumpy pv image with drag-and-drop <https://github.com/CARTAvis/carta-frontend/issues/1790>`_
* `Regions not selectable near the bottom of the window <https://github.com/CARTAvis/carta-frontend/issues/1794>`_
* `NaN* pixel value in the cursor info bar of the image viewer when the image is 1x1 pixel <https://github.com/CARTAvis/carta-frontend/issues/1879>`_
* `Update image view mode when catalog selection button is disabled <https://github.com/CARTAvis/carta-frontend/issues/1967>`_
* `missing tiles when animation stops <https://github.com/CARTAvis/carta-frontend/issues/954>`_
* `missing raster image when zooming in edge pixels <https://github.com/CARTAvis/carta-frontend/issues/948>`_
* `show empty sky if no tile is requested when switching between spatially matched images <https://github.com/CARTAvis/carta-frontend/issues/819>`_
* `panning and zooming of spatially matched images is odd if image has very different FoV to reference <https://github.com/CARTAvis/carta-frontend/issues/719>`_
* `incorrect "AUTO" coordinate system when loading image as new <https://github.com/CARTAvis/carta-frontend/issues/582>`_



Region of interest
^^^^^^^^^^^^^^^^^^
* `Error importing region files when extension missing <https://github.com/CARTAvis/carta-backend/issues/1182>`_
* `raster image rendering precision at high(er) zoom level <https://github.com/CARTAvis/carta-frontend/issues/949>`_


Catalog
^^^^^^^
* `regression: cannot load large catalog <https://github.com/CARTAvis/carta-frontend/issues/1652>`_
* `The size of catalog overlay on Apple M1 and with Retina display <https://github.com/CARTAvis/carta-frontend/issues/1662>`_
* `only enable catalog selection button when there is a layer of catalog overlay <https://github.com/CARTAvis/carta-frontend/issues/1826>`
* `better precision handling of xy tick values in the catalog scatter and histogram plots <https://github.com/CARTAvis/carta-frontend/issues/1884>`_

Online catalog query
^^^^^^^^^^^^^^^^^^^^
* `Simbad dist calculation has ~0.01-0.1 arcsec difference <https://github.com/CARTAvis/carta-frontend/issues/1669>`_

GUI
^^^
* `detached header search field <https://github.com/CARTAvis/carta-frontend/issues/1459>`_
* `layout with blank panel <https://github.com/CARTAvis/carta-frontend/issues/1387>`_
* `workaround for BlueprintJS column resizing bug <https://github.com/CARTAvis/carta-frontend/issues/1304>`_
* `Safari only bug with CARTA icon in reconnection splash screen (when hosting frontend via backend) <https://github.com/CARTAvis/carta-frontend/issues/1296>`_
* `keyboard event conflict between image viewer and drop down menu <https://github.com/CARTAvis/carta-frontend/issues/758>`_
* `floating widget cannot be moved to new location if its content is updating (spectral profile) <https://github.com/CARTAvis/carta-frontend/issues/482>`_
* `draggable marker should be stopped when out of chart <https://github.com/CARTAvis/carta-frontend/issues/152>`_


Misc.
^^^^^
* `missing casacore log in carta.log <https://github.com/CARTAvis/carta-backend/issues/1169>`_
* `Double-escaped URL parameters when file argument contains special characters <https://github.com/CARTAvis/carta-frontend/issues/1862>`_
* `Opening a CASA image with a trailing / using the URL parameter doesn't work properly <https://github.com/CARTAvis/carta-frontend/issues/1816>`_