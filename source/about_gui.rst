.. _about_gui:

Graphical user interface
========================
The CARTA graphical user interface (GUI) is designed to be flexible and user-friendly, supporting a variety of use cases such as continuum image analysis, spectral line cube analysis, polarization cube analysis, and catalog analysis. This section introduces the GUI and provides examples to familiarize you with layout configuration via mouse actions and how to interact with images, regions, and charts.


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
* Widget (docked)
* Widget (floating) 
* Tab
* Dialog

.. raw:: html

   <a href="_static/carta_gui.png" target="_blank">
       <img src="_static/carta_gui.png" 
           style="width:100%;height:auto;">
   </a>

The main browser window consists of a set of docked widgets. Multiple docked widgets can be stacked and share the same space. In this case, inactive widgets are displayed as tabs. For example, the above figure shows six docked widgets in the main browser window. Among them, two docked widgets share the same space as tabs in the bottom-left part of the GUI. A docked widget (i.e., a tab) may be detached to become a floating widget by clicking the "pin" button at the top-right corner of the widget. The GUI layout is highly configurable via mouse and is reusable. Please refer to the section :ref:`layoutConfiguration` for details.

The menu bar provides control options, such as image input/output, launching widgets, getting help, etc. The widget bar provides widgets to view or analyze images. The dialog bar provides dialogs for configurations. The region bar provides shortcut buttons for creating regions of interest or image annotation objects in the Image Viewer. 

The status bar includes indicators of the server (backend) status (as a green, orange, or red circle), data stream status (as a green cloud), new release notification (as an orange envelope), and share workspace button ("carta_controller" only). 

A widget provides a specific function to view or analyze image data, such as Image Viewer, Statistics, Spatial Profiler, etc. A toolbar provides tools for a widget, such as zoom buttons for the Image Viewer Widget or export options for the Spectral Profiler Widget. A dialog provides options for configurations, such as image view properties, region properties, contour properties, etc.


.. _quickstart:

Quick start
-----------
This section provides basic instructions on interacting with CARTA through the graphical user interface (GUI). A summary of the full set of controls and shortcuts can be found via the "**Help**" -> "**Controls and Shortcuts**" menu or via "**shift**"+"**?**" keys. 

Image view interactions
^^^^^^^^^^^^^^^^^^^^^^^
To zoom an image

* Use the mouse wheel to scroll
* Use the zoom buttons from the toolbar of the Image Viewer

To pan an image

* Use the mouse to drag-and-drop on the image (default) 
* Hold the “**command**” (macOS) / “**ctrl**” (Linux) key, then mouse click
* Mouse middle click

To pan from *inside* a region

* Hold the “**command**” (macOS) / “**ctrl**” (Linux) key, then mouse click
* Mouse middle click

Region of interest or image annotation object interactions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Regions of interest and image annotation objects share similar behaviors. In the following, we use "region" for short.

To enable region creation mode

* Press the “**C**” key
* Click the region creation button from the toolbar of the Image Viewer
* Click a target region type from the region bar 

To create a circle region via the ellipse region type or a square region via the rectangle region type

* Hold the “**shift**” key, then drag-and-drop

To create or modify a region (rectangle, ellipse, or line) with the alternative mode (center-to-corner v.s. corner-to-corner)

* Hold the “**command**” (macOS) / “**ctrl**” (Linux) key, then drag-and-drop

To configure a region

* Double-click on a region entry in the Region List Widget
* Double-click inside a region in the Image Viewer

To lock/unlock a region

* Press the "**L**" key
* Press the "**shift**" + "**L**" key to unlock all locked regions
* Click the lock button in the Region List Widget
* Click the lock button in the Region Configuration Dialog

To delete a region

* Press the “**delete**” key
* Press the “**backspace**” key
* Click the delete button in the Region Configuration Dialog

Cursor update
^^^^^^^^^^^^^
To freeze or unfreeze cursor position update in the Image Viewer

* Press the “**F**” key

To show/hide cursor marker rendering

* Press the “**G**” key

Chart interactions
^^^^^^^^^^^^^^^^^^
Focused zoom

* Use the mouse wheel to scroll

Horizontal zoom

* Drag-and-drop in the horizontal direction

Vertical zoom

* Drag-and-drop in the vertical direction

Box zoom

* Drag-and-drop in the diagonal direction

Reset zoom

* Double-click

Horizontal pan

* Hold the “**shift**” key, then drag-and-drop horizontally


.. _layoutConfiguration:

Configuring the layout
----------------------
Mouse actions, such as click or drag-and-drop can change the layout configuration. The drag-and-drop action is guided with a semi-transparent box. Various operations are described below. By mastering this section, you should be able to create, save, and restore custom layouts that fit your use cases.


.. _resizing_a_widget:

Resizing a widget
^^^^^^^^^^^^^^^^^
A widget can be resized by applying drag-and-drop action to its borders. After a panel is resized, adjacent panels are resized automatically to fit the new layout. The image size on the screen and the aspect ratio will be displayed for the Image Viewer after the widget size is changed.


.. raw:: html

   <a href="_static/carta_gui_resizing_panel.png" target="_blank">
       <img src="_static/carta_gui_resizing_panel.png" 
          style="width:100%;height:auto;">
   </a>


Relocating a tab as a new docked widget
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A tab (docked widget) can be detached and relocated by dragging its title to a desired location as a docked widget. The target location is visualized with a semi-transparent box, as shown in the example below.


.. raw:: html

   <a href="_static/carta_gui_relocating_tab_as_panel.png" target="_blank">
       <img src="_static/carta_gui_relocating_tab_as_panel.png" 
           style="width:100%;height:auto;">
   </a>

Relocating a tab to share space with other docked widget
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A tab (docked widget) can be moved to another existing docked widget to share space by dragging its title to the upper border of the target location, as shown in the example below.


.. raw:: html

   <a href="_static/carta_gui_relocating_tab_as_tab.png" target="_blank">
       <img src="_static/carta_gui_relocating_tab_as_tab.png" 
           style="width:100%;height:auto;">
   </a>


Maximizing and restoring a widget
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
By clicking the "**maximize**" button at the top-right corner of a docked widget, the widget (including all the other stacked widgets) will be maximized to the main browser window. 

.. raw:: html

   <a href="_static/carta_gui_max_panel.png" target="_blank">
       <img src="_static/carta_gui_max_panel.png" 
           style="width:100%;height:auto;">   
   </a>


By clicking the "**restore**" button, the widget (and the other stacked widgets) will be restored to its original location.

.. raw:: html

   <a href="_static/carta_gui_min_panel.png" target="_blank">
       <img src="_static/carta_gui_min_panel.png" 
           style="width:100%;height:auto;">   
   </a>



Detaching and attaching a widget
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The active tab can be detached as a floating widget by clicking the "**detach**" (unpin) button at the top-right corner of a docked widget.


.. raw:: html

  <a href="_static/carta_gui_detach_panel.png" target="_blank">
       <img src="_static/carta_gui_detach_panel.png" 
           style="width:100%;height:auto;">   
   </a>

By dragging the “attach” (pin) button, a floating widget can be stacked with an existing docked widget or positioned as a docked widget.

.. raw:: html

   <a href="_static/carta_gui_attach_panel.png" target="_blank">
       <img src="_static/carta_gui_attach_panel.png" 
           style="width:100%;height:auto;">   
   </a>


Creating a widget as a floating widget or as a docked widget
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A widget can be activated as a floating widget by clicking the desired widget button from the widget bar. Alternatively, a widget can be activated as a docked widget by dragging the desired widget button from the widget bar directly to a desired location.


.. raw:: html

   <a href="_static/carta_gui_activating_widget.png" target="_blank">
       <img src="_static/carta_gui_activating_widget.png" 
           style="width:100%;height:auto;">   
   </a>


Light and dark themes
^^^^^^^^^^^^^^^^^^^^^
CARTA supports light and dark themes. The default theme is determined automatically from the operating system (if applicable). The theme can be changed using the menu "**View**" -> "**Theme**", or the shortcut "**shift**" + "**D**".

.. raw:: html

   <a href="_static/carta_gui_theme.png" target="_blank">
       <img src="_static/carta_gui_theme.png" 
           style="width:100%;height:auto;">   
   </a>


Custom layout, save, and restore
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
CARTA has a set of preset layouts designed for different kinds of image analysis. These layouts are accessible via the menu "**View**" -> "**Layouts**" -> "**Existing Layouts**". 

You may customize a preset layout for a different purpose and save it for the future. To save a custom layout, use the menu "**View**" -> "**Layouts**" -> "**Save Layout**". A name is required when saving a layout. 

A saved layout can be restored via the menu "**View**" -> "**Layouts**" -> "**Existing Layouts**". The active layout is highlighted in blue ("my layout 01" in the following example). Saved layouts can be removed via the menu "**View**" -> "**Layouts**" -> "**Delete Layout**" or renamed via the menu "**View**" -> "**Layouts**" -> "**Rename Layout**".


.. raw:: html

   <a href="_static/carta_gui_custom_layout.png" target="_blank">
       <img src="_static/carta_gui_custom_layout.png" 
           style="width:100%;height:auto;">   
   </a>


By default, CARTA will load the preset layout named “Default” when initialized. Which layout, including user-customized layouts, should be loaded can be further defined via the Preferences Dialog ("**File**" -> "**Preferences**"). The initial layout can be set via the "**Initial layout**" dropdown menu of the "**Global**" tab.


.. raw:: html

   <a href="_static/carta_gui_layout_preference.png" target="_blank">
       <img src="_static/carta_gui_layout_preference.png" 
           style="width:90%;height:auto;">   
   </a>


.. note::
  
  The layout files are kept in :code:`<your home>/.carta/config/layouts` folder in the JSON format. When you install CARTA on a new computer, you may copy the layout files from the old computer to migrate the custom layouts.


User preferences
----------------
CARTA provides several preferences for you to customize the graphical user interface (GUI), including layouts. All the preferences and layout will be restored when you launch CARTA next time. The Preferences Dialog is accessible via the menu "**File**" -> "**Preferences**". Note that some preferences are effective immediately without needing a full reload. Below, we summarize the options of all preferences.  

.. note::
  
  As a JSON file, the preferences file is kept in :code:`<your home>/.carta/config/preferences.json`. When you install CARTA on a new computer, you may copy the preferences file from the old computer to migrate the custom preferences.


* Global

  * **Theme**: To switch between the light or dark theme for the graphical user interface. (default: automatic) [effective immediately]
  * **Enable code snippets**: To enable the *experimental* feature of the in-app `JavaScript scripting interface <https://cartavis.org/carta-frontend/docs/category/code-snippet-tutorial>`_  (default: disabled) [effective immediately]
  * **Auto-launch file browser**: Should the File Browser be launched upon initializing CARTA? (default: yes)
  * **File list**: Options on how a file list is generated. If there are usually lots of files in your folders, you can switch to the "filter by extension" mode or "all files" mode to boost performance. (default: filter by file content) [effective immediately]
  * **Initial layout**: The layout that should be restored upon CARTA initialization. (default: "Default")
  * **Initial cursor position**: When CARTA is initialized, the cursor position on the image can be fixed to show a cross at the image center. Press the "**F**" key to switch back to tracking mode. (default: Tracking).
  * **Initial zoom level**: Select the initial zoom level of a newly loaded image to either fit the Image Viewer or display at a 1:1 image-to-screen pixel ratio. (default: "Zoom to fit") [effective immediately]
  * **Zoom to**: Zoom in/out relative to the cursor position (also known as focused zoom) or the center of the Image Viewer. [effective immediately]
  * **Enable drag-to-pan**: Pan image by mouse dragging or clicking. [effective immediately]
  * **WCS matching on append**: Automatically activate WCS matching for newly added images. [effective immediately]
  * **Spectral matching**: Spectral convention adopted for spectral matching [effective immediately]
  * **Transparent image background**: Set the background of the exported PNG file as transparent (default: white or black depending on the GUI theme) [effective immediately]
  * **Save last used directory**: To set the initial directory path for CARTA to the last loaded image.

  .. raw:: html

    <a href="_static/carta_gui_preferences_global.png" target="_blank">
        <img src="_static/carta_gui_preferences_global.png" 
            style="width:100%;height:auto;">   
    </a>

* Render Configuration

  * **Default scaling**: The scaling function of the colormap (default: linear) [effective to new images]
  * **Default colormap**: The default colormap for the raster image (default: inferno) [effective to new images]
  * **Default percentile ranks**: The default clip level for the colormap (default: 99.9%) [effective to new images]
  * **NaN color**: The color for rendering NaN pixels [effective immediately]
  * **Smoothed bias/contrast**: Apply smoothed bias and contrast transfer functions to the selected scaling function (default: enabled) [effective immediately]
  
  .. raw:: html

    <a href="_static/carta_gui_preferences_renderConfig.png" target="_blank">
        <img src="_static/carta_gui_preferences_renderConfig.png" 
            style="width:100%;height:auto;">   
    </a>



* Contour Configuration

  * **Generator type**: Builtin functions for generating a set of contour levels to be calculated and rendered (default: start-step-multiplier)
  * **Smoothing mode**: The image smoothing mode before calculating contour vertices (default: Gaussian)
  * **Default smoothing factor**: The kernel size in the number of pixels for image smoothing (default: 4)
  * **Default contour levels**: The number of contour levels to be generated with the level generator (default: 5)
  * **Thickness**: The line thickness of contour rendering (default: 1)
  * **Default color mode**: To render contours with a constant color or a color map (default: constant color)
  * **Default colormap**: The colormap for contour rendering when the color mode is "color-mapped" .
  * **Default color**: The constant color for contour rendering when the color mode is "constant color".

  .. raw:: html

    <a href="_static/carta_gui_preferences_contourConfig.png" target="_blank">
        <img src="_static/carta_gui_preferences_contourConfig.png" 
            style="width:100%;height:auto;">   
    </a>



* Vector Overlay Configuration

  * **Default pixel averaging**: The block averaging factor before computing the vector overlay data (default: 4x4 pixels)
  * **Use fractional intensity**: To compute fractional polarization intensity if it is possible (default: false)
  * **Thickness**: The line width to render the vector overlay (default: 1)
  * **Default color mode**: To render vector overlay with a constant color or a color map (default: constant color)
  * **Default colormap**: The colormap for vector overlay rendering when the color mode is "color-mapped" 
  * **Default color**: The constant color for vector overlay rendering when the color mode is "constant color"

  .. raw:: html

    <a href="_static/carta_gui_preferences_vectorOverlayConfig.png" target="_blank">
        <img src="_static/carta_gui_preferences_vectorOverlayConfig.png" 
            style="width:100%;height:auto;">   
    </a>


* WCS and Image Overlay

  * **Color**: The color for the WCS overlay, including border, grid line, ticks, labels, and title [effective to new images]
  * **WCS grid visible**: To show grid line or not as default (default: yes) [effective to new images]
  * **Label visible**: To show coordinate labels or not as default (default: yes) [effective to new images]
  * **Cursor info visible**: The mode to show the cursor info bar in the Image Viewer (default: active image only) [effective immediately]
  * **WCS format**: The format of the displayed world coordinate. The default is "automatic", meaning for GALACTIC or ECLIPTIC systems, the world coordinate is displayed in decimal degrees, and for FK4, FK5, or ICRS, the world coordinate is displayed in sexigesimal format. (default: automatic) [effective to new images]
  * **Colorbar visible**: To show a colorbar in the Image Viewer (default: yes) [effective to new images]
  * **Colorbar interactive**: When this is activated, if you hover over the colorbar, a dynamic color clip is applied to the raster image immediately to assist you in exploring image features (default: activated) [effective to new images]
  * **Colorbar position**: The position where the colorbar should be rendered in the Image Viewer (default: right) [effective to new images]
  * **Colorbar width (px)**: The width of the colorbar (default: 15) [effective to new images]
  * **Colorbar ticks density (per 100px)**: The density of the computed ticks per 100 screen pixels (default: 1) [effective to new images]
  * **Colorbar label visible**: To show a colorbar label (default: no) [effective to new images]
  * **Beam visible**: To show a spatial resolution element (default: yes) [effective to new images]
  * **Beam color**: The color for rendering a spatial resolution element [effective to new images]
  * **Beam type**: The styling for rendering a spatial resolution element (default: open) [effective to new images]
  * **Beam width (px)**: The line width for rendering a spatial resolution element (default: 1) [effective to new images]

  .. raw:: html

    <a href="_static/carta_gui_preferences_WCSImageOverlayConfig.png" target="_blank">
        <img src="_static/carta_gui_preferences_WCSImageOverlayConfig.png" 
            style="width:100%;height:auto;">   
    </a>


* Catalog        

  * **Displayed columns**: Displaying only the first N columns of a catalog as default [effective to new catalogs]

  .. raw:: html

    <a href="_static/carta_gui_preferences_catalog.png" target="_blank">
        <img src="_static/carta_gui_preferences_catalog.png" 
            style="width:100%;height:auto;">   
    </a>

* Region

  * **Color**: The default color of a region [effective to new regions]
  * **Line width (px)**: The default line width of a region (default: 2) [effective to new regions]
  * **Dash length (px)**: The default dash length of the line composing a region. The default is to show a region in a solid line (default: 0) [effective to new regions]
  * **Region type**: The default selected region in the toolbar of the Image Viewer (default: rectangle) [effective to new images]
  * **Region size**: The default region (screen) size when created by a single click (rectangle, ellipse, and line) [effective to new regions]
  * **Creation mode**: The rectangle or ellipse can be created by dragging the mouse in two ways: center-to-corner or corner-to-corner. (default: center-to-corner) [effective to new regions]

  .. raw:: html

    <a href="_static/carta_gui_preferences_region.png" target="_blank">
        <img src="_static/carta_gui_preferences_region.png" 
            style="width:100%;height:auto;">   
    </a>

* Annotation

  * **Color**: The default color of an annotation object [effective to new annotation objects]
  * **Line width (px)**: The default line width of an annotation object (default: 2) [effective to new annotation objects]
  * **Dash length (px)**: The default dash length of the line composing an annotation object. The default is a solid line (default: 0) [effective to new annotation objects]
  * **Point shape**: The default selected point shape in the toolbar of the Image Viewer (default: filled square) [effective to new annotation objects]
  * **Point size (px)**: The default annotation object (screen) size when created by a single click (default: 6) [effective to new annotation objects]
  
  .. raw:: html

    <a href="_static/carta_gui_preferences_annotation.png" target="_blank">
        <img src="_static/carta_gui_preferences_annotation.png" 
            style="width:100%;height:auto;">   
    </a>


* Performance

  * **Low bandwidth mode**: To reduce required image resolution by a factor of two and reduce the cursor responsiveness to 400 ms [effective immediately]
  * **Limit overlay redraw**: To throttle the WCS grid rendering (default: yes) [effective immediately]
  * **Compression quality (image)**: You can adjust the image quality through lossy compression with a parameter range of 1 to 32. The higher the number is, the better quality the images are. Choose with caution. (default: 11) [effective immediately]
  * **Compression quality (animation)**: You can adjust the animation quality through lossy compression with a parameter range of 1 to 32. The higher the number is, the better the quality of the animation playback is. Choose with caution. (default: 9) [effective immediately]
  * **GPU tile cache size (number of tiles)**: The cache size of GPU for tiles (default: 512)
  * **System tile cache size (number of tiles)**: The cache size of system memory for tiles (default: 4096)
  * **Contour rounding factor**: The number of contour vertices per pixel
  * **Contour compression level**: The compression quality of contour image data
  * **Contour chunk size**: The chunk size of contour data streaming
  * **Contour control map resolution**: The control map resolution for reprojecting contour vertices to other coordinate systems.
  * **Stream image tiles while zooming**: To stream image tiles for all throttled image zoom levels.
  * **Stop animation playback in**: A timer to stop animation playback for server resource management.
  * **PV preview cube size limit**: The upper limit of the memory cache to perform PV image preview (default: 1 GB)

  .. raw:: html

    <a href="_static/carta_gui_preferences_performance.png" target="_blank">
        <img src="_static/carta_gui_preferences_performance.png" 
            style="width:100%;height:auto;">   
    </a>


* Telemetry
  
  * **Telemetry mode**: The mode for sending anonymous usage data to the CARTA development team for development and planning purposes 
  * **Log telemetry output**: To show telemetry log in the browser debug console (default: off)

  .. raw:: html

    <a href="_static/carta_gui_preferences_telemetry.png" target="_blank">
        <img src="_static/carta_gui_preferences_telemetry.png" 
            style="width:100%;height:auto;">   
    </a>


* Compatibility

  * **AIPS cube beam support**: To derive the beam information from the HISTORY entries of an AIPS cube. (default: disabled)

  .. raw:: html

    <a href="_static/carta_gui_preferences_compatibility.png" target="_blank">
        <img src="_static/carta_gui_preferences_compatibility.png" 
            style="width:100%;height:auto;">   
    </a>


* Log Events

  This is for debugging purposes. General users can skip this part. CARTA's client-side and server-side communicate through "protocol buffer" messages. For debugging purposes, advanced users can identify a set of messages in the list and launch the browser console to see those message flows.

  .. raw:: html

    <a href="_static/carta_gui_preferences_log.png" target="_blank">
        <img src="_static/carta_gui_preferences_log.png" 
            style="width:100%;height:auto;">   
    </a>



.. _mouse_interaction_with_images:

Mouse interactions with images
------------------------------

Zooming an image
^^^^^^^^^^^^^^^^
The image can be zoomed in by scrolling up and out by scrolling down.


.. raw:: html

   <a href="_static/carta_gui_mouse_images_zoom.png" target="_blank">
       <img src="_static/carta_gui_mouse_images_zoom.png" 
           style="width:100%;height:auto;">   
   </a>



Panning an image
^^^^^^^^^^^^^^^^
The image can be panned by mouse drag-and-drop on the image. Alternatively, the image can be re-positioned by mouse middle-click or by holding the "**command/ctrl**" (macOS) key or "**ctrl**" (Linux) key with a click.

.. raw:: html

   <a href="_static/carta_gui_mouse_images_pan.png" target="_blank">
       <img src="_static/carta_gui_mouse_images_pan.png" 
           style="width:100%;height:auto;">   
   </a>



If you want to pan inside a region, hold the "**command/ctrl**" key (macOS) or "**ctrl**" key (Linux) while clicking inside the region. Alternatively, you can use middle-click. Single-clicking on a region will change the region state to "active".


.. raw:: html

   <a href="_static/carta_gui_mouse_images_pan_roi.png" target="_blank">
       <img src="_static/carta_gui_mouse_images_pan_roi.png" 
           style="width:100%;height:auto;">   
   </a>



.. _mouse_interaction_with_regions:

Mouse interactions with region of interest
------------------------------------------
Regions of interest and annotation objects share similar behaviors. In the following, we use "region" for short.


Region creation
^^^^^^^^^^^^^^^
A region can be created by entering the region creation mode and then applying drag-and-drop action in the Image Viewer. To enter the region creation mode, click the "**region**" button in the bottom-right corner of the Image Viewer or press the "**C**" key. Double-clicking the region icon brings up all available region types (rectangle, ellipse, polygon, point, line, and polyline). Alternatively, you may click the buttons in the region bar at the top of the GUI to enter the region creation mode.

To create a point region, a single click will do. The rectangle region, the ellipse region, or the line region can be created in the "center-to-corner" mode or the "corner-to-corner" mode, depending on the preferences setting in the Preferences Dialog ("**File**" -> "**Preferences** -> "**Region**"). To temporarily switch to the other mode, hold the "**command**" (macOS) or "**ctrl**" (Linux) key then drag-and-drop. The "circle" and the "square" regions are the special cases of the ellipse region and the rectangle region, respectively. These symmetric regions can be created by holding the "**shift**" key followed by the drag-and-drop action. Alternatively, a single mouse click can create a rectangle region, an ellipse region, or a line region. The default size on the screen is defined in the Preferences Dialog ("**File**" -> "**Preferences**" -> "**Region**").

.. raw:: html

   <a href="_static/carta_fn_roi_creation1.png" target="_blank">
       <img src="_static/carta_fn_roi_creation1.png" 
           style="width:100%;height:auto;">   
   </a>



To create a polygon region or a polyline region, start with a click followed by a series of clicks to define the control points of a desired shape and finish with a double click. CARTA detects a "complex" polygon (polygon with intersections) and shows it in pink. Spectral profiles, statistics, or histograms of a complex polygon can still be requested. However, please note that the results may be beyond your expectations since the actual pixel coverage depends on *how* a complex polygon is created. 

.. raw:: html

   <a href="_static/carta_fn_roi_creation2.png" target="_blank">
       <img src="_static/carta_fn_roi_creation2.png" 
           style="width:100%;height:auto;">   
   </a>


Region selection and modification
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Click on a region in the Image Viewer will change the region state to "active". The active region will be highlighted in the Region List Widget. Alternatively, a region can be selected by clicking a region entry in the Region List Widget. CARTA allows selecting a "region in region". The layer order of regions is adjusted automatically based on the region size. To deselect a region, click elsewhere in the Image Viewer or press the "**esc**" key.


.. raw:: html

   <a href="_static/carta_roi_selection.png" target="_blank">
       <img src="_static/carta_roi_selection.png" 
           style="width:100%;height:auto;">   
   </a>


Double-click on a region in the Image Viewer or a region in the Region List Widget will launch the Region Configuration Dialog. You can make changes to the region's name, location, shape, and style using the dialog. Pressing the "**delete**" or the "**backspace**" key will remove the active region. 


.. raw:: html

   <a href="_static/carta_roi_modification.png" target="_blank">
       <img src="_static/carta_roi_modification.png" 
           style="width:100%;height:auto;">   
   </a>



.. tip::
  "**backspace**" does not delete a region...

  When you launch CARTA with the Firefox web browser on macOS, you may find the "**backspace**" key navigates back a page instead of removing a region. This behavior can be prevented by modifying your Firefox web browser settings:

  1. Enter about:config in the address bar.
  2. Click "I accept the risk!"
  3. A search bar appears at the top of a long list of preferences. Search for "browser.backspace_action"
  4. It will likely have a value of 0. Double-click it, and then modify it to a value of "2".
  5. Close the about:config tab, and now backspace will no longer navigate back a page.


A new control point can be added by clicking on a line segment for a polygon or polyline region. A control point can be deleted by double-clicking on the control point.

.. raw:: html

   <a href="_static/carta_fn_roi_creation3.png" target="_blank">
       <img src="_static/carta_fn_roi_creation3.png" 
           style="width:100%;height:auto;">   
   </a>


.. _mouse_interaction_with_charts:

Mouse interactions with charts
------------------------------

Zooming a chart
^^^^^^^^^^^^^^^
A chart (profiles and histograms) can be zoomed in by scrolling up and zoomed out by scrolling down. Alternatively, horizontal zoom, vertical zoom, and box zoom are supported by drag-and-drop actions.

.. raw:: html

   <a href="_static/carta_gui_mouse_charts_zoom.png" target="_blank">
       <img src="_static/carta_gui_mouse_charts_zoom.png" 
           style="width:100%;height:auto;">   
   </a>

Panning a chart
^^^^^^^^^^^^^^^
A chart can be panned by holding the "**shift**" key and then applying drag-and-drop action. Panning in the x direction is supported only.


.. raw:: html

   <a href="_static/carta_gui_mouse_charts_pan.png" target="_blank">
       <img src="_static/carta_gui_mouse_charts_pan.png" 
           style="width:100%;height:auto;">   
   </a>


Resetting range
^^^^^^^^^^^^^^^
Double-clicking on the chart resets the plotting range.

.. raw:: html

   <a href="_static/carta_gui_mouse_charts_reset.png" target="_blank">
       <img src="_static/carta_gui_mouse_charts_reset.png" 
           style="width:100%;height:auto;">   
   </a>



Getting help
------------
The online user manual (the one you are reading!) can be accessed via the menu "**Help**" -> "**Online Manual**". A new browser window will be launched to show this CARTA user manual. 


.. raw:: html

   <a href="_static/carta_gui_onlinehelp.png" target="_blank">
       <img src="_static/carta_gui_onlinehelp.png" 
           style="width:100%;height:auto;">   
   </a>


In addition, an in-app help manual (no internet is required) can be accessed via the "?" button at the top-right corner of a widget or a dialog. The help content will be displayed in a drawer.

.. raw:: html

   <a href="_static/carta_gui_inapphelp.png" target="_blank">
       <img src="_static/carta_gui_inapphelp.png" 
           style="width:100%;height:auto;">   
   </a>


Controls and shortcuts
----------------------
CARTA supports keyboard shortcuts to enable specific actions without using a mouse. A summary is accessible via the menu "**Help**" -> "**Controls and Shortcuts**", or the shortcut "**shift**" + "**?**". The shortcuts are slightly different depending on the operating system. The table below summarizes the shortcuts for each operating system.


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
| Mirror cursor on multipanel view | G                               | G                               |
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
