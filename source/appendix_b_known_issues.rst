Appendix B: known issues
========================
CARTA has the following known issues for the release v1.1. The CARTA development team will try to fix them in coming releases. The list is updated up to May 1, 2019. 



Stability and performace
^^^^^^^^^^^^^^^^^^^^^^^^
* performance degradation of images with per-plane-beam (`GitHub issue <https://github.com/CARTAvis/nrao-carta-backend/issues/46>`_)

* backend crash when close file but threads are still running (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/19>`_)

* HDF5 files should be opened in read mode, not write mode (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/87>`_)

* HDF5 files with a non-float main dataset are not supported (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/77>`_)

* HDF5 file stays open if reading main dataset in file info loader fails (`GitHub issue <https://github.com/CARTAvis/carta-backend/issues/76>`_)

Image viewer
^^^^^^^^^^^^
* no update on image cursor values when switching stokes or channel (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/150>`_)

Animator
^^^^^^^^
* no radio button is checked (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/108>`_)


Region of interest
^^^^^^^^^^^^^^^^^^
* symmetric creation/modification of a region with side anchor and shift key (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/308>`_)


Misc.
^^^^^
* Export image: long names not fully visible in the Save As field (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/130>`_)




