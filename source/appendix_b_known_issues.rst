Appendix B: known issues
========================
CARTA has the following known issues for the release v1.2. The CARTA development team will try to fix them in coming releases. The list is updated up to August 28, 2019. 



Stability and performace
^^^^^^^^^^^^^^^^^^^^^^^^
* performance degradation of images with per-plane-beam (`GitHub issue <https://github.com/CARTAvis/nrao-carta-backend/issues/46>`_)
* backend crash when close file but threads are still running (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/19>`_)
* HDF5 files with a non-float main dataset are not supported (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/77>`_)
* performance impact of AST grid tolerance to wide field images (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/451>`_)


Animator
^^^^^^^^
* no radio button is checked (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/108>`_)
* Req index and Current index in animator (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/424>`_)
* mis-aligned range index with current index in the animator (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/399>`_)


Region of interest
^^^^^^^^^^^^^^^^^^
* Cannot export regions when image has invalid or non-existent WCS headers (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/334>`_)
* Regions entirely outside image cannot be imported or exported (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/320>`_)
* symmetric creation/modification of a region with side anchor and shift key (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/308>`_)
* cannot create a polygon if users click too fast (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/443>`_)

GUI
^^^
* floating widget cannot be moved to new location if its content is updating (spectral profile) (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/482>`_)
* x range of profile widget (spatial/spectral) when open a new image (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/463>`_)
* Zooming in a profile in point style results in empty plot (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/453>`_)
* [dynamic layout] raster view turns black when switching layouts during animation (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/416>`_)
* dropdown indicator is not visible in "light" theme (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/405>`_)
* draggable marker should be stopped when out of chart (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/152>`_)


Misc.
^^^^^
* Export image: long names not fully visible in the Save As field (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/130>`_)




