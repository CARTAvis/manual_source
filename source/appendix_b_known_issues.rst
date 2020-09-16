Appendix B: known issues
========================
CARTA has the following known issues for the release v1.4 (updated up to September 17, 2020). 

The CARTA development team plans to address most of the following issues in the next release (v1.5).

Stability and performace
^^^^^^^^^^^^^^^^^^^^^^^^
* the desktop instance got killed when killing a remote mode instance (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/1179>`_)
* shortcuts conflict when using CARTA in the remote mode (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/1143>`_)
* cursor update for profiles stops during zoom (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/544>`_)
* performance impact of AST grid tolerance to wide field images (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/451>`_)


File browser
^^^^^^^^^^^^
* File list scrolling broken in Firefox (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/1159>`_)
* Fits file doesn't load when header doesn't adhere to fits standard (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/596>`_)
* Re-open image probably uses cache (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/579>`_)
* CARTA freezes when file browser is openend during file change (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/578>`_)
* casacore processed headers when exceptions happen (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/460>`_)
* CARTA hangs in file info gathering step (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/431>`_)
* TabularCoordinate - start and end values in table must differ (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/373>`_)
* HDF5 files with a non-float main dataset are not supported (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/77>`_)



Animator
^^^^^^^^
* missing tiles when animation stops (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/954>`_)
* frame label and other info out of sync with image change when animating between frames (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/815>`_)
* a flash with missing tiles then full image restored when we press stop to stop animation (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/794>`_)
* incomplete contour rendering when stop animating (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/579>`_)
* Synchronise contour and raster data when animating (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/569>`_)
* Req index and Current index in animator (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/424>`_)
* mis-aligned range index with current index in the animator (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/399>`_)
* backend stops responding when stop animating raster+contour images (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/366>`_)


Histogram
^^^^^^^^^
* rounding histogram widget axis value floating points (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/985>`_)


Image viewer
^^^^^^^^^^^^
* missing raster image when zooming in edge pixels (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/948>`_)
* show empty sky if no tile is requested when switching between spatially matched images (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/819>`_)
* panning and zooming of spatially matched images is odd if image has very different FoV to reference (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/719>`_)
* Show correct beam for multi-beam images (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/697>`_)
* incorrect "AUTO" coordinate system when loading image as new (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/582>`_)


Stokes analysis
^^^^^^^^^^^^^^^
* missing grid lines when zooming the Q vs U scatter plot in the Stokes widget (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/578>`_)


Region of interest
^^^^^^^^^^^^^^^^^^
* detached region control point for rotation (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/1208>`_)
* region rendering precision at high(er) zoom level (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/949>`_)
* symmetric creation/modification of a region with side anchor and shift key (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/308>`_)
* position offset seen in exported region (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/541>`_)
* Cannot import ICRS regions to FK5 image (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/528>`_)
* regions away from the reference pixel are distorted and give the wrong pixel count (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/389>`_)


Catalogue
^^^^^^^^^
* catalog: region creation mode is not activated immediately by click when catalog selection mode is enabled (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/961>`_)
* blurry catalog overlay on Retina display (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/889>`_)
* Problem with read RA and Dec of FITS(ascii) (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/624>`_)


GUI
^^^
* Broken help button when catalog-histogram and catalog-scatter widgets are docked (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/1210>`_)
* Red indicator of profile is out of bound (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/1191>`_)
* safari specific: spatial profiler not resized properly (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/970>`_) **CRITICAL** to Safari users
* keyboard event conflict between image viewer and drop down menu (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/758>`_)
* floating widget cannot be moved to new location if its content is updating (spectral profile) (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/482>`_)
* x range of profile widget (spatial/spectral) when open a new image (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/463>`_)
* Zooming in a profile in point style results in empty plot (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/453>`_)
* draggable marker should be stopped when out of chart (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/152>`_)






