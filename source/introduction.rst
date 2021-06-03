Introduction
============

The mission of CARTA
--------------------
CARTA is the *Cube Analysis and Rendering Tool for Astronomy*, a new image visualization and analysis tool designed for the ALMA, the VLA, and the SKA pathfinders - MeerKAT and ASKAP. As the image size increases dramatically with modern telescopes in recent years, viewing an image with a local image viewer or with a remote image viewer via the ssh protocol plus X11 tunneling or the VNC becomes much less efficient. The mission of CARTA is to provide usability and scalability for the future by utilizing modern web technologies and computing parallelization. 

Client-Server architecture
--------------------------
CARTA uses a client-server architecture which is suitable for visualizing images with large file sizes (GB to TB) easily obtained from ALMA, VLA, or SKA pathfinders (MeerKAT and ASKAP) observations. It is practically difficult to process such a huge file with a personal computer or laptop. By using a client-server architecture, computation and data storage are handled by remote enterprise-class servers or clusters with high computing power and high performance storage, while processed products are sent to clients only for visualization with modern web features, such as GPU-accelerated rendering. This architecture also enables users to visualize images from  the ALMA and the VLA science archives by using CARTA as an interface. 


.. raw:: html

   <img src="_static/carta_intro_serverClient.png" 
        style="width:100%;height:auto;">


Codebase and releases
---------------------
CARTA is an open-source project. Its source code is publicly available at https://github.com/CARTAvis. 

CARTA has two deployment modes: "Site Deployment Mode" (SDM) and "User Deployment Mode" (UDM). The former is intended for hosting multiple users with an enterprise-class server, while the later is intended for single-user usage with a personal computer, a laptop, or a remote server. 

Installation guides for the "Site Deployment Mode" and the "User Deployment Mode" are provided in the section :ref:`installation_configuration`. Please contact the `CARTA Helpdesk <carta_helpdesk@asiaa.sinica.edu.tw>`_ (carta_helpdesk@asiaa.sinica.edu.tw) if there is a problem. 

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

* v1.3: WCS matching (released 31st March 2020)

  * Contour rendering
  * Raster image matching in world coordinates
  * Contour image matching in world coordinates
  * Image matching in spectral domain
  * Drag-to-pan support
  * Spectral conversion in the spectral profiler
  * Enhanced usability with “Active” region type
  * Enhanced “remote” mode
  * Optional low-bandwidth mode for poor network connections
  * Offline in-app help manual
  * Bug fixes and performance improvements


* v1.4: Catalogue overlay and analysis tools (released 17th September 2020)

  * Catalogue support
  * Shared region analytics
  * Animation playback improvement of raster and contour images
  * Profile smoothing
  * Moment map generator
  * Spectral line query
  * Server authentication and deployment improvements
  * File browser improvements
  * Bug fixes and performance improvements

  
* v2.0: Feature enhancement and codebase maintenance (**current release**, released 7th June 2021) 

  * Multi-profile plot with the spectral profiler
  * Progress report and cancellation when requesting a long file list
  * Forming a Stokes hypercube at image loading stage
  * Colorbar display in the image viewer and enhanced raster image config widget
  * Support rectangular pixel rendering for PV image
  * Filtering function in the spectral line query widget
  * Enhanced FITS and CASA image support
  * Saving subimage
  * Searching a keyword from image header
  * Profile fitting in the spectral profiler 
  * Marker-based catalog rendering and performance enhancement
  * New deployment modes


* Into the future (this is a non-exclusive list of features that we would like to implement in subsequent releases but these are not decided upon yet, and depend on feedback from users, and resourcing etc. )

  * Multi-panel view
  * Channel map view
  * Position-velocity map generator
  * Server collaborative tools
  * Vector field (polarization) rendeting
  * Volume (pseudo-3D) rendering
  * Profile and histogram fitting tool
  * Image (2D) fitting tool
  * Scripting interface with Python3
  * Three-color (RGB) image blender
  * Angular distance measuring tool
  * Image source finder
  * Online image query (VO)
  * Online catalog query (VO)
  * Publication quality export (images)
  * Image arithmetic

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
**[TODO]** Please use the following DOI as a citation when using CARTA for publications.

.. image:: https://zenodo.org/badge/DOI/10.5281/zenodo.3377984.svg
   :target: https://doi.org/10.5281/zenodo.3377984

The bibtex is

.. code-block:: bibtex
   
   @software{angus_comrie_2018_3377984,
   author       = {Angus Comrie and
                  Kuo-Song Wang and
                  Pamela Harris and
                  Anthony Moraghan and
                  Shou-Chieh Hsu and
                  Adrianna Pińska and
                  Cheng-Chin Chiang and
                  Hengtai Jan and
                  Rob Simmonds and
                  Tien-Hao Chang and
                  Ming-Yi Lin},
   title        = {{CARTA: The Cube Analysis and Rendering Tool for 
                   Astronomy}},
   month        = dec,
   year         = 2018,
   publisher    = {Zenodo},
   doi          = {10.5281/zenodo.3377984},
   url          = {https://doi.org/10.5281/zenodo.3377984}
   }


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
* GoogleTest: https://github.com/google/googletest
* gRPC: https://grpc.io/
* GSL: https://www.gnu.org/software/gsl/
* MobX: https://mobx.js.org
* MongoDB: https://www.mongodb.com
* node.js: https://nodejs.org
* Plotly: https://plotly.com
* Protocol buffers: https://developers.google.com/protocol-buffers 
* Pugixml: https://pugixml.org
* React: https://reactjs.org
* spdlog: https://github.com/gabime/spdlog
* sse2neon: https://github.com/DLTcollab/sse2neon
* TBB: https://www.threadingbuildingblocks.org
* uWebsockets: https://github.com/uNetworking/uWebSockets
* WebAssembly: https://webassembly.org


The source code of CARTA is hosted on `Github <https://github.com/CARTAvis>`_.

The CARTA development team is grateful to David Berry for consultation of the AST library and to Kumar Golap for consultation of the casacore library.

Copyright and License
---------------------
Copyright (C) 2018-2021 ASIAA, IDIA, NRAO, and Department of Physics, University of Alberta. This program is free software; you can redistribute it and/or modify it under the terms of the `GNU General Public License version 3 <http://www.gnu.org/copyleft/gpl.html>`_ as published by the Free Software Foundation.
