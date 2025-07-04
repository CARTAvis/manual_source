Image viewer
============
.. note::
   | To know more about raster rendering, see :ref:`raster_rendering`.
   | To know more about contour rendering, see :ref:`contour_rendering`.
   | To know more about vector field rendering (e.g., polarization), see :ref:`vector_rendering`.
   | To know more about mult-color blending, see :ref:`multicolor_blending`.
   | To know more about channel map view, see :ref:`channel_map_view`.


.. note::
    If you run a VNC session from a headless server, CARTA may fail to render images correctly (they may appear as a block with a uniform color or as an empty plot). It is because CARTA renders images using WebGL2, which uses GPU to accelerate the rendering process. Most headless servers have neither discrete nor integrated GPUs. In such cases, it is highly recommended to use your *local* web browser to access the backend, as it is much more efficient than VNC. Please refer to the section :ref:`how_to_run_carta`.

Rendering modes
---------------

The Image Viewer Widget is the main widget in CARTA providing the capability to view image data in various ways (note that this widget is a special widget that cannot be undocked, nor closed). For example, it can display image data as a raster image or as a contour image, or a combination of both like the folllowing examples:

1. a single raster image
2. a single raster image plus its contours
3. a single raster image plus a set of contour images with matched world coordinates from other image files 
4. a set of contour images without a background raster image

.. raw:: html

   <img src="_static/carta_fn_imageViewer_examples.png" 
        style="width:100%;height:auto;">

By default, CARTA displays images as raster images when they are loaded, like the first example in the figure above. Then you can generate contour images (see :ref:`contour_rendering`) and enable WCS matching between different images (see :ref:`wcs_matching`), such as the other three examples above.

In addition, a vector overlay from a vector field (e.g., a linear polarization field or a magnetic field, etc.) or a scalar field (e.g., a temperature field or a column density field, etc.) can be added to the image view (see :ref:`vector_rendering`).

.. raw:: html

   <img src="_static/carta_fn_imageViewer_examples2.png" 
        style="width:100%;height:auto;">

CARTA also provides a multi-color blending mode to combine multiple images into one raster image in the color space. This mode is useful for visualizing multi-wavelength images, such as optical, infrared, and radio images, in a single view. See :ref:`multicolor_blending` for more information.

.. raw:: html

   <img src="_static/carta_fn_imageViewer_examples3.png" 
        style="width:100%;height:auto;">



Changing image field of view
----------------------------

You can configure the field of view of the image in the Image Viewer by using mouse actions. If precise control of the position and zoom level of the image is needed, you can use the "**Pan and Zoom**" tab of the Image Viewer Settings Dialog for the purpose. The same dialog can be enabled by double-clicking the "pan" button in the toolbar of the Image Viewer.

.. raw:: html

   <img src="_static/carta_fn_changeFOV.png" 
      style="width:100%;height:auto;">

The widget geometry determines the aspect ratio of the image view. When the Image Viewer Widget is resized, a tooltip with a ratio in screen pixels will be displayed (c.f., :ref:`resizing_a_widget` ).


Changing channel and polarization
---------------------------------

Paired with the Image Viewer Widget, the Animator Widget provides a set of sliders to change the active image from the loaded images, as well as the channel and polarization (if applicable) of the active image cube. The Animator Widget is located at the bottom-right corner of the Image Viewer Widget by default.


.. raw:: html

   <img src="_static/carta_fn_imageViewer_animator.png" 
      style="width:100%;height:auto;">


Single-panel view and multi-panel view
--------------------------------------
The Image Viewer provides two modes for viewing images: single-panel and multi-panel views. By default, a *dynamic* multi-panel view mode is enabled. You can use the "**viewer mode**" button at the Image Viewer Widget's top-right corner to switch between the two modes. The view mode is persistent in a new CARTA session (i.e., it is an implicit preference). Additional view mode configuration options are available in the settings dialog of the Image Viewer Widget. You can have a dynamic multi-panel view layout (with a configurable maximum n rows by m columns) based on the number of loaded images or have a fixed layout regardless of how many images are loaded. You can use the "**next page**" and "**previous page**" buttons at the top-right corner of the Image Viewer to view images if the current grid layout cannot show all loaded images at once.  

.. raw:: html

   <img src="_static/carta_fn_imageViewer_panelMode.png" 
        style="width:100%;height:auto;">

When the view mode is single-panel, the image in the view is the "active" image. The “active” image is highlighted with a red box when the view mode is multi-panel. In the above example, the image on the left-hand side is the "active" image. In the Image List Widget (the widget at the bottom-left corner in the above example), the "active" image is highlighted in boldface. There is always an "active" image, except when no image is loaded in CARTA. You can use the Animator Widget or the Image List Widget to select a new "active" image. 

In analytics widgets, such as the Statistics Widget or the Spectral Profiler Widget, the "**Image**" dropdown menu contains a list of loaded images, as well as an option as "Active" (default), which refers to the "active" image in the Image Viewer. This feature allows you to view the "active" image's analytics efficiently without needing extra configurations in all analytics widgets. If you use the "**Image**" dropdown menu to select an image other than "Active", the analytics widgets will stop updating if you set a new "active" image. For example, you can enable two Statistics Widgets and use the "**Image**" dropdown menu to configure the widgets to show the statistics from two images, respectively.


.. tip::
   When comparing images side-by-side in the multi-panel mode, you can render mirrored cursor positions at different panels by clicking the "G" key.

   .. raw:: html

      <img src="_static/carta_fn_imageViewer_mirrorCursor.png" 
           style="width:100%;height:auto;">


When multiple images are loaded in the append mode, their loading order determines the order in the image slider of the Animator Widget and the rendering order in the multi-panel view (left-right, then top-down). You can change the order by dragging an entry to a desired place in the Image List Widget.

.. raw:: html

   <img src="_static/carta_fn_reorderFrame.png" 
      style="width:100%;height:auto;">


Channel map view
----------------

The channel map view is a special view mode of the Image Viewer that displays an image cube in a 2D grid layout. Each cell in the grid represents a channel of the image cube, and the cells are arranged in a way that reflects the spectral order of the channels. The channel map view can be enabled by clicking the "**Channel Map**" button at the top-right corner of the Image Viewer Widget. See :ref:`channel_map_view` for detailed configuration options in the Channel Map Control Widget.

.. raw:: html

   <img src="_static/carta_fn_imageViewer_channelMap.png" 
        style="width:100%;height:auto;">

.. note::
   With v5.0 release, the channel map view mode only supports raster rendering. Contour images and vector field overlay are not supported in the channel map view mode.


Coordinate system
-----------------

Once an image is rendered in the Image Viewer, a grid layer representing the the coordinate system of the image is displayed on top of the image. The coordinate system can be changed by clicking the "**WCS**" button in the toolbar of the Image Viewer Widget. The available coordinate systems include:

* ICRS (International Celestial Reference System)
* FK5 (Fifth Fundamental Catalog)
* FK4 (Fourth Fundamental Catalog)
* GALACTIC (GAL; Galactic coordinate system)
* ECLIPTIC (ECL; Ecliptic coordinate system)
* ICRS (International Celestial Reference System)
* IMG (Image coordinate system)

By default, the displayed coordinate system is the one defined in the image header. If the image header does not provide a valid world coordinate system, the image coordinate system is used by default. You can change the coordinate system by selecting a different one from the "**WCS**" menu. Optionally you can enable the grid line by clicking the "**Grid**" button in the toolbar of the Image Viewer Widget. 

All the supported coordinate systems also have an addtional "offset" mode with a flexible origin of the offset reference. By clicking the re-center button from the "**WCS**" menu, a new origin is defined at the center of the image view. For detailed offset mode configuration options, see the "Pan and Zoom" tab in the Image Viewer Settings Dialog. 

In the example below, the left panel is the FK5 coordinate system with the grid line enabled, the center panel is the same coordinate system in the offset mode with a custom origin, and the right panel is the image coordinate system in the offset mode with a custom origin.

.. raw:: html

   <img src="_static/carta_fn_imageViewer_wcs.png" 
        style="width:100%;height:auto;">


Cursor information
------------------

In addition to displaying images, the Image Viewer displays cursor information at the top and provides a set of tool buttons in the bottom-right corner when you use the mouse to hover over the image. 

.. raw:: html

   <img src="_static/carta_fn_imageViewer_intro.png" 
        style="width:100%;height:auto;">

When the cursor is movning on the Image Viewer, the pixel information at the cursor position is shown at the top side of the image. The information includes:

* World coordinate of the current coordinate system. 
* Image coordinate in pixel (0-based).
* Pixel value.
* Frequency, velocity, reference frame (if applicable), and polarization parameter (if applicable).


.. raw:: html

   <img src="_static/carta_fn_imageViewer_cursorInfo.png" 
        style="width:100%;height:auto;">

When the coordinate system changes (e.g., ICRS to GALACTIC), the displayed world coordinate will be changed accordingly. By default, they are displayed in decimal degrees for GALACTIC and ECLIPTIC systems, while for FK5, FK4, and ICRS systems, they are displayed in sexagesimal format. The precision of both formats is determined dynamically based on the image header and the image zoom level. 

The reference image coordinate (0, 0) is located at the center of the bottom-left pixel of the image. Whether the displayed image is downsampled, the image coordinate always refers to the full-resolution image.

When the cursor is moving, a pixel value of the full-resolution image is displayed. If the image header provides sufficient information in the frequency/velocity domain, a frequency and a velocity with the reference frame of the current channel will be shown. A polarization parameter (e.g., Stokes I) will also be displayed if the polarization information is available in the image header.

To stop/resume cursor update, press the "**F**" key. When the cursor stops updating, the cursor information bar, cursor spatial profile, and cursor spectral profile will stop updating, too.

.. tip::

   A cursor info bar is displayed at the top of the active image plot by default in the Image Viewer. When it is the single-panel view mode, the image in the current view is the active image. When it is the multi-panel view mode, the active image is highlighted with a red box. With the "**File**" -> "**Preferences**" -> "**WCS and image overlay**" -> "**Cursor Info Visible**" dropdown menu, you can switch to a different mode. Available modes are

   * Always: Always show the cursor info bar per image
   * Active image only: Only show the cursor info bar on the active image (default)
   * Hide when tiled: Do not show the cursor info bar when it is in the multi-panel view mode.
   * Never: Do not show the cursor info bar regardless of whether it is the single-panel view mode or the multi-panel view mode.



Colorbar
--------

By default, a colorbar is displayed along with the raster image on the right-hand side. You can configure its properties in the settings dialog (the "**cog**" button at the top-right corner) of the Image Viewer Widget. In "**File**" -> "**Preferences**" -> "**WCS and Image Overlay**", you can set colorbar properties persistent for new images, such as the orientation of the colorbar, for example. When you use the mouse to hover over the colorbar, a color-scale value is displayed at the bottom of the colorbar, and a real-time color clip of the color-scale value is applied to the Image Viewer to assist you in investigating features in the image. The pixels less than the color-scale are rendered in grayscale temporarily. This interactive feature can be disabled in "**File**" -> "**Preferences**" -> "**WCS and Image Overlay**".


.. raw:: html

   <img src="_static/carta_fn_imageViewer_colorbar.png" 
        style="width:100%;height:auto;">






Toolbar
-------

The toolbar of the Image Viewer Widget is located at the bottom-right corner of the Image Viewer when you use mouse to hover over the image. It provides a set of tool buttons to assist you in interacting with the image. The tools allow you to

* measure an angular distance
* select a source from the catalog overlay (if applicable)
* create a region of interest or an annotation object
* perform zoom actions
* enter pan mode
* trigger matching images in world coordinates and/or in the spectral domain
* change reference coordinate grid lines and labels
* export image as a PNG file
* hide/show the toolbar

.. raw:: html

   <img src="_static/carta_fn_imageViewer_toolButtons.png" 
        style="width:70%;height:auto;">


Settings
--------

CARTA provides flexible options to configure the appearance of an image plot as well as the image layout. The Image Viewer Settings Dialog is accessible by clicking the "**cog**" at the top-right corner of the Image Viewer Widget.

The settings dialog has several tabs, including:

* **Pan and Zoom**: You can have fine control of the center and field of view of the displayed image as well as a custom offset origin for the coordinate system.
* **Global**: You can set the layout for the multi-panel mode, the overall overlay color theme, the cooridnate grid rendering accuracy (tolerance), labelling location, and the coordinate system for the image overlay.
* **Title**: You can set the title of the image plot, including styling.
* **Ticks**: You can set the tick density and styling.
* **Grids**: You can set the syling of the world coordinate grid lines and pixel coordinate grid lines.
* **Border**: You can set the styling of the axis border.
* **Axes**: You can set the styling of the axis when the labelling location is set to "interior".
* **Numbers**: You can set the styling of the tick values, their formatting, and precision.
* **Labels**: You can set the axis labels, including styling.
* **Colorbar**: You can set the styling of the colorbar.
* **Beam**: You can set the styling of the restoring beam.
* **Conversion**: You can apply a spectral conversion if the active image is a spatial-spectral image such as a position-velocity image. 

The following screenshots highlight these options.

.. raw:: html

   <img src="_static/carta_fn_imageViewer_settingsDialog1.png" 
        style="width:100%;height:auto;">

.. raw:: html

   <img src="_static/carta_fn_imageViewer_settingsDialog2.png" 
        style="width:100%;height:auto;">

.. raw:: html

   <img src="_static/carta_fn_imageViewer_settingsDialog3.png" 
        style="width:100%;height:auto;">

.. raw:: html

   <img src="_static/carta_fn_imageViewer_settingsDialog4.png" 
        style="width:100%;height:auto;">

Image export for presentation
-----------------------------

The image can be exported as a PNG image by clicking the "**Export image**" button at the bottom-right corner of the Image Viewer or by "**File**" -> "**Export image**". High-resolution PNG images can be requested with the additional "200%" and "400%" options. With the "100%" option, the resolution is the same as the screen resolution. With these options, you can set the resolution as 1X, 2X, or 4X the screen resolution. Note that if you use a high-resolution screen to export a PNG image and the request resolution exceeds the limitation of WebGL2, the final resolution of the PNG image will be reduced automatically. 

.. raw:: html

   <img src="_static/carta_fn_exportImagePNG.png" 
        style="width:100%;height:auto;">


Depending on the theme, a background layer in white or black will be added to the PNG file by default. If you prefer a transparent background, please go to "**File**" -> "**Preferences**" -> "**Global**" and set the "**Transparent image background**" toggle to false. 


