.. _installation_configuration:

Installation and configuration
==============================
CARTA utilizes discrete or integrated GPU for image rendering. Therefore, the CARTA Desktop 'local' version is intended for use on a laptop or desktop computer directly connected to a monitor.

We also provide a 'remote' version for users who wish to run CARTA from a remote RedHat6/CentOS6 or RedHat7/CentOS7 server via the ssh protocol. As the majority of servers do not have onboard GPUs, the remote version runs the CARTA 'backend' on the server, while the CARTA 'frontend' is accessed through your web browser of choice running on your local machine. This allows your local machine's GPU to perform the image rendering, while the remote server handles the storage and CPU/RAM instensive tasks.

.. note::
   NOTE FOR VNC USERS





If there is any problem, please contact `CARTA Helpdesk <carta_helpdesk@asiaa.sinica.edu.tw>`_ for help.

Local version
-------------

macOS 10.12/10.13/10.14 / OSX 10.11
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Please follow the steps:

1. `Download the package <https://github.com/CARTAvis/carta-releases/releases/download/v1.0.1/CARTA-v1.0.1.dmg>`_
2. Open the dmg file and drag the CARTA-v1.0.1.app to the /Applications folder. 
3. To run CARTA-v1.0.1, click on it in the Launchpad, or double click on it in the Finder.

.. tip::
   Alternatively, the user may run CARTA from the terminal by adding an alias to their ~/.bashrc file. e.g. 

   .. code-block:: bash

      alias carta=/Applications/CARTA-v1.0.1.app/Contents/MacOS/CARTA-v1.0.1

   and

   .. code-block:: bash

      source ~/.bashrc 

   Now CARTA can be started by typing carta in the terminal.

   .. code-block:: bash

      carta 
       


Redhat 7, CentOS 7
^^^^^^^^^^^^^^^^^^
Please follow the steps:

1. `Download the package (AppImage)  <https://github.com/CARTAvis/carta-releases/releases/download/v1.0.1/CARTA-v1.0.1-RedHat7.AppImage>`_ 

2. After downloading, make the AppImage file executable:

.. code-block:: bash  

  chmod 755 CARTA-v1.0.1-RedHat7.AppImage 

3. Then execute:

.. code-block:: bash

  ./CARTA-v1.0.1-RedHat7.AppImage 



Ubuntu 16.04 LTS/18.04 LTS
^^^^^^^^^^^^^^^^^^^^^^^^^^
Please follow the steps:

1. `Download the package (AppImage)  <https://github.com/CARTAvis/carta-releases/releases/download/v1.0.1/CARTA-v1.0.1-ubuntu.AppImage>`_ 

2. After downloading, make the AppImage file executable:

.. code-block:: bash  

  chmod 755 CARTA-v1.0.1-ubuntu.AppImage 

3. Then execute:

.. code-block:: bash

  ./CARTA-v1.0.1-ubuntu.AppImage



Remote version
--------------

Redhat 6/7, CentOS 6/7
^^^^^^^^^^^^^^^^^^^^^^
Please follow the steps:

1. `Download the package  <https://github.com/CARTAvis/carta-releases/releases/download/v1.0.1/CARTA-v1.0.1-RedHat6-RedHat7-remote.tar.gz>`_

2. On your remote server, extract the archive:

.. code-block:: bash

  tar -xvf CARTA-v1.0.1-RedHat6-RedHat7-remote.tar.gz

3. Run the carta executable in your terminal window:

.. code-block:: bash

  ./CARTA-v1.0.1-RedHat6-RedHat7-remote/carta

4. This will provide a unique URL. Copy and paste this URL in to your local web browser to access CARTA.

5. When finished, close your browser window, and press 'q' in the terminal window in order to close CARTA.

.. note::
   The default search path for images is $HOME, but you may override this by appending a path to a directory of your choice 
   
   .. code-block:: bash
   
     ./CARTA-v1.0-RedHat6-RedHat7-remote/carta /path/to/my/images


