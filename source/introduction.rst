Introduction
============

The mission of CARTA
--------------------
CARTA is the *Cube Analysis and Rendering Tool for Astronomy*, a new image visualization and analysis tool designed for the ALMA, the VLA, and the SKA pathfinders. As the image size increases drastically with modern telescopes in recent years, viewing an image with a local image viewer or with a remote image viewer via the ssh protocol becomes less efficient. The mission of CARTA is to provide usability and scalability for the future by utilizing modern web technologies and computing parallelization.

Client-Server architecture
--------------------------
CARTA uses a client-server architecture which is suitable for visualizing images with large file sizes (GB to TB) easily obtained from ALMA or VLA observations. It is practically difficult to process such a huge file with personal computer or laptop. By using a client-server architecture, computation and data storage are handled by remote enterprise-class servers or clusters with high performance storage, while processed products are sent to clients only for visualization with modern web features, such as GPU-accelerated rendering. This architecture also enables users to interact with the ALMA and VLA science archives by using CARTA as an interface. 


.. raw:: html

   <img src="_static/carta_intro_serverClient.png" 
        style="width:100%;height:auto;">

Codebase and releases
---------------------
CARTA is an open-source project. Its source code is available at https://github.com/CARTAvis. 

CARTA ultimately will have two distributions: CARTA-server and CARTA-desktop. The former is designed for handling large datasets with remote servers, while the later is suitable for smaller datasets (a few thousand pixels in the x and y dimensions) which can still be handled with personal computer or laptop. 

With the version 1.0 desktop release, CARTA supports two use cases. For users using a laptop or a desktop with a monitor, please use the "Local" version. For users using a remote server via the ssh protocol, please use the "Remote" version. Installation guides for these two versions are provided in the section :ref:`installation_configuration`.

With the *current* version 1.0.1 desktop patch release, CARTA further provides:

* enhanced file browser navigation capability.
* remote server (backend) status icon.
* improvements of file information and header.
* displaying data values in the spatial and the spectral profilers.

The release plan and major goals are the following:

* Version 1.0: basic image and profile viewing capability.
  
  * Version 1.0.1: current release, enhanced file browser navigation capability

* Version 1.1: basic region of interest (ROI) support and relevant analysis tools (statistics, histogram, and profilers).
* Version 1.2: WCS group support which allows multiple images to be aligned in spatial and spectral domains.
* Next: multiple-panel view
* Next: moments image, position-velocity image, and scripting interface
* Next: interactive clean
* Next: collaborative mode
* Next: misc.


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
Copyright (C) 2018-2019 ASIAA, IDIA, and NRAO. This program is free software; you can redistribute it and/or modify it under the terms of the `GNU General Public License version 3 <http://www.gnu.org/copyleft/gpl.html>`_ as published by the Free Software Foundation.

.. It is the policy of Associated Universities, Inc. (AUI), that the copyright and licensing for all software created at the National Radio Astronomy Observatory (NRAO) allows the source code for that software to be freely distributed and modified. This policy is both to support the Observatory's mission in providing software which might be of use in new scientific contexts, and to acknowledge that the Observatory has gained great advantage from open source software and the best way to repay this debt is to contribute to the effort. This policy does not require you to distribute software intended for in-house work, although if it might be of general interest we encourage you to do so. This policy also does not result in any additional support burden: the software is to be made available only on an "as is" basis unless special arrangements are negotiated.

.. As a further policy, due to the familiarity of the Observatory with the Free Software Foundation's GNU `General Public License (GPL) <http://www.gnu.org/copyleft/gpl.html>`_, and with the GNU `Lesser General Public License (LGPL) <http://www.gnu.org/copyleft/lesser.html>`_, these licenses are to be used. In both cases the line: 

..    Copyright (C) 2018-2019 Associated Universities, Inc. Washington DC, USA.

.. Alternative licensing is possible (for example a BSD style license), but will require individual approval.

.. Exceptions to either policy require a waiver from the Associate Director for Data Management.


.. .. raw:: html

..   <hr>

.. The newly developed and modified source code by ASIAA CASA team will be licensed with GNU General Purpose License (GPL) or GNU Lesser General Purpose License (LGPL) with Associated Universities, Inc listed as the copyright holder. This license may be modified to another open source license agreement by agreement of NRAO and ASIAA.