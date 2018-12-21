Appendix B: known issues
========================
CARTA has the following known issues for the release v1.0. The CARTA development team will try to fix them in coming releases. The list is updated up to December 21, 2018.



Stability and performace
^^^^^^^^^^^^^^^^^^^^^^^^
.. raw:: html

   <img src="_static/carta_bug.png" 
        style="width:10%;height:auto;">


* memory leak when stepping through channels (`GitHub issue <https://github.com/CARTAvis/nrao-carta-backend/issues/41>`_)

* memory leak when calculating cube histogram (`GitHub issue <https://github.com/CARTAvis/nrao-carta-backend/issues/42>`_)

File browser
^^^^^^^^^^^^
.. raw:: html

   <img src="_static/carta_noBug.png" 
        style="width:10%;height:auto;">

Image viewer
^^^^^^^^^^^^
.. raw:: html

   <img src="_static/carta_bug.png" 
        style="width:10%;height:auto;">


* backend crashes when multiple sessions access same dataset (`GitHub issue <https://github.com/CARTAvis/nrao-carta-backend/issues/17>`_)

* backend crash when close file but threads are still running (`GitHub issue <https://github.com/CARTAvis/nrao-carta-backend/issues/19>`_)

* artifacts when using very large line widths in AST overlay (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/120>`_)

* incorrect native coordinate when reopening an image (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/73>`_)

Animator
^^^^^^^^
* no radio button is checked (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/108>`_)


Render configuration
^^^^^^^^^^^^^^^^^^^^
.. raw:: html

   <img src="_static/carta_noBug.png" 
        style="width:10%;height:auto;">


Spectral profiler
^^^^^^^^^^^^^^^^^
.. raw:: html

   <img src="_static/carta_noBug.png" 
        style="width:10%;height:auto;">


Spatial profiler
^^^^^^^^^^^^^^^^
.. raw:: html

   <img src="_static/carta_noBug.png" 
        style="width:10%;height:auto;">


GUI
^^^
.. raw:: html

   <img src="_static/carta_noBug.png" 
        style="width:10%;height:auto;">



Misc.
^^^^^
.. raw:: html

   <img src="_static/carta_bug.png" 
        style="width:10%;height:auto;">


* Export image: long names not fully visible in the Save As field (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/130>`_)

* no png image is saved (`GitHub issue <https://github.com/CARTAvis/carta-frontend/issues/102>`_)



