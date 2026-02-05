.. _workspace:

Workspace
=========

.. note::
   Full workspace features are under development. In the v5.1 release, workspace support is limited.


Workspace saving and restoring
------------------------------

A "workspace" in CARTA refers to a snapshot of the GUI state that you can save and restore for future usage. Ultimately, a CARTA workspace will also be shareable so that you can use it as a collaborative tool to work with your collaborators over the internet. In this initial implementation, the following components are saveable and restorable:

* All loaded images except generated in-memory images (e.g., moment images, PV images, etc.)
* Image matching states, including spatial, spectral, and raster
* Raster rendering
* Contour rendering layers
* Vector overlay layers
* Regions and image annotations

.. note::
   Image view grid layout, GUI layout, and preferences are not supported yet.


To save a workspace, use the menu "**File**" -> "**Save Workspace**". To restore a workspace, use the menu "**File**" -> "**Open Workspace**". 

.. raw:: html

   <a href="_static/carta_fn_workspace.png" target="_blank">
       <img src="_static/carta_fn_workspace.png" 
            style="width:100%;height:auto;">
   </a>

When a workspace is selected in the file list, basic workspace information is displayed in the panel on the right-hand side, including:

* A screenshot of the GUI (currently limited to the Image Viewer only)
* The name of the workspace
* Number of regions
* File name of the spatial reference image
* File name of the spectral reference image
* File name of the raster scaling reference image
* A list of all image files and their validation results

If the image validation result is "invalid", please check if the image is still accessible on the file system. We encourage you to reach out for assistance if you encounter an error. You can contact our `Helpdesk <mailto:support@carta.freshdesk.com>`_ or visit our `GitHub <https://github.com/CARTAvis/carta/issues>`_ repository to file an issue.


Workspace sharing (experimental; carta-controller-only feature)
-----------------------------------------------------------------
If you are using a site-deployment-mode version of CARTA with the CARTA `controller <https://carta-controller.readthedocs.io/en/dev/>`_, you may share workspaces with your collaborators via a URL. Once you have saved a workspace via "**File**" -> "**Save Workspace**", a "**Share**" button in gray color will appear in the top-right corner of the CARTA GUI. When you click the "**Share**" button, a popup window will prompt you to generate a unique URL linked to the workspace that you have just saved. Via the URL, your collaborators will be able to restore and view the workspace. 

.. raw:: html

   <a href="_static/carta_fn_workspace_share1.png" target="_blank">
       <img src="_static/carta_fn_workspace_share1.png" 
            style="width:100%;height:auto;">
   </a>

.. raw:: html

   <a href="_static/carta_fn_workspace_share2.png" target="_blank">
       <img src="_static/carta_fn_workspace_share2.png" 
            style="width:100%;height:auto;">
   </a>


Please note that your collaborators need to have file read permissions for all the workspace images to restore it fully. If there are images that your collaborators do not have permission to read, those images will be skipped in the workspace restoration process, and a warning will be displayed.

