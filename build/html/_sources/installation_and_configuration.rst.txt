.. _installation_configuration:

Installation and configuration
==============================
CARTA supports two use cases in this desktop v1.0 release. For users using a laptop or a desktop connected with a monitor, please download the "Local" version. For users using a remote server via the ssh protocol, please download the "Remote" version. If there is any problem, please contact `CARTA Helpdesk <carta_helpdesk@asiaa.sinica.edu.tw>`_ for help.


Local version
-------------

macOS 10.12/10.13/10.14 / OSX 10.11
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Please follow the steps:

1. `Download the package <https://github.com/CARTAvis/carta-releases/releases/download/v1.0/CARTA-v1.0.dmg>`_
2. Open the dmg file and drag the CARTA-v1.0.app to the /Applications folder. 
3. To run CARTA-v1.0, click on it in the Launchpad, or double click on it in the Finder.

Redhat 7, CentOS 7
^^^^^^^^^^^^^^^^^^
Please follow the steps:

1. `Download the package (AppImage)  <https://github.com/CARTAvis/carta-releases/releases/download/v1.0/CARTA-v1.0-RedHat7.AppImage>`_ 

2. After downloading, make the AppImage file executable:

.. code-block:: bash  

  chmod 755 CARTA-v1.0-RedHat7.AppImage 

3. Then execute:

.. code-block:: bash

  ./CARTA-v1.0-RedHat7.AppImage 



Ubuntu 16.04 LTS/18.04 LTS
^^^^^^^^^^^^^^^^^^^^^^^^^^
Please follow the steps:

1. `Download the package (AppImage)  <https://github.com/CARTAvis/carta-releases/releases/download/v1.0/CARTA-v1.0-ubuntu.AppImage>`_ 

2. After downloading, make the AppImage file executable:

.. code-block:: bash  

  chmod 755 CARTA-v1.0-ubuntu.AppImage 

3. Then execute:

.. code-block:: bash

  ./CARTA-v1.0-ubuntu.AppImage



Remote version
--------------

Redhat 6/7, CentOS 6/7
^^^^^^^^^^^^^^^^^^^^^^
Please follow the steps:

1. `Download the package  <https://github.com/CARTAvis/carta-releases/releases/download/v1.0/CARTA-v1.0-RedHat6-headless.tar.gz>`_

2. On your remote server, extract the archive:

.. code-block:: bash

  tar -xvf CARTA-v1.0-RedHat6-headless.tar.gz

3. Run the carta executable in your terminal window:

.. code-block:: bash

  ./CARTA-v1.0-RedHat6-headless/carta

4. This will provide a unique URL. Copy and paste this URL in to your local web browser to access CARTA.

5. When finished, close your browser window, and press 'q' in the terminal window in order to close CARTA.

.. note::
   The default search path for images is $HOME, but you may override this by appending a path to a directory of your choice 
   
   .. code-block:: bash
   
     ./CARTA-v1.0-RedHat6-headless/carta /path/to/my/images


