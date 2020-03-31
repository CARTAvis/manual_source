Appendix B: known issues
========================
CARTA has the following known issues for the release v1.3. The CARTA development team will try to fix them in coming releases. The list is updated up to March 31, 2020. 



Stability and performace
^^^^^^^^^^^^^^^^^^^^^^^^
* cursor update for profiles stops during zoom (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/544>`_)
* performance impact of AST grid tolerance to wide field images (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/451>`_)


File browser
^^^^^^^^^^^^
* Some FITS files with multiple HDUs can't be opened in CARTA (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/476>`_)
* casacore processed headers when exceptions happen (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/460>`_)
* Regression: Opening certain files results in invalid WCS (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/436>`_)
* CARTA hangs in file info gathering step (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/431>`_)
* TabularCoordinate - start and end values in table must differ (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/373>`_)
* HDF5 files with a non-float main dataset are not supported (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/77>`_)



Animator
^^^^^^^^
* frame label and other info out of sync with image change when animating between frames (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/815>`_)
* incomplete contour rendering when stop animating (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/579>`_)
* Synchronise contour and raster data when animating (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/569>`_)
* no radio button is checked (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/108>`_)
* Req index and Current index in animator (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/424>`_)
* mis-aligned range index with current index in the animator (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/399>`_)
* backend keeps streaming image data repeatedly after animation has stopped (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/420>`_)
* backend stops responding when stop animating raster+contour images (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/366>`_)



Contour configuration
^^^^^^^^^^^^^^^^^^^^^
* contour level generator still generates levels when parameters are not properly set (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/840>`_)


Image viewer
^^^^^^^^^^^^
* show empty sky if no tile is requested when switching between spatially matched images (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/819>`_)
* panning and zooming of spatially matched images is odd if image has very different FoV to reference (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/719>`_)
* Show correct beam for multi-beam images (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/697>`_)
* incorrect "AUTO" coordinate system when loading image as new (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/582>`_)


Spectral profiler
^^^^^^^^^^^^^^^^^
* unit of y axis in the spectral profile with different statistics (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/699>`_)


Stokes analysis
^^^^^^^^^^^^^^^
* missing grid lines when zooming the Q vs U scatter plot in the Stokes widget (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/578>`_)


Region of interest
^^^^^^^^^^^^^^^^^^
* Render imported regions based on their color definitions if exist (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/831>`_)
* Cannot export regions when image has invalid or non-existent WCS headers (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/334>`_)
* symmetric creation/modification of a region with side anchor and shift key (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/308>`_)
* regions away from the reference pixel are distorted and give the wrong pixel count (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/389>`_)
* Cannot import/export regions when image has invalid or non-existent WCS headers (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/334>`_)




GUI
^^^
* reload get blank frontend layout when backend is lost (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/833>`_)
* keyboard event conflict between image viewer and drop down menu (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/758>`_)
* floating widget cannot be moved to new location if its content is updating (spectral profile) (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/482>`_)
* x range of profile widget (spatial/spectral) when open a new image (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/463>`_)
* Zooming in a profile in point style results in empty plot (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/453>`_)
* [dynamic layout] raster view turns black when switching layouts during animation (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/416>`_)
* draggable marker should be stopped when out of chart (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/152>`_)






