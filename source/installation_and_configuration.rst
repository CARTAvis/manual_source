.. _installation_configuration:

Installation and configuration
==============================
CARTA v1.3 supports the following operating systems:

* macOS 10.14/10.15
* Ubuntu 16.04 LTS/18.04 LTS
* RedHat 7
* RedHat 6 (conditional)

Command line to launch CARTA is supported (see :ref:`commandLineStartup` for instructions).

CARTA utilizes discrete or integrated GPU for image rendering. For users who wish to run CARTA from a remote RedHat 6/7 or Ubuntu 16.04 LTS/18.04 LTS server via the ssh protocol, CARTA v1.3 also provides a "remote" mode for this use case (see :ref:`commandLineStartup` for instructions). As the majority of servers do not have onboard GPUs, the remote mode runs the CARTA "backend" on the server, while the CARTA "frontend" is accessed through your web browser of choice running on your local machine. This allows your local machine's GPU to perform the image rendering, while the remote server handles the storage and CPU/RAM intensive tasks.

If there is any problem, please contact `CARTA Helpdesk <carta_helpdesk@asiaa.sinica.edu.tw>`_ for help.


CARTA-server
------------
The installation and configuration of the server version is available through `CARTA Helpdesk <carta_helpdesk@asiaa.sinica.edu.tw>`_. The CARTA team would be happy to work with you on getting CARTA-server installed on your server.



CARTA-desktop: macOS 10.14/10.15
--------------------------------
Please follow the steps:

1. `Download the DMG installer file <https://github.com/CARTAvis/carta-releases/releases/download/v1.3.1/CARTA-v1.3.1.dmg>`_

2. Open the DMG file and drag the CARTA icon to your /Applications folder.

3. To run CARTA either:

  a) Find the CARTA icon in the Launchpad and click it, or double click it in the Finder.

  b) (**Highly recommended**) Create an alias in your ~/.bashrc file by opening your ~/.bashrc file in a text editor and add the following line:

  .. code-block:: bash

     alias carta='/Applications/CARTA.app/Contents/MacOS/CARTA'

  Then, after entering source ~/.bashrc in the terminal, you will be able to start CARTA by simply typing “carta”.

  .. code-block:: bash

     source ~/.bashrc
     carta

.. note::
   If you see a prompt with "CARTA can't be opended because Apple cannot check it for malicious software.", please go to **System preferences** -> **Security & Privacy** and hit the **Open anyway** button to launch CARTA.

   .. raw:: html

      <img src="_static/carta_blocked.png" 
        style="width:100%;height:auto;">

   .. raw:: html

      <img src="_static/carta_blocked_solution.png" 
        style="width:100%;height:auto;">


CARTA-desktop: Ubuntu 16.04 LTS/18.04 LTS
-----------------------------------------
Please follow the steps:

1. `Download the tgz file <https://github.com/CARTAvis/carta-releases/releases/download/v1.3.1/CARTA-v1.3.1-ubuntu.tgz>`_

2. Unzip the tgz file

   .. code-block:: bash

      tar -xvf CARTA-v1.3.1-ubuntu.tgz

3. To run CARTA either 
   
   a) Execute the AppImage directly
   
   .. code-block:: bash
      
      ./CARTA.AppImage
   
   b) (**Highly recommended**) Create an alias in your shell script file. For example, if you are using bash and the AppImage happens to be in your Downloads folder, open ~/.bashrc file in a text editor and add a line

   .. code-block:: bash

      alias carta='~/Downloads/CARTA.AppImage'
   
   Then, after entering source ~/.bashrc in the terminal, you will be able to start carta by simply typing “carta”.

   .. code-block:: bash

      source ~/.bashrc
      carta
    
   If you use csh or tcsh, the syntax differs only in that there is no equals sign, therefore it would be 
   
   .. code-block:: tcsh
   
      alias carta '~/Downloads/CARTA.AppImage'
   
   and 
   
   .. code-block:: tcsh

      source ~/.cshrc
      carta
   
   or 
   
   .. code-block:: tcsh
   
      source ~/.tcshrc
      carta

.. note::
   For this v1.3 release we are providing a combined desktop and remote server capability. 
   
   Invoke remote mode with the "-\\-remote" flag
   
   .. code-block:: bash
   
      ./CARTA.AppImage --remote
      
   or, if an alias is created, 
   
   .. code-block:: bash
   
      carta --remote


CARTA-desktop: Redhat 7
-----------------------
Please follow the steps:

1. `Download the tgz file <https://github.com/CARTAvis/carta-releases/releases/download/v1.3.1/CARTA-v1.3.1-RedHat7.tgz>`_

2. Unzip the tgz file

   .. code-block:: bash

      tar -xvf CARTA-v1.3-RedHat7.tgz

3. To run CARTA either 

  a) Execute the AppImage directly
  
  .. code-block:: bash 
  
     ./CARTA.AppImage
  
  b) (**Highly recommended**) Set up an alias in your shell script file. For example, if your are using bash and the AppImage happens to be in your Downloads folder, open your ~/.bashrc file in a text editor and add a line
  
  .. code-block:: bash

     alias carta='~/Downloads/CARTA.AppImage'

  Then, after entering source ~/.bashrc in the terminal, you will be able to start carta by simply typing “carta”.
  
  .. code-block:: bash

     source ~/.bashrc
     carta

  If you use csh or tcsh, the syntax differs only in that there is no equals sign, therefore it would be 
  
  .. code-block:: tcsh
  
     alias carta '~/Downloads/CARTA.AppImage'

  and 
  
  .. code-block:: tcsh
 
     source ~/.cshrc
     carta 
  
  or
  
  .. code-block:: tcsh
 
     source ~/.tcshrc
     carta 

.. note::
   On RedHat7 machines, an updated 'nss' package may need to be installed.
   
   .. code-block:: bash 
   
      sudo yum install nss


.. note::
   On RedHat7 machines after starting the AppImage, you may see a warning about 'Fontconfig'. It does not affect usage of CARTA, but the warning can be removed by installing the fontconfig package.
   
   .. code-block:: bash
   
     sudo yum install fontconfig


.. note::
   For this v1.3 release we are providing a combined desktop and remote server capability. 
   
   Invoke remote mode with the "-\\-remote" flag e.g. 

   .. code-block:: bash

     ./CARTA.AppImage --remote 

   or

   .. code-block:: bash

      carta --remote

   If using remote mode on RedHat7 with Firefox browser, the Firefox version needs to be newer than ESR 52.7.2 and have "*wasm*" streaming enabled (See :ref:`troubleshooting` for more information).


CARTA-desktop: Redhat 6
-----------------------
Neither AppImage nor Electron runs on RedHat 6, therefore we supply a "standalone" remote server package. It is intended for RedHat 6 use only, however it can also run on both RedHat 7 and Ubuntu 16.04 LTS/18.04 LTS.

Please follow the steps:

1. `Download the tar.gz file <https://github.com/CARTAvis/carta-releases/releases/download/v1.3.1/CARTA-v1.3.1-remote.tgz>`_

2. Extract the archive

   .. code-block:: bash

      tar -xvf CARTA-v1.3.1-remote.tgz

3. Execute the carta script within the "CARTA-v1.3.1-remote" folder

   .. code-block:: bash

      ./carta

4. Follow the onscreen instructions to copy and paste the unique URL into your web browser.

5. Usage instructions are slightly different from the Desktop versions so please check the help command with "./carta -\\-help". For example, you can not open images directly (can not "./carta image.fits")

6. You could make an alias in your ~/.bashrc file similar to this 

   .. code-block:: bash

      alias carta='~/CARTA-v1.3.1-remote/carta'

   If you use csh or tcsh, the syntax differs only in that there is no equals sign, therefore it would be 
  
   .. code-block:: tcsh
  
      alias carta '~/Downloads/CARTA-v1.3.1-remote/carta'

   and 
  
   .. code-block:: tcsh
 
      source ~/.cshrc
      carta 
  
   or
  
   .. code-block:: tcsh
 
      source ~/.tcshrc
      carta 

.. _commandLineStartup:

Command line startup 
--------------------
CARTA can be started through the command line. To enable this feature, an alias of the CARTA executable needs to be created first. 

Once it is set, simply typing "carta" then hitting the "return" key will launch CARTA. 

.. code-block:: bash 
   
   carta              # file browser will show images in the current working directory ($PWD)

The CARTA executable alias accepts keyword arguments or flags to configure how the CARTA backend is initialized. Common use cases are summarized below.

* open an image via the command line

  .. code-block:: bash 
   
     carta M51.fits     # to open an image in FITS format
     carta M51.image    # to open an image in CASA format
     carta M51.hdf5     # to open an image in HDF5-IDIA format
     carta M51.im       # to open an image in MIRIAD format
   
* launch CARTA and have the file browser to show images at a custom directory

  .. code-block:: bash 
   
     carta /my/image/directory     


If CARTA is installed on a remote server, and users access the server via the ssh protocol, CARTA backend can be initialized via the following options.

* initialize a remote CARTA backend service with both frontend and backend ports selected automatically:

  .. code-block:: bash 
   
     carta --remote     # CARTA URL will be shown in the prompt. 
                        # Copy-and-paste the URL to your local browser (Chrome, Firefox, or Safari)
   
     =========== what you may see after hitting return key ===========
     Starting CARTA in remote mode
 
     To access CARTA, please enter either of the following URLs in your local web browser: 
 
     www.carta.edu:2000/?socketUrl=ws://www.carta.edu:3000
 
     OR
 

     192.168.1.312:2000/?socketUrl=ws://192.168.1.312:3000
 
     Press ctrl+c to exit

  .. tip::
     When using remote mode, an image may be opened directly using a modified URL. For example, if we wanted to open a remote image file "/home/acdc/CARTA/Images/jet.fits", we would append
     
     .. code-block:: bash 
     
        &folder=/home/acdc/CARTA/Images&file=jet.fits
        
     to the end of the URL (e.g., http://www.carta.edu:2000/?socketUrl=ws://www.carta.edu:3000). In this example our full URL is 
     
     .. code-block:: bash 
    
        http://www.carta.edu:2000/?socketUrl=ws://www.carta.edu:3000&folder=/home/acdc/CARTA/Images&file=jet.fits 
        
     Please note that it is necessary to give *full* path. Tilde (~) is not allowed.


* initialize a remote CARTA backend service with customized frontend (e.g., 5678) and backend (e.g., 1234) ports:

  .. code-block:: bash 
   
     carta --remote --port=1234 --fport=5678
  
     =========== what you may see after hitting return key ===========
     Starting CARTA in remote mode
 
     To access CARTA, please enter either of the following URLs in your local web browser: 
 
     www.carta.edu:5678/?socketUrl=ws://www.carta.edu:1234
 
     OR

 
     192.168.1.312:5678/?socketUrl=ws://192.168.1.312:1234
 
     Press ctrl+c to exit

  For CARTA-server administration, the following advanced keyword arguments may be adopted.

* to set a limit of the file list scope:

  .. code-block:: bash 
   
     carta --remote --root=/lustre/users/bob     # user cannot navigate up to /lustre/users
                                                 # --root defaults to "/"

* to set a number of threads for the CARTA backend service:

  .. code-block:: bash 
   
     carta --remote --threads=24     # set 24 threads for the CARTA backend service
                                     # --threads defaults to number of cores on your system

An online user manual regarding all the above mentioned keyword arguments is also available.

.. code-block:: bash 
   
   carta --help     # show all available keyword arguments with explanations. 

   usage: carta [] CARTA file browser will default to the current path.
             [<path>]                 CARTA file browser will default to the specified
                                      path <path> e.g. carta ~/CARTA/Images
             
             [<image>]                CARTA will directly open the image named <image>
                                      e.g. carta aJ.fits or carta ~/CARTA/Images/aJ.fits
             
             [--folder=<path>]        Optional: An alternative way to define the
                                      default CARTA file browser path.
                                      Note: Not for directly opening an image.
             
             [--help]                 View this help output
   
   Remote mode flags
             [--remote]               start CARTA in 'remote' mode. For accessing CARTA's
                                      frontend through your webrowser rather than the standard 
                                      Electron interface. A free websocket port and a frontend
                                      port will be chosen automatically.
             
             [--port=<number>]        Optional: Manually choose a websocket port for the
                                      backend. CARTA will check if the port is available
                                      and issue a warning if not. A typical value is
                                      between 1025-65535.
             
             [--fport=<number>]       Optional: Manually choose a frontend port for the
                                      CARTA web interface. CARTA will check if the port
                                      is available and issue a warning if not. A typical
                                      value is between 1025-65535.
   
   Advanced usage flags
             [--root=<path>]          Define the lowest path the file browser can
                                      navigate to. e.g. carta --root /home/bob means the 
                                      the file browser can not access anything in /home
                                      Note: --root can not be set inside --folder.
             
             [--threads=<number>]     Set the number of threads. It controls how many
                                      tasks CARTA handles simultaneosuly. The default
                                      value is set as 4
             
             [--omp_threads=<number>] Set the number of OpenMP threads. It controls
                                      how trivially parallelisable tasks are split
                                      by CARTA. The default value is the
                                      automatically detected number of cores on
                                      your system; usually 4 or 8 on a typcial
                                      desktop or laptop.
            


.. _troubleshooting:


Troubleshooting 
---------------
In this section, we provide common issues we have experienced so far and provide solutions. If none of the solutions work, please do contact `CARTA Helpdesk <carta_helpdesk@asiaa.sinica.edu.tw>`_ for help.

* I see a blank image...

  If you are using vnc:

  .. tip::
     The following is a tip for VNC users. 
   
     If your VNC connection passes through an intermediate or 'gate' machine, e.g. 
   
     <local machine> - <gate machine> - <remote machine>,
   
     you may need to do an additional port mapping step.

     Assuming you have successfully connected to <remote machine> and have started the CARTA remote server there, you will see the CARTA URL with two unique port numbers
     e.g.
    
     .. code-block:: bash 
   
        <remote machine>:<1st port number>/?socketUrl=ws://<remote machine>:<2nd port number>

     On your local machine, open a new terminal and enter the following command:

     .. code-block:: bash
   
        ssh -L 1234:<remote machine>:<1st port number> -L 5678:<remote machine>:<2nd port number> <username>@<gate machine>

     You can now enter 
   
     .. code-block:: bash 
   
        <remote machine>:1234/?socketUrl=ws://<remote machine>:5678
      
     in your local machine's web browser to connect to CARTA remote server running on the remote machine (1234 and 5678 are given as an example. You may choose different port numbers if you wish).

     <remote machine> can either be the machine's hostname or IP address.

  .. tip::
     If you are running the RedHat7 AppImage version on a VNC server but loaded images appear blank, please use the following prefix when starting the AppImage: 

     .. code-block:: bash
     
        LIBGL_ALWAYS_INDIRECT=1 ./CARTA.AppImage 

     Loaded images should now render correctly.

* After copy-and-paste a CARTA URL, I see the CARTA GUI is not initialized...

  Check your browser version. It needs to support "*wasm*" streaming and be enabled. More information about browser support of WebAssembly can be found at https://caniuse.com/#search=WebAssembly 

  CARTA utilises WebAssembly and that was introduced in version 52 of Firefox. Some RedHat6 and RedHat7 distributions may have versions of Firefox earlier than version 52. If that is the case, we highly recommend that you update to a more recent Firefox version with "sudo yum update firefox".

  Other RedHat7 distributions may have Firefox 52 ESR which although having WebAssembly support, it is deactivated by default. We still recommend updating to a newer version of Firefox, but if you can not, you can try activating WebAssembly as follows:

  1) Open a new tab and enter "about:config" in the URL bar. 
  2) A warning message will appear. Click the button to continue. 
  3) In the search box enter "wasm" and the list will filter down to a few results. 
  4) Double click each line related to "javascript.options.wasm" so that the "Value" column shows them as "true". 
  5) Then simply close the "about:config" tab and the CARTA frontend should now load properly.

  As for the Chrome browser, Webassembly support was introduced in Chrome version 51, but versions 51 to 56 have it deactivated by default. To activate WebAssembly in Chrome 51 to 56 enter "chrome://flags" in the URL bar, type WebAssembly in the search box that appears, and change each WebAssembly option to "Enabled". If you have Chrome version 57 or newer, WebAssembly should be activated by default. 

  

* CARTA does not launch...

  Check if there is existing "carta_backend" process running. The port number may conflict.

* The RedHat7 AppImage does not open and it prints a message suggesting to extract the AppImage using the "-\\-appimage-extract" flag.

  This error is due to lack of FUSE (File System in Userspace) support. We suspect that FUSE support in RedHat7 systems may be disabled in some institute environments for security reasons. If that is the case, we recommend using the 'remote' version of CARTA instead.


* "**backspace**" does not delete a region...

  If using CARTA remote mode in Firefox on MacOS, you may find the "**backspace**" key navigates back a page instead of removing a region. This behaviour can be prevented by modifying your Firefox web browser settings:

  1. Enter about:config in the address bar.
  2. Click "I accept the risk!"
  3. A search bar appears at the top of a long list of preferences. Search for "browser.backspace_action"
  4. It will likely have a value of 0. Double click it, and then modify it to a value of "2".
  5. Close the about:config tab and now backspace will no longer navigate back a page.