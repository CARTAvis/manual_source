.. _about_gui:

Graphical user interface
========================
The graphical user interface (GUI) of CARTA is designed to be flexible and user friendly to support most of use cases, such as continuum image analysis, or spectral line cube analysis, etc. In this section, we introduce the GUI and provide examples to guide users to get familiar with configuring layouts via mouse interactions. Examples on how to interact with regions and charts are provided as well.


Components
----------
The GUI of CARTA is classified into different components:

* main window
* menu bar
* widget bar
* panel (docked widget)
* floating widget
* tab
* dialog
* status icon


.. raw:: html

   <img src="_static/carta_gui.png" 
        style="width:100%;height:auto;">
   


The main window consists of a set of panels and each panel may hold multiple docked widgets in tabs. For example, in the above figure there are five panels in the main window and there are two tabs in the bottom-left panel. A tab or a docked widget may be detached to become a floating widget. The menu bar provides control options, such as image input/output, launching widgets, getting helps, etc. The widget bar provides tools to view or analyze images. The icon at the top-right corner of the main window is an indicator of server (backend) status. A dialog provides options to configure compoments, such as image layout, or region properties, etc.



Configuring the layout
----------------------
The layout configuration can be changed by mouse operations, like single click or drag-and-drop. In the examples below, the drag-and-drop action is guided on the GUI with a semi-transparent rectangle. Various operations are demonstrated below.


.. _resizing_a_panel:

Resizing a panel
^^^^^^^^^^^^^^^^
As shown in the example below, a panel can be resized by dragging its borders. After a panel is resized, nearby panels are resized automatically to fit the new layout. Note that the appearance of the UI elements is adaptive to the size of the panel, as seen in the **render configuration** widget or the **animator** widget in the example. 


.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_resizing_panel.mp4" type="video/mp4">
   </video>



Relocating a tab as a new panel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A tab can be relocated by dragging its title to a desired new panel. The target location is visualized with a semi-transparent box, as shown in the example below.


.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_relocating_tab_as_panel.mp4" type="video/mp4">
   </video>

Relocating a tab to another panel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A tab can be moved to other existing panel by dragging its title to the upper boarder of the target panel, as shown in the example below.


.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_relocating_tab_as_tab.mp4" type="video/mp4">
   </video>




Maximixing and restoring a panel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
By clicking the **maximize** icon at the top-right corner of a panel, the panel (including all tabs) will be maximized to the main window. By clicking the **restore** icon, the panel will be restored to its original location.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_max_min_panel.mp4" type="video/mp4">
   </video>

Detaching and attaching a tab
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
By clicking the **detach** (unpin) icon at the top-right corner of a panel, the activated tab will be detached to become a floating widget. By dragging the **attach** (pin) icon, a floating widget will be attached to an existing panel or as a new panel.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_detach_attach_tab.mp4" type="video/mp4">
   </video>


Creating a widget as a floating widget or as a tab
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A widget is activated as a floating widget by clicking the button in the widget bar. Alternatively, a widget can be activated as a tab by dragging the button in the widget bar directly to a desired location.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_activating_widget.mp4" type="video/mp4">
   </video>

Light and dark theme
^^^^^^^^^^^^^^^^^^^^
CARTA supports a light (default) and dark theme. The theme can be changed using the **View** -> **Interface** menu item, or the shortcut **shift** + **D**.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_theme.mp4" type="video/mp4">
   </video>


.. _mouse_interaction_with_images:

Mouse interactions with images
------------------------------

Zooming
^^^^^^^
The image can be zoomed in by scrolling up and zoomed out by scrolling down.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_mouse_images_zoom.mp4" type="video/mp4">
   </video>


Panning
^^^^^^^
The image can be panned equivalently by single-clicking a position in the image. The image will be re-centered at that position in the view.  

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_mouse_images_pan.mp4" type="video/mp4">
   </video>

If it is intended to pan *inside* a region, please hold **command** (mac) or **ctrl** (linux) key and click inside a region, or simply use middle click. Single click on a region will change the region state to "selected".  

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_mouse_images_pan_roi.mp4" type="video/mp4">
   </video>


.. _mouse_interaction_with_regions:

Mouse interactions with region of interest
------------------------------------------

Region creation
^^^^^^^^^^^^^^^
A region can be created by firstly entering the region creation mode then dragging on the image viewer. To enter the region creation mode, click the *region* button at the bottom-right corner of the image viewer or press "**c**" key. Double-clicking the region icon brings up all available region types (in version 1.1, only rectangle and ellipse are available). As a default, a region is created in the "center-to-corner" mode. To temporarily switch to "corner-to-corner" mode, hold "**commmand**" (mac) or "**ctrl**" (linux) key then drag. A symmetric region such as "circle" or "square" can be created by holding **shift** key then dragging.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_roi_creation.mp4" type="video/mp4">
   </video>


Region selection and modification
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Click on a region will change the region state to "selected" and the selected region will be highlighted in the region list widget. Alternatively, a region can be selected by clicking the region list. CARTA provides the flexibility to select "region in region" as demostrated in the following video. The layer order of regions is adjusted automatically based on the region size. To de-select all regions, press "**esc**" key.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_roi_selection.mp4" type="video/mp4">
   </video>

Double-click on a region or a region in the region list brings up the region property dialog. The dialog allows users to modify region's name, location, shapes, and region cosmetics. Pressing "**delete**" key will remove the selected region. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_roi_modification.mp4" type="video/mp4">
   </video>



.. _mouse_interaction_with_charts:

Mouse interactions with charts
------------------------------

Zooming
^^^^^^^
A chart (profiles and histograms) can be zoomed by wheel scrolling.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_mouse_charts_zoom1.mp4" type="video/mp4">
   </video>


Alternatively, horizontal zoom, vertical zoom, and box zoom are supported.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_mouse_charts_zoom2.mp4" type="video/mp4">
   </video>


Panning
^^^^^^^
Dragging while holding the shift key pans the chart.


.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_mouse_charts_pan.mp4" type="video/mp4">
   </video>

Resetting range
^^^^^^^^^^^^^^^
Double-clicking on the chart resets the plotting range.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_mouse_charts_reset.mp4" type="video/mp4">
   </video>


Controls and shortcuts
----------------------
CARTA supports keyboard shortcuts to enable certain controls without using a mouse. A summary is accessible via the menu **Help** -> **Controls and Shortcuts**, or the shortcut **shift** + **?**. The shortcuts are slightly different depending on the operating system in use. The shortcuts for each operating system are summarized in the following table.


+----------------------------------+----------------------------+-----------------------------+
| Control                          | macOS                      | Linux                       |
+==================================+============================+=============================+
| **Help**                         |                            |                             |
+----------------------------------+----------------------------+-----------------------------+
| Controls and shortcuts           | shift + ?                  | shift + ?                   |
+----------------------------------+----------------------------+-----------------------------+
| **Navigation**                   |                            |                             | 
+----------------------------------+----------------------------+-----------------------------+
| Pan image                        | click                      | click                       |
+----------------------------------+----------------------------+-----------------------------+
| Pan image (inside region)        | cmd + click / middle-click | ctrl + click / middle-click |
+----------------------------------+----------------------------+-----------------------------+
| Zoom image                       | mouse wheel                | mouse wheel                 |
+----------------------------------+----------------------------+-----------------------------+
| **Regions**                      |                            |                             |
+----------------------------------+----------------------------+-----------------------------+
| Region properties                | double-click               | double-click                | 
+----------------------------------+----------------------------+-----------------------------+
| Delete selected region           | del / backspace            | del / backspace             |
+----------------------------------+----------------------------+-----------------------------+
| Toggle region creation mode      | c                          | c                           |
+----------------------------------+----------------------------+-----------------------------+
| Deselect region                  | esc                        | esc                         |
+----------------------------------+----------------------------+-----------------------------+
| Corner-to-corner region creation | cmd + drag                 | ctrl + drag                 |
+----------------------------------+----------------------------+-----------------------------+
| Symmetric region creation        | shift + drag               | shift + drag                |
+----------------------------------+----------------------------+-----------------------------+
| **Appearance**                   |                            |                             |
+----------------------------------+----------------------------+-----------------------------+
| Toggle light/dark theme          | shift + D                  | shift + D                   |
+----------------------------------+----------------------------+-----------------------------+
| **Cursor**                       |                            |                             |
+----------------------------------+----------------------------+-----------------------------+
| Freeze/unfreeze cursor           | F                          | F                           |
+----------------------------------+----------------------------+-----------------------------+
| **File controls**                |                            |                             |
+----------------------------------+----------------------------+-----------------------------+
| Open image                       | cmd + O                    | ctrl + O                    |
+----------------------------------+----------------------------+-----------------------------+
| Append image                     | cmd + L                    | ctrl + L                    |
+----------------------------------+----------------------------+-----------------------------+
| Export image                     | cmd + E                    | ctrl + E                    |
+----------------------------------+----------------------------+-----------------------------+
| **Frame controls**               |                            |                             |
+----------------------------------+----------------------------+-----------------------------+
| Next frame                       | cmd + ]                    | ctrl + ]                    |
+----------------------------------+----------------------------+-----------------------------+
| Previous frame                   | cmd + [                    | ctrl + [                    |
+----------------------------------+----------------------------+-----------------------------+
| Next channel                     | cmd + up                   | ctrl + up                   |
+----------------------------------+----------------------------+-----------------------------+
| Previous channel                 | cmd + down                 | ctrl + down                 |
+----------------------------------+----------------------------+-----------------------------+
| Next Stokes                      | cmd + shift + up           | ctrl + shift + up           |
+----------------------------------+----------------------------+-----------------------------+
| Previous Stokes                  | cmd + shift + down         | ctrl + shift + down         |
+----------------------------------+----------------------------+-----------------------------+

