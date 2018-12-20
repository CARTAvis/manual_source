Introduction
============

The mission of CARTA
--------------------
CARTA is the *Cube Analysis and Rendering Tool for Astronomy*, a new image visualization and analysis tool designed for the ALMA, the JVLA, and the radio telescopes of the future such as the SKA. As the image size increases drastically with modern telecscopes in recent years, contemporary image viewers face performance issues which degrade user experience significantly. The mission of CARTA is to resolve this and provide usability and scalability for the future by utilizing modern web technologies and computing parallelization.

Client-Server architecture
--------------------------
CARTA uses a client-server architecture which is suitable for visualizing images with large file sizes (GB to TB) easily obtained from ALMA or JVLA observations. It is practically difficult to process such a huge file with personal computer or laptop. By using a client-server architecture, computation and data storage are handled by remote enterprise-class servers or clusters with high performance storage, while processed products are sent to clients only for visualization with modern web features, such as GPU-accelerated rendering. This architecture also enables users to interact with the ALMA and JVLA science archives by using CARTA as an interface. 


.. raw:: html

   <img src="_static/carta_intro_serverClient.png" 
        style="width:100%;height:auto;">

Codebase and releases
---------------------
CARTA is an open-source project. Its source code is available at https://github.com/CARTAvis. 

CARTA has two distributions: CARTA-server and CARTA-desktop. The former is designed for handling large datasets with remote servers, while the later is suitable for smaller datasets (a few thousand pixels in the x and y dimensions) which can still be handled with personal computer or laptop. Installation guides for these two versions are provided in the section :ref:`installation_configuration`.

The release plan and major goals are the following:

* Version 1.0: current release, including basic image and profile  viewing capability.
* Version 1.1: basic region of interest (ROI) support and relevant analysis tools (statistics, histogram, and profilers).
* Version 1.2: WCS group support which allows multiple images to be aligned in spatial and spectral domains.
* Version 1.3: multiple-panel view
* Version 1.4: moments image, position-velocity image, and scripting interface
* Version 1.5: interactive clean
* Version 1.6: collaborative mode
* Version 1.7+: misc.


Getting help
------------
The CARTA team welcomes any suggestion, feature request, or bug report, to make CARTA better via the `CARTA Helpdesk <carta_helpdesk@asiaa.sinica.edu.tw>`_.



Contributors
------------
The development of the CARTA project is a joint effort from (in alphabetical order):

* `Academia Sinica, Institute of Astronomy and Astrophysics (ASIAA) <https://www.asiaa.sinica.edu.tw>`_
* `Inter-university Institute for Data Intensive Astronomy (IDIA) <https://idia.ac.za>`_
* `National Radio Astronomy Observatory (NRAO) <https://science.nrao.edu>`_
* `Department of Physics, University of Alberta <https://www.ualberta.ca/physics>`_


.. raw:: html

   <img src="_static/carta_wg_logo.png" 
        style="width:100%;height:auto;">


Acknowledgement
---------------
ASIAA CASA Development Center (ACDC) acknowledges the grant from the Ministry of Science and Technology of Taiwan for the ALMA-NA collaboration.

The Inter-University Institute for Data Intensive Astronomy is a partnership of three South African universities: the University of Cape Town, the University of the Western Cape and the University of Pretoria.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

CARTA is mainly built in C++, TypeScript, and JavaScript, and with the following third-party libraries:

* AST: http://starlink.eao.hawaii.edu/starlink/AST
* Blueprint: https://blueprintjs.com
* casacore: https://casacore.github.io
* Chart.js: https://www.chartjs.org
* Electron: https://electronjs.org
* GoldenLayout: https://golden-layout.com
* MobX: https://mobx.js.org
* React: https://reactjs.org
* TBB: https://www.threadingbuildingblocks.org

.. * HDF5: https://www.hdfgroup.org/solutions/hdf5


The source code of CARTA is hosted on `Github <https://github.com/CARTAvis>`_.



Copyright and License
---------------------
