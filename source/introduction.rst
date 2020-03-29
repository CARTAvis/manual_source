Introduction
============

The mission of CARTA
--------------------
CARTA is the *Cube Analysis and Rendering Tool for Astronomy*, a new image visualization and analysis tool designed for the ALMA, the VLA, and the SKA pathfinders - MeerKAT and ASKAP. As the image size increases drastically with modern telescopes in recent years, viewing an image with a local image viewer or with a remote image viewer via the ssh protocol plus X11 tunneling or the VNC becomes much less efficient. The mission of CARTA is to provide usability and scalability for the future by utilizing modern web technologies and computing parallelization. 

Client-Server architecture
--------------------------
CARTA uses a client-server architecture which is suitable for visualizing images with large file sizes (GB to TB) easily obtained from ALMA, VLA, or SKA pathfinders (MeerKAT and ASKAP) observations. It is practically difficult to process such a huge file with personal computer or laptop. By using a client-server architecture, computation and data storage are handled by remote enterprise-class servers or clusters with high performance storage, while processed products are sent to clients only for visualization with modern web features, such as GPU-accelerated rendering. This architecture also enables users to interact with the ALMA and VLA science archives by using CARTA as an interface. 


.. raw:: html

   <img src="_static/carta_intro_serverClient.png" 
        style="width:100%;height:auto;">

Codebase and releases
---------------------
CARTA is an open-source project. Its source code is available at https://github.com/CARTAvis. 

CARTA has two flavors: CARTA-server and CARTA-desktop. The former is intended for hosting multiple users with an enterprise-class server, while the later is intedned for single-user usage with a personal computer or a laptop. The desktop version can also be used in the "remote" mode, where the backend (server) is run in a remote server and the frontend (client) is run locally with an internet browser. 

Deployment of CARTA in a server environment may require addtional efforts of server configurations, such as user authentication, server load balance, or resource monitoring, etc. Please contact the `CARTA Helpdesk <carta_helpdesk@asiaa.sinica.edu.tw>`_ (carta_helpdesk@asiaa.sinica.edu.tw) for consultations. 

Installation guides for the desktop version are provided in the section :ref:`installation_configuration`, including the usages of the remote mode. 

The release plan and major goals are the following:

* v1.0: Basic image and profile viewing capability (released 29th December 2018)

* v1.1: Initial support of region of interest, ROI (released 2nd May 2019)

  * basic ROI for single image including rectangle and ellipse
  * ROI statistics
  * ROI spectral profile
  * ROI histogram
  * HDF5-IDIA image format support
  * Improved remote version
  * Performance and memory usage improvements

* v1.2: performance and usability improvement (released 28th August 2019)

  * New server authentication method
  * User preferences and layouts
  * Tiled rendering and animator enhancement
  * support point and polygon regions
  * support region import/export in crtf syntax
  * introducing enhanced profile delivery strategies 
  * new Stokes analysis widget
  * support HDF5 images under IDIA schema

* v1.3: WCS matching (**current release**)

  * Contour rendering
  * WCS matching
  * Tiled animation
  * Active region
  * Spectral conversion
  * In-app help
  * Improved remote mode
  * Initial touchscreen support
  * Bug fixes and performance improvements

* v1.4: Catalogue overlay and analysis tools (subject to change)

  * Catalogue overlay
  * WCS region of interest
  * Animator improvement
  * Mip map support in HDF5 (IDIA schema) format
  * Initial support of scripting interface in Python3
  * Server-side authentication improvements
  * Profile smoothing
  * Moment map generator
  * Line catalogue overlay


Getting help
------------
The CARTA team welcomes any suggestion, feature request, or bug report, to make CARTA better via 

* `CARTA Helpdesk <carta_helpdesk@asiaa.sinica.edu.tw>`_ (carta_helpdesk@asiaa.sinica.edu.tw) 
* `Github Issue <https://github.com/CARTAvis/carta/issues>`_ (https://github.com/CARTAvis/carta/issues)


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


Software citation
-----------------
Please use the following DOI as a citation when using CARTA for publications.

.. image:: https://zenodo.org/badge/DOI/10.5281/zenodo.3377984.svg
   :target: https://doi.org/10.5281/zenodo.3377984



Acknowledgement
---------------
ASIAA CASA Development Center (ACDC) acknowledges the grant from the Ministry of Science and Technology of Taiwan for the ALMA-NA collaboration.

The Inter-University Institute for Data Intensive Astronomy is a partnership of three South African universities: the University of Cape Town, the University of the Western Cape and the University of Pretoria.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under cooperative agreement by Associated Universities, Inc.

The Department of Physics at the University of Alberta has contributed to the CARTA project thanks to support from the National Radio Astronomy Observatory under an ALMA Development Project and from the Canada Foundation for Innovation as part of the Canadian Initiative for Radio Astronomy Data Analysis (CIRADA).

CARTA is mainly built in C++, TypeScript, and JavaScript, and with the following third-party libraries:

* AST: http://starlink.eao.hawaii.edu/starlink/AST
* Blueprint: https://blueprintjs.com
* casacore: https://casacore.github.io
* CASA source code: https://casa.nrao.edu/index.shtml
* Chart.js: https://www.chartjs.org
* Electron: https://electronjs.org
* GoldenLayout: https://golden-layout.com
* jsoncpp: https://github.com/open-source-parsers/jsoncpp
* MobX: https://mobx.js.org
* MongoDB: https://www.mongodb.com
* React: https://reactjs.org
* TBB: https://www.threadingbuildingblocks.org


The source code of CARTA is hosted on `Github <https://github.com/CARTAvis>`_.

The CARTA development team is grateful to David Berry for consultation of the AST library and to Kumar Golap for consultation of the casacore library.

Copyright and License
---------------------
Copyright (C) 2018-2020 ASIAA, IDIA, NRAO, and Department of Physics, University of Alberta. This program is free software; you can redistribute it and/or modify it under the terms of the `GNU General Public License version 3 <http://www.gnu.org/copyleft/gpl.html>`_ as published by the Free Software Foundation.
