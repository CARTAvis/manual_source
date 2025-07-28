Introduction
============

CARTA development scope
-----------------------
CARTA, *Cube Analysis and Rendering Tool for Astronomy*, is an image visualization and analysis tool designed for the ALMA, the VLA, and the SKA pathfinders - MeerKAT and ASKAP as well as the SKA as it evolves. CARTA is designed to be a modern, web-based, and high-performance image viewer for large astronomical data cubes, which are often in the range of gigabytes to multi-terabytes in size. As the image size increases dramatically with modern telescopes in the past decade or so, viewing an image with a local CPU-based image viewer or with a remote CPU-based image viewer via the SSH protocol plus X11 tunneling or the VNC becomes much less efficient. The mission of CARTA is to provide usability, scalability, and maintainability for the future by focusing on UI/UX and utilizing modern web technologies and computing parallelization. For example, to enhance the science productivity for astronomers, CARTA has been integrated with the ALMA, NRAO, and ASKAP (CASDA) science archives, allowing users to visualize images from these archives directly. In addition, CARTA is now featured as one of the tools in an SRCNet prototyping team, having been chosen to visualize SKA astronomical data.



Client-Server architecture
--------------------------
CARTA uses a client-server architecture suitable for visualizing images with large file sizes (GB to several TB) easily obtained from ALMA, VLA, or SKA pathfinders (MeerKAT and ASKAP) observations. Processing such a massive file with a personal computer or a laptop is difficult. Using a client-server architecture, heavy-lifting computation and data storage can be handled by remote enterprise-class servers or clusters with high computing power and high-performance storage. At the same time, processed products are sent to clients for light-weight computation and for visualization with modern web technologies, such as GPU-accelerated rendering. This architecture also enables users to visualize images from the ALMA, NRAO, and ASKAP (CASDA) science archives directly using CARTA as an interface. 


.. raw:: html

   <a href="_static/carta_intro_serverClient.png" target="_blank">
       <img src="_static/carta_intro_serverClient.png" 
           style="width:100%;height:auto;">
   </a>


Codebase and releases
---------------------
CARTA is an open-source project. Its source code is publicly available at https://github.com/CARTAvis. 

CARTA has two deployment modes: "Site Deployment Mode" (SDM) and "User Deployment Mode" (UDM). The former is designed for hosting multiple users on an enterprise-class server, while the latter is designed for single-user usage on a personal computer, laptop, or remote server. 

Installation guides for the "Site Deployment Mode" and the "User Deployment Mode" are provided in the section :ref:`installation_configuration`. Please contact the `CARTA Helpdesk <support@carta.freshdesk.com>`_ (support@carta.freshdesk.com) or file an `issue <https://github.com/CARTAvis/carta/issues>`_ if there is a problem. 

Besides the annual stable release (the current stable release is v5.0.0), there are one or two beta releases within the one-year development cycle. With the beta releases, you can try new features and provide feedback to the development team to improve the next stable release. Please visit the CARTA homepage (https://cartavis.org) for the latest beta and stable releases. 


Getting help
------------
The CARTA development team welcomes any suggestion, feature request, or bug report to make CARTA better via 

* `CARTA Helpdesk <support@carta.freshdesk.com>`_ (support@carta.freshdesk.com) 
* `GitHub Issue <https://github.com/CARTAvis/carta/issues>`_ (https://github.com/CARTAvis/carta/issues)


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

The development team is composed of astronomers, software engineers, and computer scientists who are passionate about astronomy and data visualization.



Software citation
-----------------

Please use the following DOI as a citation when using CARTA for publications.

.. image:: https://zenodo.org/badge/DOI/10.5281/zenodo.3377984.svg
   :target: https://doi.org/10.5281/zenodo.3377984

The bibtex is

.. code-block:: bibtex
   
   @software{angus_comrie_2018_3377984,
   author       = {Angus Comrie and
                  Kuo-Song Wang and
                  Yu-Hsuan Hwang and
                  Anthony Moraghan and
                  Pamela Harris and
                  Adrianna Pińska and
                  Carli Raul-Omar and
                  Kuan-Chou Hou and
                  Cheng-Chin Chiang and
                  Tien-Hao Chang and
                  Shou-Chieh Hsu and
                  Qi Pang and
                  Rob Simmonds and
                  Po-Sheng Huang and
                  Ming-Yi Lin and
                  Hengtai Jan},
   title        = {{CARTA: The Cube Analysis and Rendering Tool for 
                   Astronomy}},
   month        = dec,
   year         = 2018,
   publisher    = {Zenodo},
   doi          = {10.5281/zenodo.3377984},
   url          = {https://doi.org/10.5281/zenodo.3377984}
   }

You may also refer to https://ui.adsabs.harvard.edu/abs/2020zndo...3377984C/abstract.

Acknowledgment
--------------
ASIAA CASA Development Center (ACDC) acknowledges the grant from the National Science and Technology Council of Taiwan for the ALMA-NA collaboration.

The Inter-University Institute for Data Intensive Astronomy is a partnership of three South African universities: the University of Cape Town, the University of the Western Cape, and the University of Pretoria.

The National Radio Astronomy Observatory is a facility of the National Science Foundation operated under a cooperative agreement by Associated Universities, Inc.

The Department of Physics at the University of Alberta has contributed to the CARTA project thanks to support from the National Radio Astronomy Observatory under an ALMA Development Project and from the Canada Foundation for Innovation as part of the Canadian Initiative for Radio Astronomy Data Analysis (CIRADA).

CARTA is mainly built in C++, TypeScript, and JavaScript and with the following third-party libraries:

* AST: http://starlink.eao.hawaii.edu/starlink/AST
* Blueprint: https://blueprintjs.com
* casacore: https://casacore.github.io
* CASA source code: https://casa.nrao.edu/index.shtml
* Chart.js: https://www.chartjs.org
* Electron: https://electronjs.org
* GoldenLayout: https://golden-layout.com
* GoogleTest: https://github.com/google/googletest
* GSL: https://www.gnu.org/software/gsl/
* json-schema-validator: https://github.com/pboettch/json-schema-validator
* MobX: https://mobx.js.org
* MongoDB: https://www.mongodb.com
* node.js: https://nodejs.org
* Plotly: https://plotly.com
* Protocol buffers: https://developers.google.com/protocol-buffers 
* Pugixml: https://pugixml.org
* React: https://reactjs.org
* spdlog: https://github.com/gabime/spdlog
* sse2neon: https://github.com/DLTcollab/sse2neon
* uWebsockets: https://github.com/uNetworking/uWebSockets
* WebAssembly: https://webassembly.org

CARTA utilizes the following external data services:

* The `SIMBAD <https://simbad.u-strasbg.fr>`_ database, operated at CDS, Strasbourg, France (2000,A&AS,143,9, "The SIMBAD astronomical database", Wenger et al.)
* The `VizieR <https://vizier.cds.unistra.fr>`_ catalogue access tool, operated at CDS, Strasbourg Astronomical Observatory, France (2000, A&AS, 143, 23, "The VizieR database of astronomical catalogues.", Ochsenbein et al.)
* `HiPS2FITS <https://alasky.cds.unistra.fr/hips-image-services/hips2fits>`_, a service provided by CDS
* `Splatalogue <https://splatalogue.online>`_, a service provided by NRAO. See the FAQ page for the full set of catalog collection

The source code of CARTA is available on `GitHub <https://github.com/CARTAvis>`_.

The CARTA development team acknowledges David Berry for consulting on the AST library, Kumar Golap for the casacore library, and Anthony Remijan and Chris O'Brien for consulting on the Splatalogue SLAP API.

Copyright and license
---------------------
Copyright (C) 2018-2025 ASIAA, IDIA, NRAO, and Department of Physics, University of Alberta. This software is free to redistribute and modify under the `GNU General Public License version 3 <http://www.gnu.org/copyleft/gpl.html>`_, published by the Free Software Foundation.
