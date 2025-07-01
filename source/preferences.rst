Preferences
===========

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

