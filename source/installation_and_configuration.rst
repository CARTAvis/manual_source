.. _installation_configuration:

Installation and configuration
==============================
CARTA is fundamentally a web application and utilizes client-server architecture. There are three main components:

* carta_backend
* carta_frontend
* carta-controller

The "carta_backend" focuses on computations of image data for visualization at the client side. Usually the "carta_backend" is run on a powerful server or cluster with high-speed storage where users' data reside. The "carta_frontend" receives the data from the server side and utilizes web technologies to render the data for users. The "carta_frontend" also serves as the graphical user interface (GUI) for users to interact with the CARTA application. The "carta-controller" is a key component to handle the lifetime of a "carta_backend" process and the authentication of user login. Once the three components are configured properly, users will just need to visit a dedicated CARTA URL and login with credentials. Then, the GUI should be loaded and ready for use. This is called the **"Site Deployment Mode"**. Mostly it is suitable for institution-wide deployment for groups of users by a system administrator.

Alternatively, the "carta_backend" and the "carta_frontend" can be run on the same computer or on two different computers without the "carta-controller". It is up to the users to execute the "carta_backend" on a computer where the image data reside and connect to it with a web browser. Traditionally, the common use case is a user connects to a remote server via the ssh protocol and displays applications through X11 tunneling, or via VNC. The architectural design of CARTA is to avoid these less efficient ways of interacting with image data. Instead, users should use their *local* web browser (not a web browser in the VNC environment) to connect to the "carta_backend" running on a remote server which is accessed via the ssh protocol. This is called the **"User Deployment Mode"**. It is up to the users to install CARTA on a desired computer and run it manually.

The supported operating systems of the two modes are summarized below.

* Site Deployment Mode
  
  * Ubuntu 18.04 LTS (Bionic Beaver) and 20.04 LTS (Focal Fossa)

* User Deployment Mode

  * Ubuntu Linux: 18.04 LTS (Bionic Beaver), 20.04 LTS (Focal Fossa)
  * Red Hat Enterprise Linux: 7, 8
  * CentOS: 7, 8
  * macOS: 10.15 (Catalina), 11 (Big Sur)

.. note::
   CARTA may work on other Linux distributions (e.g., Fedora, Debian, etc), but has not been tested by us. CARTA may work on macOS 10.14 (Mojave), but again, it has not been tested by us.


In the following two sections, we provide the installation instructions for the two deployment modes. System administrators who wish to deploy CARTA institution-wide, please refer to the section  :ref:`installation_SDM`. For general users, please refer to the section :ref:`installation_UDM`.

.. _installation_SDM:

Site Deployment Mode
--------------------
The Site Deployment Mode supports the following operating systems:

* Ubuntu 18.04 LTS (Bionic Beaver) and 20.04 LTS (Focal Fossa)

To deploy CARTA at your institution as a web-based application for multiple users, please refer to the  `CARTA controller documentation <https://carta-controller.readthedocs.io/en/dev/>`_. Detailed instructions on installation and configuration of the "carta_backend", the "carta_frontend", and the "carta-controller" are provided. If there is a problem, please contact the `CARTA helpdesk <mailto:carta_helpdesk@asiaa.sinica.edu.tw>`_.


.. _installation_UDM:

User Deployment Mode
--------------------
The User Deployment Mode supports the following operating systems:

* Ubuntu Linux: 18.04 LTS (Bionic Beaver), 20.04 LTS (Focal Fossa)
* Red Hat Enterprise Linux: 7, 8
* CentOS: 7, 8
* macOS: 10.15 (Catalina), 11 (Big Sur)

If you have *root* access and can use a package manager to install CARTA via commandline, please refer to the section :ref:`installation_UDM_package_managers`. Otherwise, please refer to the section :ref:`installation_UDM_direct_download`.



.. _installation_UDM_package_managers:

Installation via package managers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
CARTA can be installed via commandline with package managers such as:

* :code:`yum` on Red Hat Enterprise Linux and CentOS
* :code:`apt` on Ubuntu Linux
* :code:`brew` on macOS

Please identify your operating system where you wish to run CARTA and follow the instructions. If there is a problem, please contact the `CARTA helpdesk <mailto:carta_helpdesk@asiaa.sinica.edu.tw>`_.

**Ubuntu**

Ubuntu 18.04 and 20.04 packages are available from our `PPA <https://launchpad.net/~cartavis-team/+archive/ubuntu/carta>`_. Please note that *root* access is required, unless you install in a Docker container.

.. code-block:: bash

   sudo add-apt-repository ppa:cartavis-team/carta
   sudo apt-get update
   sudo apt install carta

Please refer to the section :ref:`how_to_run_carta` for different single-user use cases.

**Red Hat Enterprise Linux 7**

For Red Hat Enterprise Linux 7 users, you first need to add the el7 "cartavis" and "EPEL" repositories. Please note that *root* access is required, unless you install in a Docker container.

.. code-block:: bash

   sudo curl https://packages.cartavis.org/cartavis-el7.repo --output /etc/yum.repos.d/cartavis.repo
   sudo rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
   sudo yum -y install carta

Please refer to the section :ref:`how_to_run_carta` for different single-user use cases.

**CentOS 7**

For CentOS7 users, you first need to add the el7 "cartavis" and "EPEL" repositories. Please note that *root* access is required, unless you install in a Docker container.

.. code-block:: bash

   sudo curl https://packages.cartavis.org/cartavis-el7.repo --output /etc/yum.repos.d/cartavis.repo
   sudo yum -y install epel-release
   sudo yum -y install carta

Please refer to the section :ref:`how_to_run_carta` for different single-user use cases.

**Red Hat Enterprise Linux 8**

For Red Hat Enterprise Linux 8 users, you first need to add the el8 "cartavis" and "EPEL" repositories. Please note that *root* access is required, unless you install in a Docker container.

.. code-block:: bash

   sudo curl https://packages.cartavis.org/cartavis-el8.repo --output /etc/yum.repos.d/cartavis.repo
   sudo rpm -ivh https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
   sudo yum -y install carta

Please refer to the section :ref:`how_to_run_carta` for different single-user use cases.

**CentOS 8**

For CentOS8 users, you first need to add the el8 "cartavis", "EPEL", and "powertools" repositories. Please note that *root*  access is required, unless you install in a Docker container.

.. code-block:: bash

   sudo curl https://packages.cartavis.org/cartavis-el8.repo --output /etc/yum.repos.d/cartavis.repo
   sudo dnf -y install 'dnf-command(config-manager)'
   sudo dnf -y install epel-release
   sudo dnf -y config-manager --set-enabled powertools
   sudo dnf -y install carta

Please refer to the section :ref:`how_to_run_carta` for different single-user use cases.

**macOS**

We officially support macOS 10.15 Catalina and macOS 11.0 Big Sur through `Homebrew <https://brew.sh/>`_. If you do not already have it, you may install Homebrew using the following command (*root* access is required):

.. code-block:: bash

   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

Now CARTA can be installed with:   

.. code-block:: bash

   brew install cartavis/tap/carta



.. _installation_UDM_direct_download:

Installation of the stand-alone application (direct download)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
If you do not have *root* access and cannot use package managers to install CARTA via the commandline, here we provide alternative solutions.

**Ubuntu Linux AppImage**

The Ubuntu Linux AppImage does not require *root* access. You simply download, extract, and run it. The AppImage has been tested to run on Ubuntu 18.04 and 20.04.

The AppImage can be downloaded `here <http://alma.asiaa.sinica.edu.tw/_downloads/carta-v2.0-ubuntu.tar.gz>`_. Alternatively, you can use the commandline:

.. code-block:: bash

   wget http://alma.asiaa.sinica.edu.tw/_downloads/carta-v2.0-ubuntu.tar.gz
   tar -xzf carta-v2.0-ubuntu.tar.gz

Please refer to the section :ref:`how_to_run_carta` for different single-user use cases.


**Red Hat Linux AppImage**

The Red Hat Linux AppImage does not require root access. You simply download, extract, and run it. The AppImage has been tested to run on Red Hat Enterprise Linux (RHEL) 7 and 8, as well as CentOS 7 and 8.

The AppImage can be downloaded `here <http://alma.asiaa.sinica.edu.tw/_downloads/carta-v2.0-redhat.tar.gz>`_. Alternatively, you can use the commandline:

.. code-block:: bash

   wget http://alma.asiaa.sinica.edu.tw/_downloads/carta-v2.0-redhat.tar.gz
   tar -xzf carta-v2.0-redhat.tar.gz

Please refer to the section :ref:`how_to_run_carta` for different single-user use cases.


**macOS Electron Desktop**

The macOS Electron Desktop version can be downloaded `here <http://alma.asiaa.sinica.edu.tw/_downloads/CARTA-v2.0.dmg>`_. 

After downloading, open the DMG installer and drag the CARTA icon to the Applications folder.

.. note::
   You may create an alias for starting the CARTA Electron version through your terminal. To do so, please open your "~/.zshrc" file (or "~/.bashrc" if you use bash) in a text editor and add the following line:

   .. code-block:: bash

      alias carta='/Applications/CARTA.app/Contents/MacOS/CARTA'

You may use a different alias rather than 'carta' e.g. 'carta-v2.0' or 'carta-electron'.

Please refer to the section :ref:`how_to_run_carta` for different single-user use cases.



.. _how_to_run_carta:

How to run CARTA?
-----------------
There are different ways of running CARTA in your working environment. Please identify the following use cases and follow the instructions accordingly.

* CARTA is installed in the "Site Deployment Mode" by my system administrator at my institute: :ref:`how_to_run_carta_sdm`.
* CARTA is installed in the "User Deployment Mode", and I would like to run CARTA on a *remote* server: :ref:`how_to_run_carta_udm_remote`
* CARTA is installed in the "User Deployment Mode", and I would like to run CARTA on a *local* computer: :ref:`how_to_run_carta_udm_local`

Please note that the CARTA GUI is run in the web browser environment. The supported browsers are:

* Google Chrome (tested with v91)
* Firefox (tested with v89)
* Safari (tested with v14.1)

Other browsers might be supported but they are not tested. 

.. warning::
   At the moment, there is a layout issue with the Safari browser, which affect usability and user experience significantly. macOS users should try to avoid using Safari to run CARTA. 

.. note::
   CARTA requires WebGL in order to render images properly. WebGL2 is also required to render catalog overlay properly. Please ensure WebGL and WebGL2 are enabled in your browser. 


.. _how_to_run_carta_sdm:

Site Deployment Mode: connecting CARTA
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
If your institute has CARTA deployed for multiple users, you should have a dedicated URL to access CARTA (please check with your system administrator). What you need to do is to access the URL with your favourite browser and you should see a dashboard similar to the following.

.. raw:: html

   <img src="_static/carta_sdm_login.png" 
     style="width:70%;height:auto;">


.. note::
   When you are already authorized, you may not see the login page when you access the CARTA URL. Instead, the CARTA GUI should just appear and be ready for use.

After you provide your credentials, you should see the CARTA GUI directly and it is ready to use.

When CARTA is deployed in the "Site Deployment Mode", a "Server" option is available in the "File" menu. With the "Server" menu, you can restart the "carta_backend" process, logout of the CARTA service, or visit the dashboard for more options.   

.. raw:: html

   <img src="_static/carta_sdm_file_menu.png" 
     style="width:50%;height:auto;">

The dashboard looks like the following screenshot. With it, additionally you can request a new CARTA session as a new browser tab. Note that this new session shares the same carta_backend process with the existing sessions. 

.. raw:: html

   <img src="_static/carta_sdm_dashboard.png" 
     style="width:70%;height:auto;">

Additionally, you can view the program log via the dashboard for debugging purposes.

.. raw:: html

   <img src="_static/carta_sdm_log.png" 
     style="width:100%;height:auto;">






.. _how_to_run_carta_udm_remote:

User Deployment Mode: running CARTA on a remote server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
After you have successfully installed CARTA on a *remote* server via a package manager or by downloading the AppImage, you can try the following example to initialize CARTA with commandline:

.. code-block:: bash

   # CARTA installed via a package manager (yum, apt, or brew)
   carta --no_browser
   # CARTA installed by downloading the AppImage
   ./carta-v2.0-ubuntu.AppImage --no_browser

Please ensure that you have the :code:`--no_browser` flag set. Then you should see something like the following in your terminal:

.. code-block:: text

   [2021-06-03 10:30:57.536] [info] Writing to the log file: /Users/spongebob/.carta/log/carta.log
   [2021-06-03 10:30:57.537] [info] /usr/local/bin/carta_backend: Version 2.0.0
   [2021-06-03 10:30:57.574] [info] Serving CARTA frontend from /usr/local/Cellar/carta-beta/2.0.0/share/carta/frontend
   [2021-06-03 10:30:57.575] [info] Listening on port 3002 with top level folder /, starting folder /Users/spongebob. The number of OpenMP worker threads will be handled automatically.
   [2021-06-03 10:30:57.575] [info] CARTA is accessible at http://192.168.0.128:3002/?token=E1A26527-8226-4FD5-8369-2FCD00BACEE0

The last line contains the unique URL (e.g., :code:`http://192.168.0.128:3002/?token=E1A26527-8226-4FD5-8369-2FCD00BACEE0`) for you to access the CARTA process that you have just started up. You will need to copy the URL and paste it to your *local* web browser to initialize the CARTA GUI. Please note that by "local", we mean the computer that you are using directly in front of you. Please do not use a web browser from the remote server to prevent potential failure due to lack of WebGL support.

More CARTA initialization flags are available in the section :ref:`carta_init_flag`.

.. warning::
   It is critical to have the :code:`--no_browser` flag set when you launch CARTA on a *remote* server. If the flag is not set, CARTA will launch the default web browser on the remote server. If you have enabled X11 tunneling when you access the remote server via the ssh protocol, the web browser will be displayed in your local computer via X11. Otherwise, you will not see any browser displayed in your screen. Even the web browser from the remote server is displayed successfully with CARTA initialized, we *do not recommend* using CARTA in this way because the rendering is much less efficient and possibly your image will not be rendered properly due to lack of WebGL support. 


If you would like to initialize CARTA with an image loaded in the image viewer or a folder loaded in the file browser, please try:

.. code-block:: bash

   # CARTA installed via a package manager (yum, apt, or brew)
   carta M51.fits --no_browser
   carta /alma/data --no_browser
   # CARTA installed by downloading the AppImage
   ./carta-v2.0-ubuntu.AppImage M51.fits --no_browser
   ./carta-v2.0-ubuntu.AppImage /alma/data --no_browser



.. _how_to_run_carta_udm_local:

User Deployment Mode: running CARTA on a local computer
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
After you have successfully installed CARTA on your *local* computer via a package manager or by downloading the AppImage, you can try the following example to initialize CARTA with the commandline:

.. code-block:: bash

   # CARTA installed via a package manager (yum, apt, or brew)
   carta
   # CARTA installed by downloading the AppImage
   ./carta-v2.0-ubuntu.AppImage

Then you should see something like the following in your terminal *and* the CARTA GUI initializing in your default web browser:

.. code-block:: text

   [2021-06-03 11:03:41.279] [info] Writing to the log file: /Users/spongebob/.carta/log/carta.log
   [2021-06-03 11:03:41.280] [info] /usr/local/bin/carta_backend: Version 2.0.0
   [2021-06-03 11:03:41.289] [info] Serving CARTA frontend from /usr/local/Cellar/carta-beta/2.0.0/share/carta/frontend
   [2021-06-03 11:03:41.289] [info] Listening on port 3002 with top level folder /, starting folder /Users/spongebob. The number of OpenMP worker threads will be handled automatically.
   [2021-06-03 11:03:41.446] [info] CARTA is accessible at http://192.168.0.128:3002/?token=C71D128D-3567-4EA1-B0F2-E703D63D8D0F
   [2021-06-03 11:03:45.209] [info] Session 1 [192.168.0.128] Connected. Num sessions: 1

Your web browser is automatically launched to access the URL on the second last line. If you would like to disable this automation, please add the :code:`--no_browser` flag when you launch CARTA with commandline. If you would like to have this web browser automation but with more control on browser type or brower properties, please refer to the section :ref:`browser_options`. More CARTA initialization flags are available in the section :ref:`carta_init_flag`.

.. note::
   If you wish to run the AppImage inside a Docker container, or your system has FUSE disabled, please prefix with the following environment variable:

   .. code-block:: bash

      APPIMAGE_EXTRACT_AND_RUN=1 ./carta-v2.0-ubuntu.AppImage


If you would like to initialize CARTA with an image loaded in the image viewer or a folder loaded in the file browser, please try:

.. code-block:: bash
      
   # CARTA installed via a package manager (yum, apt, or brew)
   carta M51.fits --no_browser
   carta /alma/data --no_browser
   # CARTA installed by downloading the AppImage
   ./carta-v2.0-ubuntu.AppImage M51.fits --no_browser
   ./carta-v2.0-ubuntu.AppImage /alma/data --no_browser



.. _carta_init_flag:

CARTA initialization flags
--------------------------
CARTA supports a set of commandline flags for initialization. Try the following to see all options:

.. code-block:: bash

   # CARTA installed via a package manager (yum, apt, or brew)
   carta --help
   # CARTA installed by downloading the AppImage
   ./carta-v2.0-ubuntu.AppImage --help

Then you should see:

.. code-block:: text

   Cube Analysis and Rendering Tool for Astronomy
   Usage:
     carta [OPTION...] <file or folder to open>

     -h, --help                    print usage
     -v, --version                 print version
         --verbosity <level>       display verbose logging from this level
                                   (default: 4)
         --no_log                  do not log output to a log file
         --log_performance         enable performance debug logs
         --log_protocol_messages   enable protocol message debug logs
         --no_http                 disable frontend HTTP server
         --no_browser              don't open the frontend URL in a browser on
                                   startup
         --browser <browser>       custom browser command
         --host <interface>        only listen on the specified interface (IP
                                   address or hostname)
     -p, --port <port>             manually set the HTTP and WebSocket port
                                   (default: 3002 or nearest available port)
     -g, --grpc_port <port>        set gRPC service port
     -t, --omp_threads <threads>   manually set OpenMP thread pool count
         --top_level_folder <dir>  set top-level folder for data files
         --frontend_folder <dir>   set folder from which frontend files are
                                   served
         --exit_timeout <sec>      number of seconds to stay alive after last
                                   session exits
         --initial_timeout <sec>   number of seconds to stay alive at start if
                                   no clients connect
         --idle_timeout <sec>      number of seconds to keep idle sessions alive
         --read_only_mode          disable write requests
         --no_user_config          ignore user configuration file
         --no_system_config        ignore system configuration file

    Deprecated and debug options:
         --debug_no_auth      accept all incoming WebSocket connections on the
                              specified port (not secure; use with caution!)
         --threads <threads>  [deprecated] no longer supported
         --base <dir>         [deprecated] set starting folder for data files
                              (use the positional parameter instead)
         --root <dir>         [deprecated] use 'top_level_folder' instead

   By default the CARTA backend uses the current directory as the starting data 
   folder, and uses the root of the filesystem (/) as the top-level data folder. If 
   a custom top-level folder is set, the backend will be restricted from accessing 
   files outside this directory.

   Frontend files are served from '../share/carta/frontend' (relative to the 
   location of the backend executable). By default the backend listens for HTTP and 
   WebSocket connections on all available interfaces, and automatically selects the 
   first available port starting from 3002.  On startup the backend prints out a URL 
   which can be used to launch the frontend, and tries to open this URL in the 
   default browser.

   The gRPC service is disabled unless a gRPC port is set. By default the number of 
   OpenMP threads is automatically set to the detected number of logical cores.

   Logs are written both to the terminal and to a log file, '.carta/log/carta.log' 
   in the user's home directory. Possible log levels are:
    0   off
    1   critical
    2   error
    3   warning
    4   info
    5   debug

   Performance and protocol message logging is disabled by default, but can be 
   enabled with flags. The verbosity takes precedence: the additional log messages 
   will only be visible if the level is set to 5 (debug). Performance logs are 
   written to a separate log file, '.carta/log/performance.log'.

   Options are provided to shut the backend down automatically if it is idle (if no 
   clients are connected), and to kill frontend sessions that are idle (no longer 
   sending messages to the backend).

   Disabling the browser takes precedence over a custom browser command. The custom 
   browser command may contain the placeholder CARTA_URL, which will be replaced by 
   the frontend URL. If the placeholder is omitted, the URL will be appended to the 
   end.


If you have installed the macOS Electron Desktop version and set up an alias, a few commandline options are available:

.. code-block:: text

   carta --help

   CARTA Electron desktop version
   Usage:
   carta []             CARTA file browser will default to the current path.
         [<path>]       CARTA file browser will default to the specified    
                        path <path> e.g. carta ~/CARTA/Images               
         [<image>]      CARTA will directly open the image named <image>    
                        e.g. carta aJ.fits or carta ~/CARTA/Images/aJ.fits  
         --help         View this help output.                              
         --debug        Open the DevTools in the Electron window.            


.. _browser_options:

Browser options
---------------
A new option has been added to the CARTA backend executable which allows you to specify a custom browser command for CARTA to use to launch the frontend automatically. This option is still under development and has certain temporary limitations. We provide some examples below to demonstrate how it can be used.

The option is provided as an arbitrary string which includes a browser executable name as well as any custom flags that you would like to pass to the browser. The special placeholder CARTA_URL will be replaced by CARTA by the frontend URL, complete with the security token. It's only necessary to add this if there is something that you need to add after the URL -- otherwise you can leave it out and it will be appended to the end.

This command string can be passed to the :code:`carta` executable as a commandline argument (:code:`--browser`), or written permanently to a configuration file, or even used to create a custom launcher for your GUI environment. If your command contains spaces, please make sure that you quote it.

Commandline examples:

Chrome on Linux (select the correct executable name):

:code:`--browser="google-chrome --app=CARTA_URL --new-window&"`

:code:`--browser="chrome --app=CARTA_URL --new-window&"`

:code:`--browser="chromium-browser --app=CARTA_URL --new-window&"`

Firefox on Linux:

:code:`--browser="firefox -new-tab"`

:code:`--browser="firefox -new-window"`

macOS:

:code:`--browser="open -a firefox"`

:code:`--browser="open -a Google\ Chrome"`

:code:`--browser="open -n -a Google\ Chrome --args --app=CARTA_URL --new-window"`





Log and configuration files
---------------------------
For users who installed CARTA in the "User Deployment Mode", a set of configuration files are created in the :code:`~/.carta` folder after you have run CARTA once. You should see that two folders are created:

* config: configuration files including preferences and layouts
* log: backend log named as "carta.log"

The preferences and layout files are in the JSON format. The "preferences.json" file allows you to set up the preferences programmatically. A full set of options is available in :ref:`appendix_d_preferences_schema`. The layout folder contains all the custom layouts that you have created.


.. _troubleshooting:

Troubleshooting
---------------
In this section, we provide common issues users have experienced so far and provide solutions. If none of the solutions work, please do contact `CARTA Helpdesk <carta_helpdesk@asiaa.sinica.edu.tw>`_ for help.

* **A spectral line query causes the RedHat AppImage version of CARTA to crash**  

  CARTA uses "curl" to access the Splatalogue via "https". You may be running an outdated version of RedHat7 and need to update your Network Security Services (nss) package by doing :code:`sudo yum update nss`.

* **The RedHat7 AppImage does not open and it prints a message suggesting to extract the AppImage using the** :code:`--appimage-extract` **flag.**

  This error is due to lack of FUSE (File System in Userspace) support. FUSE support in RedHat7 systems may be disabled in some institute environments for security reasons. If that is the case, please prefix with the :code:`APPIMAGE_EXTRACT_AND_RUN=1` environment variable. i.e. :code:`APPIMAGE_EXTRACT_AND_RUN=1 ./carta-v2.0-redhat.AppImage`

* **There are error messages when I try to install CARTA using Homebrew**

  There could be various problems such as "dyld: Library not loaded" due to "libgrpc++.1.37.dylib" or "libprotobuf.26.dylib", for example. If you encounter similar errors, please try the following:

  .. code-block:: bash

     brew update
     brew remove cartavis/tap/carta
     brew install cartavis/tap/carta

  Or,

  .. code-block:: bash

     brew remove cartavis/tap/carta-beta
     brew --build-from-source cartavis/tap/carta-beta

  If the error mentions that "homebrew-core is a shallow clone". please try as it suggests:

  .. code-block:: bash

     git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core fetch --unshallow
     git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask fetch --unshallow

     brew uninstall cartavis/tap/carta
     brew install cartavis/tap/carta

* **I see a blank page or image...**

  Check your browser version. It needs to support "*wasm*" streaming and be enabled. More information about browser support of WebAssembly can be found at https://caniuse.com/#search=WebAssembly

  Some outdated RedHat7 distributions may have Firefox 52 ESR which although having WebAssembly support, it is deactivated by default. We recommend updating to a newer version of Firefox "sudo yum update firefox" or installing Google Chrome. If you can not update Firefox, you can try activating WebAssembly as follows:

  1) Open a new tab and enter "about:config" in the URL bar.
  2) A warning message will appear. Click the button to continue.
  3) In the search box enter "wasm" and the list will filter down to a few results.
  4) Double click each line related to "javascript.options.wasm" so that the "Value" column shows them as "true".
  5) Then simply close the "about:config" tab and the CARTA frontend should now load properly.

  As for the Chrome browser, WebAssembly support was introduced in Chrome version 51, but versions 51 to 56 have it deactivated by default. To activate WebAssembly in Chrome 51 to 56 enter "chrome://flags" in the URL bar, type WebAssembly in the search box that appears, and change each WebAssembly option to "Enabled". If you have Chrome version 57 or newer, WebAssembly should be activated by default.

  CARTA uses GPU to render the image in the image viewer. If you are running CARTA remotely through a VNC window, the image may fail to render correctly leading to a blank image even though X/Y profiles and contour still function correctly. In this case we recommend to use :code:`--no_browser` flag to launch CARTA at the remote server and use your local web browser to access the URL shown in your terminal. Please refer to the section :ref:`how_to_run_carta_udm_remote`.