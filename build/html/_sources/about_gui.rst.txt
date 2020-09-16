.. _about_gui:

Graphical user interface
========================
The graphical user interface (GUI) of CARTA is designed to be flexible and user friendly to support most use cases, such as continuum image analysis, or spectral line cube analysis, etc. In this section, we introduce the GUI and provide examples to guide users to get familiar with configuring layouts via mouse interactions. Examples on how to interact with regions and charts are provided as well.




Components
----------
The GUI of CARTA is classified into different components:

* Main window
* Menu bar
* Region bar
* Widget bar
* Dialogue bar
* Tool bar
* Panel (docked widget)
* Floating widget
* Tab
* Dialogue
* Status icon

.. raw:: html

   <img src="_static/carta_gui.png" 
        style="width:100%;height:auto;">
   

The main window consists of a set of panels and each panel may contain multiple docked widgets as tabs. For example, in the above figure there are five panels in the main window and there are two docked widgets as tabs in the bottom-left panel. A tab or a docked widget may be detached to become a floating widget. The menu bar provides control options, such as image input/output, launching widgets, getting help, etc. The widget bar provides widgets to view or to analyze images. The dialogue bar provides dialogues for configurations. The region bar provides shortcut buttons for creating region of interest. The icons at the top-right corner of the main window are the indicators of server (backend) status and data stream. A dialogue provides options to configure components, such as image layout, or region properties, etc. A tool bar provides tools for a widget, such as zoom buttons for the image viewer widget or the export options for the spectral profile widget, etc. 


.. _quickstart:

Quickstart guide
----------------
In this section, basic instructions on how to interact with CARTA through the graphical user interface (GUI) are introduced. A summary of the full set of controls and shortcuts can be found via the "Help" -> "Controls and Shortcuts" menu or via "**shift**"+"**?**" keys. 

Image viewing interactions
^^^^^^^^^^^^^^^^^^^^^^^^^^
To zoom an image

* use mouse wheel to scroll
* use the zoom buttons at the bottom-left corner of image viewer

To pan an image

* use mouse to drag on image (default) 
* hold “**command**” (mac) / “**ctrl**” (linux) key then mouse click

To pan *inside* a region

* hold “**command**” (mac) / “**ctrl**” (linux) key then mouse click
* mouse middle click

Region of interest interactions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
To enable region creation mode

* press “**C**” key

To create symmetric regions (circle or square)

* hold “**shift**” key then mouse drag

To create / modify a region (rectangle or ellipse) with the alternative mode (center-to-corner or corner-to-corner).

* hold “**command**” (mac) / “**ctrl**” (linux) key then mouse drag

To configure a region

* double mouse click on the region list
* double mouse click inside a region in image viewer

To lock/unlock a region

* press "**L**" key
* press "**shift**" + "**L**" key to unlock all locked regions
* click the lock icon in the region list widget
* click the lock icon in the region configuration dialogue.

To delete a region

* press “**delete**” key
* press “**backspace**” key
* click the delete button in the region configuration dialogue.

Cursor update
^^^^^^^^^^^^^
To freeze/unfreeze cursor position update in the image viewer

* press “**F**” key

Chart interactions
^^^^^^^^^^^^^^^^^^
Focused zoom

* use mouse wheel to scroll

Horizontal zoom

* hold-and-drag in the horizontal direction

Vertical zoom

* hold-and-drag in the vertical direction

Box zoom

* hold-and-drag in the diagonal direction

Reset zoom

* double mouse click

Horizontal pan

* hold “**shift**” key then mouse drag horizontally



Getting help
------------
This online user manual can be accessed via "**Help**" -> "**Online manual**". A new browser window will be launched and show the CARTA user manual. In addition, an in-app help manual (no internet is required) can be accessed via the "?" icon at the top-right corner of a widget or a dialogue. The help content will be displayed in a drawer.


.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_inapphelp.mp4" type="video/mp4">
   </video>



Configuring the layout
----------------------
The layout configuration can be changed by mouse operations, such as click or drag-and-drop. The drag-and-drop action is guided on the GUI with a semi-transparent guider. Various operations are demonstrated below.


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
A tab can be moved to another existing panel by dragging its title to the upper boarder of the target panel, as shown in the example below.


.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_relocating_tab_as_tab.mp4" type="video/mp4">
   </video>

Maximizing and restoring a panel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A widget is activated as a floating widget by clicking the button in the widget bar. Alternatively, a widget can be activated as a tab by dragging the button in the widget bar directly to a desired location.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_activating_widget.mp4" type="video/mp4">
   </video>


Light and dark theme
^^^^^^^^^^^^^^^^^^^^
CARTA supports light and dark themes. The default theme is determined automatically from the operating system (if applicable). The theme can be changed using the **View** -> **Theme** menu item, or the shortcut **shift** + **D**.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_theme.mp4" type="video/mp4">
   </video>


Custom layout, save, and restore
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
CARTA has a set of preset layouts suitable for different kinds of image analysis. These layouts are accessible via the menu **View** -> **Layouts** -> **Existing layouts**. 

.. raw:: html

   <img src="_static/carta_gui_layout_menu.png" 
        style="width:100%;height:auto;">

Users may further customize a preset layout or make a new layout from scratch for different purposes and save it for the future. To save a custom layout, use the menu **View** -> **Layouts** -> **Save layout**. A name is required when saving a layout (e.g., "my layout 01" in the above example). 

A saved layout can be restored via the menu **View** -> **Layouts** -> **Existing layouts**. The activated layout is highlighted in blue ("Default" in the above example). Saved layouts can be removed via the menu **View** -> **Layouts** -> **Delete layout**.

By default, CARTA will load the "Default" preset layout when initialized. Which layout, including user customized layouts, should be loaded can be further defined via the preferences dialogue **File** -> **Preferences**. The initial layout can be set via **Global** -> **Initial layout**.

.. raw:: html

   <img src="_static/carta_gui_layout_preference.png" 
        style="width:90%;height:auto;">


User preferences
----------------
CARTA provides a number of preferences for users to customize the GUI, including layouts. The preferences are persistent so that next time when users launch CARTA, all the preferences and a layout are restored. The preferences dialogue is accessible via the menu **File** -> **Preferences**. Preferences are effective after CARTA reloads, except few that are effective immediately. Below we summarize the options of all preferences.  



* Global

  * Theme: to adopt light or dark theme of the GUI (default: automatic) [effective immediately]
  * Auto-launch file browser: to launch the file browser or not when CARTA is initialized (default: yes)
  * Initial layout: the layout to adopt when CARTA is initialized (default: "Default")
  * Initial cursor position: to fix the cursor position on the image or not when CARTA is initialized. If it is fixed, a cross will be shown at the image center. Use "**F**" key to switch to the tracking mode (default: Tracking)
  * Initial zoom level: to select the initial zoom level of the image to be filling up the field of view or to be displayed as one image pixel to one screen pixel ratio (default: "Zoom to fit")
  * Zoom to: zoom with respect to cursor position or image viewer center
  * Enable drag-to-pan: pan image by mouse drag or mouse click
  * WCS matching on append: trigger WCS matching automatically for newly appended images
  * Spectral matching: spectral convention adopted for spectral matching 

  .. raw:: html

   <img src="_static/carta_gui_preferences_global.png" 
        style="width:100%;height:auto;">


* Render configuration

  * Default scaling: the scaling function of the color map (default: linear)
  * Default color map: the default color for the raster image (default: inferno)
  * Default percentile ranks: the default clip level for the color map (default: 99.9%)
  * NaN color: color for rendering NaN pixels

  .. raw:: html

   <img src="_static/carta_gui_preferences_renderConfig.png" 
        style="width:100%;height:auto;">



* Contour configuration

  * Generator type: tools for generating a set of contour levels to be calculated and rendered
  * Smoothing mode: image smoothing mode before calculating contour vertices
  * Default smoothing factor: kernel size in number of pixels for image smoothing 
  * Default contour levels: number of contour levels to be generated by the level generator
  * Thickness: line thickness of contour rendering
  * Default color mode: render contours with a constant color or a color map
  * Default color map: color map for contour rendering
  * Default color: constant color for contour rendering

  .. raw:: html

   <img src="_static/carta_gui_preferences_contourConfig.png" 
        style="width:100%;height:auto;">


* Overlay configuration

  * AST color: the color for the WCS overlay, including border, grid line, ticks, labels, and title (default: blue)
  * AST grid visible: to show grid line or not as default (default: yes)
  * AST label visible: to show coordinate labels or not as default (default: yes)
  * WCS format: the format of the displayed world coordinate. The default is "automatic" which means for galactic or ecliptic system, the world coordinate is displayed in decimal degrees, and for FK4, FK5, or ICRS, the world coordinate is displayed in sexigesimal format. (default: automatic) [effective for new images]
  * Beam visible: show a spatial resolution element
  * Beam color: color for rendering a spatial resolution element
  * Beam type: styling for rendering a spatial resolution element
  * Beam width: line width for rendering a spatial resolution element

  .. raw:: html

   <img src="_static/carta_gui_preferences_overlayConfig.png" 
        style="width:100%;height:auto;">



* Region

  * Color: the default color of a region (default: cyan) [effective for new regions]
  * Line width (px): the default line width of a region (default: 2) [effective for new regions]
  * Dash length (px): the default dash length of the line composing a region. The default is to show a region in solid line (default: 0) [effective for new regions]
  * Region type: the default selected region in the tool bar of the image viewer (default: rectangle)
  * Region size: the default region (screen) size when creating by a single click (rectangle and ellipse)
  * Creation mode: the method of how a rectangle or an ellipse is created by mouse dragging. Two methods are supplied: center-to-corner and corner-to-corner (default: center-to-corner) [effective for new regions]

  .. raw:: html

   <img src="_static/carta_gui_preferences_region.png" 
        style="width:100%;height:auto;">


* Performance

  * Low bandwidth mode: reduce required image resolution by a factor of two and reduce the cursor responsiveness to 400 ms
  * Compression quality (image): a parameter (1~32) to control the image quality with lossy compression. The higher the number is, the better quality the images are. Choose with caution. (default: 11) [effective immediately]
  * Compression quality (animation): a parameter (1~32) to control the animation quality with lossy compression. The higher the number is, the better quality the images are. Choose with caution. (default: 9) [effective immediately]
  * GPU tile cache size (number of tiles): the cache size of GPU for tiles (default: 512)
  * System tile cache size (number of tiles): the cache size of system memory for tiles (default: 4096)
  * Contour rounding factor: number of contour vertices per pixel
  * Contour compression level: compression quality of contour image data
  * Contour chunk size: chunk size of contour data streaming
  * Contour control map resolution: control map resolution for reprojecting contour vertices to other coordinate system
  * Stream image tiles while zooming: streaming image tiles for all sampled zoom levels
  * Stop animation playback in: a timer to automatically stop animation playback for server resource management

  .. raw:: html

   <img src="_static/carta_gui_preferences_performance.png" 
        style="width:100%;height:auto;">



* Log events

  This is for debugging purpose. Normal users can skip this part. The client side and the server side of CARTA communicate through "protocol buffer" messages. For debugging purpose, advanced users can identify a set of messages in the list and launch browser's Javascript console to see those messages.

  .. raw:: html

   <img src="_static/carta_gui_preferences_log.png" 
        style="width:100%;height:auto;">

.. _mouse_interaction_with_images:

Mouse interactions with images
------------------------------

Zooming an image
^^^^^^^^^^^^^^^^
The image can be zoomed in by scrolling up and zoomed out by scrolling down.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_mouse_images_zoom.mp4" type="video/mp4">
   </video>

Panning an image
^^^^^^^^^^^^^^^^
The image can be panned by mouse drag-and-drop on the image. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_mouse_images_pan.mp4" type="video/mp4">
   </video>

If it is intended to pan *inside* a region, please hold **command** (mac) or **ctrl** (linux) key and click inside a region, or simply use middle click. Single click on a region will change the region state to "selected". With the same operation, users can center an image pixel (regardless it is inside a region or not) in the image viewer.  


.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_gui_mouse_images_pan_roi.mp4" type="video/mp4">
   </video>



.. _mouse_interaction_with_regions:

Mouse interactions with region of interest
------------------------------------------

Region creation
^^^^^^^^^^^^^^^
A region can be created by firstly entering the region creation mode then drawing on the image viewer. To enter the region creation mode, click the *region* button at the bottom-right corner of the image viewer or press "**C**" key. Double-clicking the region icon brings up all available region types (rectangle, ellipse, polygon, and point, as of v1.4). Alternatively, users may click the buttons in the region bar at the top of the GUI to enter the region creation mode.

To create a point region, a single click will do. For the rectangle or the ellipse region, it can be created in the "center-to-corner" mode or the "corner-to-corner" mode, depending on the preference setting in the preference dialogue (**File** -> **Preferences** -> **Region**). To temporarily switch to the other mode than the default, hold the "**command**" (mac) or "**ctrl**" (linux) key then drag. "circle" and "square" regions are the special cases of ellipse and rectangle regions, respectively. These symmetric regions can be created by holding **shift** key then dragging. Alternatively, a rectangle region or an ellipse region can be created by a single mouse click. The default size on screen is defined in the preferences dialogue (**File** -> **Preferences** -> **Region**).

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_roi_creation1.mp4" type="video/mp4">
   </video>



To create a polygon region, start with a click followed by a series of clicks to define the control points of a desired polygonal shape and finish with a double click. CARTA detects "complex" polygon (polygon with intersections) and shows it in pink color. Spectral profiles, statistics, or histogram of a complex polygon can still be requested but please note that the results may be beyond users' expectations since the actual pixel coverage depends on *how* a complex polygon is created. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_roi_creation2.mp4" type="video/mp4">
   </video>


Region selection and modification
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Click on a region will change the region state to "selected" and the selected region will be highlighted in the region list widget. Alternatively, a region can be selected by clicking the region list. CARTA provides the flexibility to select "region in region" as demonstrated in the following video. The layer order of regions is adjusted automatically based on the region size. To de-select all regions, press "**esc**" key.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_roi_selection.mp4" type="video/mp4">
   </video>


Double-click on a region or a region in the region list brings up the region property dialogue. The dialogue allows users to modify region's name, location, shapes, and region cosmetics. Pressing "**delete**" or "**backspace**" key will remove the selected region. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_roi_modification.mp4" type="video/mp4">
   </video>


.. tip::
  "**backspace**" does not delete a region...

  If using CARTA remote mode in Firefox on MacOS, you may find the "**backspace**" key navigates back a page instead of removing a region. This behaviour can be prevented by modifying your Firefox web browser settings:

  1. Enter about:config in the address bar.
  2. Click "I accept the risk!"
  3. A search bar appears at the top of a long list of preferences. Search for "browser.backspace_action"
  4. It will likely have a value of 0. Double click it, and then modify it to a value of "2".
  5. Close the about:config tab and now backspace will no longer navigate back a page.


For a polygon region, a new control point can be added by clicking on a line segment. A control point can be deleted by double clicking on the control point.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_roi_creation3.mp4" type="video/mp4">
   </video>


.. _mouse_interaction_with_charts:

Mouse interactions with charts
------------------------------

Zooming a chart
^^^^^^^^^^^^^^^
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


Panning a chart
^^^^^^^^^^^^^^^
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
| Toggle region creation mode      | C                          | C                           |
+----------------------------------+----------------------------+-----------------------------+
| Deselect region                  | esc                        | esc                         |
+----------------------------------+----------------------------+-----------------------------+
| Cancel region creation           | esc                        | esc                         |
+----------------------------------+----------------------------+-----------------------------+
| Switch region creation mode      | cmd + drag                 | ctrl + drag                 |
+----------------------------------+----------------------------+-----------------------------+
| Symmetric region creation        | shift + drag               | shift + drag                |
+----------------------------------+----------------------------+-----------------------------+
| Toggle current region lock       | L                          | L                           |
+----------------------------------+----------------------------+-----------------------------+
| Unlock all regions               | shift + L                  | shift + L                   |
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
| Close image                      | cmd + W                    | ctrl + W                    |
+----------------------------------+----------------------------+-----------------------------+
| Export image                     | cmd + E                    | ctrl + E                    |
+----------------------------------+----------------------------+-----------------------------+
| Import catalogue                 | cmd + C                    | ctrl + C                    |
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
