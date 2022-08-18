.. _about_gui:

Graphical user interface
========================
The graphical user interface (GUI) of CARTA is aimed to be flexible and user friendly to support a wide range of use cases, such as continuum image analysis, spectral line cube analysis, or polarization cube analysis, etc. In this section, we introduce the GUI and provide examples for you to get familiar with layout configuration via mouse actions. Examples on how to interact with images, regions and charts are provided as well.


Components
----------

The CARTA GUI has different components:

* Main browser window
* Menu bar
* Region bar
* Widget bar
* Dialog bar
* Status bar
* Toolbar
* Panel (docked widget)
* Tab
* Floating widget
* Dialog

.. raw:: html

   <img src="_static/carta_gui.png" 
        style="width:100%;height:auto;">
   

The main browser window consists of a set of panels. Each panel may contain multiple docked widgets as tabs. For example, in the above figure there are five panels in the main browser window and there are two docked widgets sharing the same panel as tabs in the bottom-left panel. A tab (also known as a docked widget) may be detached from a panel to become a floating widget. The menu bar provides control options, such as image input/output, launching widgets, and getting help, etc. The widget bar provides widgets to view or to analyze images. The dialog bar provides dialogs for configurations. The region bar provides shortcut buttons for creating regions of interest in the image viewer. The status bar includes indicators of server (backend) status (as a green, orange, or red circle), data stream status (as a green cloud), and new release notification (as an orange envelope). A dialog provides options for configurations, such as image view properties, or region properties, etc. A toolbar provides tools for a widget, such as zoom buttons for the image viewer widget or the export options for the spectral profile widget, for example. 

The layout is highly configurable via mouse and is reusable. Please refer to the section :ref:`layoutConfiguration` for details.


.. _quickstart:

Quick start
-----------
In this section, we provide basic instructions on how to interact with CARTA through the graphical user interface (GUI). A summary of the full set of controls and shortcuts can be found via the "**Help**" -> "**Controls and Shortcuts**" menu or via "**shift**"+"**?**" keys. 

Image view interactions
^^^^^^^^^^^^^^^^^^^^^^^
To zoom an image

* use mouse wheel to scroll
* use the zoom buttons from the toolbar of the image viewer

To pan an image

* use mouse to drag-and-drop on image (default) 
* hold “**command**” (macOS) / “**ctrl**” (Linux) key then mouse click
* mouse middle click

To pan from *inside* a region

* hold “**command**” (macOS) / “**ctrl**” (Linux) key then mouse click
* mouse middle click

Region of interest interactions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
To enable region creation mode

* press “**C**” key
* click the region creation button from the toolbar of the image viewer
* click a target region type from the region bar 

To create a circle region with the ellipse region type or a square region with the rectangle region type

* hold “**shift**” key then drag-and-drop

To create or modify a region (rectangle, ellipse or line) with the alternative mode (center-to-corner v.s. corner-to-corner)

* hold “**command**” (macOS) / “**ctrl**” (Linux) key then drag-and-drop

To configure a region

* double-click on a region entry in the region list widget
* double-click inside a region in the image viewer

To lock/unlock a region

* press "**L**" key
* press "**shift**" + "**L**" key to unlock all locked regions
* click the lock button in the region list widget
* click the lock button in the region configuration dialog

To delete a region

* press “**delete**” key
* press “**backspace**” key
* click the delete button in the region configuration dialog

Cursor update
^^^^^^^^^^^^^
To freeze or unfreeze cursor position update in the image viewer

* press “**F**” key

Chart interactions
^^^^^^^^^^^^^^^^^^
Focused zoom

* use mouse wheel to scroll

Horizontal zoom

* drag-and-drop in the horizontal direction

Vertical zoom

* drag-and-drop in the vertical direction

Box zoom

* drag-and-drop in the diagonal direction

Reset zoom

* double-click

Horizontal pan

* hold “**shift**” key then drag-and-drop horizontally



Getting help
------------
This online user manual can be accessed via the menu "**Help**" -> "**Online manual**". A new browser window will be launched to show this CARTA user manual. In addition, an in-app help manual (no internet is required) can be accessed via the "?" button at the top-right corner of a widget or a dialog. The help content will be displayed in a drawer.


.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_inapphelp_poster.png" preload="none">
     <source src="_static/carta_gui_inapphelp.mp4" type="video/mp4">
   </video>


.. _layoutConfiguration:

Configuring the layout
----------------------
The layout configuration can be changed by mouse actions, such as click or drag-and-drop. The drag-and-drop action is guided with a semi-transparent guider. Various operations are demonstrated below. By mastering this section, you should be able to create, save, and restore custom layouts that fit your use cases.


.. _resizing_a_panel:

Resizing a panel
^^^^^^^^^^^^^^^^
A panel can be resized by applying drag-and-drop action to its borders. After a panel is resized, adjacent panels are resized automatically to fit the new layout. For the image viewer, the image size on screen and the aspect ratio will be displayed after the panel size is changed.


.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_resizing_panel_poster.png" preload="none">
     <source src="_static/carta_gui_resizing_panel.mp4" type="video/mp4">
   </video>

Relocating a tab as a new panel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A tab can be detached from a panel and relocated by dragging its title to a desired location as a new panel. The target location is visualized with a semi-transparent box, as shown in the example below.


.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_relocating_tab_as_panel_poster.png" preload="none">
     <source src="_static/carta_gui_relocating_tab_as_panel.mp4" type="video/mp4">
   </video>


Relocating a tab to another panel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A tab can be moved to another existing panel by dragging its title to the upper border of the target panel, as shown in the example below.


.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_relocating_tab_as_tab_poster.png" preload="none">
     <source src="_static/carta_gui_relocating_tab_as_tab.mp4" type="video/mp4">
   </video>

Maximizing and restoring a panel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
By clicking the "**maximize**" button at the top-right corner of a panel, the panel (including all tabs) will be maximized to the main browser window. By clicking the "**restore**" button, the panel will be restored to its original location.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_max_min_panel_poster.png" preload="none">
     <source src="_static/carta_gui_max_min_panel.mp4" type="video/mp4">
   </video>


Detaching and attaching a tab
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
By clicking the "**detach**" (unpin) button at the top-right corner of a panel, the active tab can be detached as a floating widget. By dragging the "**attach**" (pin) button, a floating widget can be attached to an existing panel or as a new panel.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_detach_attach_tab_poster.png" preload="none">
     <source src="_static/carta_gui_detach_attach_tab.mp4" type="video/mp4">
   </video>

Creating a widget as a floating widget or as a docked widget
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A widget can be activated as a floating widget by clicking the desired widget button from the widget bar. Alternatively, a widget can be activated as a docked widget by dragging the desired widget button from the widget bar directly to a desired location.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_activating_widget_poster.png" preload="none">
     <source src="_static/carta_gui_activating_widget.mp4" type="video/mp4">
   </video>


Light and dark themes
^^^^^^^^^^^^^^^^^^^^^
CARTA supports light and dark themes. The default theme is determined automatically from the operating system (if applicable). The theme can be changed using the menu "**View**" -> "**Theme**", or the shortcut "**shift**" + "**D**".

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_theme_poster.png" preload="none">
     <source src="_static/carta_gui_theme.mp4" type="video/mp4">
   </video>


Custom layout, save, and restore
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
CARTA has a set of preset layouts designed for different kinds of image analysis. These layouts are accessible via the menu "**View**" -> "**Layouts**" -> "**Existing layouts**". 

You may further customize a preset layout for a different purpose and save it for the future. To save a custom layout, use the menu "**View**" -> "**Layouts**" -> "**Save layout**". A name is required when saving a layout (e.g., "my layout 01" in the example). 

A saved layout can be restored via the menu "**View**" -> "**Layouts**" -> "**Existing layouts**". The active layout is highlighted in blue ("Default" in the example). Saved layouts can be removed via the menu "**View**" -> "**Layouts**" -> "**Delete layout**".

.. raw:: html

  <video controls style="width:100%;height:auto;" poster="_static/carta_gui_custom_layout_poster.png" preload="none">
    <source src="_static/carta_gui_custom_layout.mp4" type="video/mp4">
  </video>

By default, CARTA will load the "Default" preset layout when it is initialized. Which layout, including user customized layouts, should be loaded can be further defined via the preferences dialog "**File**" -> "**Preferences**". The initial layout can be set via the "**Initial layout**" dropdown menu of the "**Global**" tab.

.. raw:: html

   <img src="_static/carta_gui_layout_preference.png" 
        style="width:90%;height:auto;">


.. note::
  
  The layout files are kept in :code:`<your home>/.carta/config/layouts` folder as JSON format.


User preferences
----------------
CARTA provides a number of preferences for you to customize the graphical user interface (GUI), including layouts. All the preferences and a layout are restored when you launch CARTA next time. The preferences dialog is accessible via the menu "**File**" -> "**Preferences**". Note that some preferences are effective immediately without the need of a full reload. Below we summarize the options of all preferences.  

.. note::
  
  The preferences file is kept in :code:`<your home>/.carta/config/preferences.json`.



* Global

  * Theme: to adopt light or dark theme of the GUI (default: automatic) [effective immediately]
  * Enable code snippets: to enable the *experimental* feature of the in-app JavaScript scripting interface (default: disabled) [effective immediately]
  * Auto-launch file browser: to launch the file browser or not when CARTA is initialized (default: yes)
  * File list: options on how a file list is generated. If there are usually lots of files in your folders, you can switch to the "filter by extension" mode or "all files" mode to boost performance. (default: filter by file content) [effective immediately]
  * Initial layout: the layout to be restored when CARTA is initialized (default: "Default")
  * Initial cursor position: to fix the cursor position on the image or not when CARTA is initialized. If it is fixed, a cross will be shown at the image center. Use the "**F**" key to switch back to the tracking mode (default: Tracking)
  * Initial zoom level: to select the initial zoom level of a newly loaded image to be filling up the image viewer or to be displayed at 1:1 image-to-screen pixel ratio (default: "Zoom to fit") [effective immediately]
  * Zoom to: zoom with respect to cursor position (a.k.a. focused zoom) or image viewer center [effective immediately]
  * Enable drag-to-pan: pan image by mouse drag or mouse click [effective immediately]
  * WCS matching on append: trigger WCS matching automatically for newly appended images [effective immediately]
  * Spectral matching: spectral convention adopted for spectral matching [effective immediately]
  * Transparent image background: set the background of the exported PNG file as transparent (default: white or black depending on the GUI theme) [effective immediately]
  * Save last used directory: to remember the directory path where you loaded an image as the initial path when CARTA is initialized next time

  .. raw:: html

   <img src="_static/carta_gui_preferences_global.png" 
        style="width:100%;height:auto;">


* Render configuration

  * Default scaling: the scaling function of the color map (default: linear) [effective for new images]
  * Default color map: the default color map for the raster image (default: inferno) [effective for new images]
  * Default percentile ranks: the default clip level for the color map (default: 99.9%) [effective for new images]
  * NaN color: color for rendering NaN pixels [effective immediately]
  * Smoothed bias/contrast: apply smoothed bias and contrast transfer functions to the selected scaling function (default: enabled) [effective immediately]
  
  .. raw:: html

   <img src="_static/carta_gui_preferences_renderConfig.png" 
        style="width:100%;height:auto;">



* Contour configuration

  * Generator type: tools for generating a set of contour levels to be calculated and rendered (default: start-step-multiplier)
  * Smoothing mode: image smoothing mode before calculating contour vertices (default: Gaussian)
  * Default smoothing factor: kernel size in number of pixels for image smoothing (default: 4)
  * Default contour levels: number of contour levels to be generated with the level generator (default: 5)
  * Thickness: line thickness of contour rendering (default: 1)
  * Default color mode: to render contours with a constant color or a color map (default: constant color)
  * Default color map: a color map for contour rendering when the color mode is "color-mapped" 
  * Default color: a constant color for contour rendering when the color mode is "constant color"

  .. raw:: html

   <img src="_static/carta_gui_preferences_contourConfig.png" 
        style="width:100%;height:auto;">



* Vector overlay configuration

  * Default pixel averaging: the block averaging factor before computing the vector overlay data (default: 4x4 pixels)
  * Use fractional intenstiy: to compute fractional polarization intensity if it is possible (default: false)
  * Thickness: the line width to render the vector overlay (default: 1)
  * Default color mode: to render vector overlay with a constant color or a color map (default: constant color)
  * Default color map: a color map for vector overlay rendering when the color mode is "color-mapped" 
  * Default color: a constant color for vector overlay rendering when the color mode is "constant color"

  .. raw:: html

   <img src="_static/carta_gui_preferences_vectorOverlayConfig.png" 
        style="width:100%;height:auto;">


* WCS and image overlay

  * Color: the color for the WCS overlay, including border, grid line, ticks, labels, and title [effective for new images]
  * WCS grid visible: to show grid line or not as default (default: yes) [effective for new images]
  * Label visible: to show coordinate labels or not as default (default: yes) [effective for new images]
  * Cursor info visible: modes to show the cursor info bar in the image viewer (default: active image only) [effective immediately]
  * WCS format: the format of the displayed world coordinate. The default is "automatic" which means for galactic system or ecliptic system, the world coordinate is displayed in decimal degrees, and for FK4, FK5, or ICRS, the world coordinate is displayed in sexigesimal format. (default: automatic) [effective for new images]
  * Colorbar visible: to show a colorbar in the image viewer (default: yes) [effective for new images]
  * Colorbar interactive: when this is activated, if you hover over the colorbar, a dynamic color clip is applied to the raster image immediately to assist you exploring image features (default: activated) [effective for new images]
  * Colorbar position: the position where the colorbar should be rendered in the image viewer (default: right) [effective for new images]
  * Colorbar width (px): the width of the colorbar (default: 15) [effective for new images]
  * Colorbar ticks density (per 100px): the density of the computed ticks per 100 screen pixels (default: 1) [effective for new images]
  * Colorbar label visible: to show a colorbar label (default: no) [effective for new images]
  * Beam visible: to show a spatial resolution element (default: yes) [effective for new images]
  * Beam color: the color for rendering a spatial resolution element [effective for new images]
  * Beam type: the styling for rendering a spatial resolution element (default: open) [effective for new images]
  * Beam width (px): the line width for rendering a spatial resolution element (default: 1) [effective for new images]

  .. raw:: html

   <img src="_static/carta_gui_preferences_WCSImageOverlayConfig.png" 
        style="width:100%;height:auto;">


* Catalog        

  * Displayed columns: displaying only the first N columns of a catalog as default [effective for new catalogs]

  .. raw:: html

   <img src="_static/carta_gui_preferences_catalog.png" 
        style="width:100%;height:auto;">

* Region

  * Color: the default color of a region [effective for new regions]
  * Line width (px): the default line width of a region (default: 2) [effective for new regions]
  * Dash length (px): the default dash length of the line composing a region. The default is to show a region in solid line (default: 0) [effective for new regions]
  * Region type: the default selected region in the toolbar of the image viewer (default: rectangle) [effective for new images]
  * Region size: the default region (screen) size when creating by a single click (rectangle, ellipse, and line) [effective for new regions]
  * Creation mode: the method of how a rectangle or an ellipse is created by mouse dragging. Two methods are supplied: center-to-corner and corner-to-corner (default: center-to-corner) [effective for new regions]

  .. raw:: html

   <img src="_static/carta_gui_preferences_region.png" 
        style="width:100%;height:auto;">


* Performance

  * Low bandwidth mode: to reduce required image resolution by a factor of two and reduce the cursor responsiveness to 400 ms [effective immediately]
  * Limit overlay redraw: to throttle the WCS grid rendering (default: yes) [effective immediately]
  * Compression quality (image): a parameter (1~32) to control the image quality with lossy compression. The higher the number is, the better quality the images are. Choose with caution. (default: 11) [effective immediately]
  * Compression quality (animation): a parameter (1~32) to control the animation quality with lossy compression. The higher the number is, the better quality the animation playback is. Choose with caution. (default: 9) [effective immediately]
  * GPU tile cache size (number of tiles): the cache size of GPU for tiles (default: 512)
  * System tile cache size (number of tiles): the cache size of system memory for tiles (default: 4096)
  * Contour rounding factor: the number of contour vertices per pixel
  * Contour compression level: the compression quality of contour image data
  * Contour chunk size: the chunk size of contour data streaming
  * Contour control map resolution: the control map resolution for reprojecting contour vertices to other coordinate system
  * Stream image tiles while zooming: to stream image tiles for all throttled image zoom levels
  * Stop animation playback in: a timer to automatically stop animation playback for server resource management

  .. raw:: html

   <img src="_static/carta_gui_preferences_performance.png" 
        style="width:100%;height:auto;">


* Telemetry
  
  * Telemetry mode: modes for sending anonymouse usage data to the CARTA development team for development and planning purposes 
  * Log telemetry output: to show telemetry log in the browser debug console (default: off)

  .. raw:: html

   <img src="_static/carta_gui_preferences_telemetry.png" 
        style="width:100%;height:auto;">



* Log events

  This is for debugging purposes. Normal users can skip this part. The client side and the server side of CARTA communicate through "protocol buffer" messages. For debugging purposes, advanced users can identify a set of messages in the list and launch the browser console to see those message flows.

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

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_mouse_images_zoom_poster.png" preload="none">
     <source src="_static/carta_gui_mouse_images_zoom.mp4" type="video/mp4">
   </video>

Panning an image
^^^^^^^^^^^^^^^^
The image can be panned by mouse drag-and-drop on the image. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_mouse_images_pan_poster.png" preload="none">
     <source src="_static/carta_gui_mouse_images_pan.mp4" type="video/mp4">
   </video>

If it is intended to pan *inside* a region, please hold "**command**" (macOS) or "**ctrl**" (Linux) key and click inside a region, or simply use middle click (single click on a region will change the region state to "selected"). With the same operation, users can center an image pixel (regardless if it is inside a region or not) in the image viewer.  


.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_mouse_images_pan_roi_poster.png" preload="none">
     <source src="_static/carta_gui_mouse_images_pan_roi.mp4" type="video/mp4">
   </video>



.. _mouse_interaction_with_regions:

Mouse interactions with region of interest
------------------------------------------

Region creation
^^^^^^^^^^^^^^^
A region can be created by entering the region creation mode then applying drag-and-drop action in the image viewer. To enter the region creation mode, click the "**region**" button at the bottom-right corner of the image viewer or press the "**C**" key. Double-clicking the region icon brings up all available region types (rectangle, ellipse, polygon, point, line, and polyline). Alternatively, users may click the buttons in the region bar at the top of the GUI to enter the region creation mode.

To create a point region, a single click will do. For the rectangle region, the ellipse region or the line region, it can be created in the "center-to-corner" mode or the "corner-to-corner" mode, depending on the preferences setting in the preferences dialog ("**File**" -> "**Preferences** -> "**Region**"). To temporarily switch to the other mode, hold the "**command**" (macOS) or "**ctrl**" (Linux) key then drag-and-drop. The "circle" and the "square" regions are the special cases of the ellipse region and the rectangle region, respectively. These symmetric regions can be created by holding the "**shift**" key followed by the drag-and-drop action. Alternatively, a rectangle region, an ellipse region, or a line region can be created by a single mouse click. The default size on screen is defined in the preferences dialog ("**File**" -> "**Preferences**" -> "**Region**").

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_roi_creation1_poster.png" preload="none">
     <source src="_static/carta_fn_roi_creation1.mp4" type="video/mp4">
   </video>



To create a polygon region or a polyline region, start with a click followed by a series of clicks to define the control points of a desired shape and finish with a double click. CARTA detects a "complex" polygon (polygon with intersections) and shows it in pink color. Spectral profiles, statistics, or histograms of a complex polygon can still be requested but please note that the results may be beyond your expectations since the actual pixel coverage depends on *how* a complex polygon is created. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_roi_creation2_poster.png" preload="none">
     <source src="_static/carta_fn_roi_creation2.mp4" type="video/mp4">
   </video>


Region selection and modification
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Click on a region in the image viewer will change the region state to "active" and the active region will be highlighted in the region list widget. Alternatively, a region can be selected by clicking the region list. CARTA provides the flexibility to select "region in region" as demonstrated in the following video. The layer order of regions is adjusted automatically based on the region size. To deselect a region, click elsewhere in the image viewer or press the "**esc**" key.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_roi_selection_poster.png" preload="none">
     <source src="_static/carta_roi_selection.mp4" type="video/mp4">
   </video>


Double-click on a region in the image viewer or a region in the region list will launch the region configuration dialog. The dialog allows users to modify the region's name, location, shapes, and region cosmetics. Pressing the "**delete**" or the "**backspace**" key will remove the active region. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_roi_modification_poster.png" preload="none">
     <source src="_static/carta_roi_modification.mp4" type="video/mp4">
   </video>


.. tip::
  "**backspace**" does not delete a region...

  When you launch CARTA with the Firefox web browser on macOS, you may find the "**backspace**" key navigates back a page, instead of removing a region. This behaviour can be prevented by modifying your Firefox web browser settings:

  1. Enter about:config in the address bar.
  2. Click "I accept the risk!"
  3. A search bar appears at the top of a long list of preferences. Search for "browser.backspace_action"
  4. It will likely have a value of 0. Double click it, and then modify it to a value of "2".
  5. Close the about:config tab and now backspace will no longer navigate back a page.


For a polygon region or a polyline region, a new control point can be added by clicking on a line segment. A control point can be deleted by double-clicking on the control point.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_roi_creation3_poster.png" preload="none">
     <source src="_static/carta_fn_roi_creation3.mp4" type="video/mp4">
   </video>


.. _mouse_interaction_with_charts:

Mouse interactions with charts
------------------------------

Zooming a chart
^^^^^^^^^^^^^^^
A chart (profiles and histograms) can be zoomed in by scrolling up and zoomed out by scrolling down. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_mouse_charts_zoom1_poster.png" preload="none">
     <source src="_static/carta_gui_mouse_charts_zoom1.mp4" type="video/mp4">
   </video>


Alternatively, horizontal zoom, vertical zoom, and box zoom are supported by drag-and-drop actions.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_mouse_charts_zoom2_poster.png" preload="none">
     <source src="_static/carta_gui_mouse_charts_zoom2.mp4" type="video/mp4">
   </video>


Panning a chart
^^^^^^^^^^^^^^^
A chart can be panned by holding the "**shift**" key then applying drag-and-drop action. Panning in the x direction is supported only.


.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_mouse_charts_pan_poster.png" preload="none">
     <source src="_static/carta_gui_mouse_charts_pan.mp4" type="video/mp4">
   </video>

Resetting range
^^^^^^^^^^^^^^^
Double-clicking on the chart resets the plotting range.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_gui_mouse_charts_reset_poster.png" preload="none">
     <source src="_static/carta_gui_mouse_charts_reset.mp4" type="video/mp4">
   </video>


Controls and shortcuts
----------------------
CARTA supports keyboard shortcuts to enable certain actions without using a mouse. A summary is accessible via the menu "**Help**" -> "**Controls and Shortcuts**", or the shortcut "**shift**" + "**?**". The shortcuts are slightly different depending on the operating systems. The shortcuts for each operating system are summarized in the following table.


+----------------------------------+---------------------------------+---------------------------------+
| Control                          | macOS                           | Linux                           |
+==================================+=================================+=================================+
| **Help**                         |                                 |                                 |
+----------------------------------+---------------------------------+---------------------------------+
| Controls and shortcuts           | shift + ?                       | shift + ?                       |
+----------------------------------+---------------------------------+---------------------------------+
| **Navigation**                   |                                 |                                 | 
+----------------------------------+---------------------------------+---------------------------------+
| Pan image (two modes)            | drag-and-drop (default) / click | drag-and-drop (default) / click |
+----------------------------------+---------------------------------+---------------------------------+
| Pan image (inside region)        | cmd + click / middle-click      | ctrl + click / middle-click     |
+----------------------------------+---------------------------------+---------------------------------+
| Zoom image                       | mouse wheel                     | mouse wheel                     |
+----------------------------------+---------------------------------+---------------------------------+
| **Regions**                      |                                 |                                 |
+----------------------------------+---------------------------------+---------------------------------+
| Region properties                | double-click                    | double-click                    | 
+----------------------------------+---------------------------------+---------------------------------+
| Delete selected region           | del / backspace                 | del / backspace                 |
+----------------------------------+---------------------------------+---------------------------------+
| Toggle region creation mode      | C                               | C                               |
+----------------------------------+---------------------------------+---------------------------------+
| Deselect region                  | esc                             | esc                             |
+----------------------------------+---------------------------------+---------------------------------+
| Cancel region creation           | esc                             | esc                             |
+----------------------------------+---------------------------------+---------------------------------+
| Switch region creation mode      | cmd + drag-and-drop             | ctrl + drag-and-drop            |
+----------------------------------+---------------------------------+---------------------------------+
| Symmetric region creation        | shift + drag-and-drop           | shift + drag-and-drop           |
+----------------------------------+---------------------------------+---------------------------------+
| Toggle current region lock       | L                               | L                               |
+----------------------------------+---------------------------------+---------------------------------+
| Unlock all regions               | shift + L                       | shift + L                       |
+----------------------------------+---------------------------------+---------------------------------+
| **Appearance**                   |                                 |                                 |
+----------------------------------+---------------------------------+---------------------------------+
| Toggle light/dark theme          | shift + D                       | shift + D                       |
+----------------------------------+---------------------------------+---------------------------------+
| **Cursor**                       |                                 |                                 |
+----------------------------------+---------------------------------+---------------------------------+
| Freeze/unfreeze cursor           | F                               | F                               |
+----------------------------------+---------------------------------+---------------------------------+
| **File controls**                |                                 |                                 |
+----------------------------------+---------------------------------+---------------------------------+
| Open image                       | alt + O                         | alt + O                         |
+----------------------------------+---------------------------------+---------------------------------+
| Append image                     | alt + L                         | alt + L                         |
+----------------------------------+---------------------------------+---------------------------------+
| Close image                      | alt + W                         | alt + W                         |
+----------------------------------+---------------------------------+---------------------------------+
| Save image                       | alt + S                         | alt + S                         |
+----------------------------------+---------------------------------+---------------------------------+
| Export image                     | alt + E                         | alt + E                         |
+----------------------------------+---------------------------------+---------------------------------+
| Import catalog                   | alt + C                         | alt + C                         |
+----------------------------------+---------------------------------+---------------------------------+
| **Frame controls**               |                                 |                                 |
+----------------------------------+---------------------------------+---------------------------------+
| Next frame                       | alt + ]                         | alt + ]                         |
+----------------------------------+---------------------------------+---------------------------------+
| Previous frame                   | alt + [                         | alt + [                         |
+----------------------------------+---------------------------------+---------------------------------+
| Next channel                     | alt + up                        | alt + up                        |
+----------------------------------+---------------------------------+---------------------------------+
| Previous channel                 | alt + down                      | alt + down                      |
+----------------------------------+---------------------------------+---------------------------------+
| Next Stokes / polarization       | alt + shift + up                | alt + shift + up                |
+----------------------------------+---------------------------------+---------------------------------+
| Previous Stokes / polarization   | alt + shift + down              | alt + shift + down              |
+----------------------------------+---------------------------------+---------------------------------+
