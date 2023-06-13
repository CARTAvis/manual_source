Image cube visualization
========================
With v3.0.0, CARTA provides the following widgets and dialogs for image cube visualization:

* Widget
  
  * image viewer: to view raster images and contour images
  * render configuration: to configure how a raster image is rendered
  * animator: to navigate through different images, different channels, or different polarization components
  * image list: to configure image matching in world coordinates and in the spectral domain

* Dialog

  * file browser: to view image headers, and to load or to append an image
  * contour configuration: to configure how a contour image is computed and rendered
  * vector overlay configuration: to configure how a vector overlay is computed and rendered
  * file header: to view image header
  * overlay settings: to configure the appearance of an image in the image viewer


Server-side status and session resume
-------------------------------------
As CARTA is fundamentally a client-server application, it would be essential to know the status of the server side at the client side (i.e., your web browser). It is also useful to know if the standalone version runs normally or not. The server (also known as the carta_backend) status is displayed as a circular icon at the top-right corner of the main browser window. The connection latency and a session ID can be seen by hovering over the icon. There are three kinds of status:

* Green: this means that the server side is connected successfully.
* Orange: this means that the initial connection to the server side was broken (e.g., unstable internet) but has been reconnected. You will be asked to resume the previous session or not.  
* Red: this means that the server side is not accessible, either due to broken internet or backend crash. CARTA is not functional in this case. 

.. raw:: html

   <img src="_static/carta_gui_server_status.png" 
        style="width:100%;height:auto;">


If CARTA behaves abnormally or stops responding, please check the server-side status icon and the connection latency. If it becomes red, the connection between the client side and the server side is interrupted. At this point, CARTA is not functional. When the connection is re-established automatically, the status icon becomes orange and a prompt will be shown to ask users whether or not to resume the previous CARTA session. By clicking the "**Retry**" button, CARTA will try to resume the previous session if possible. If you choose not to resume the previous session, please reload CARTA to establish a new session. Interacting with CARTA when the status icon is in orange may lead to abnormal behaviours. 
   
.. raw:: html

   <img src="_static/carta_gui_session_resume.png" 
        style="width:100%;height:auto;">
   
If you are using the Site Deployment Mode (SDM) of CARTA and encountering the case that the backend is not accessible, you can go to the dashboard to restart a CARTA service. The dashboard can be visited also via the menu "**Server**" -> "**Dashboard**" in normal state. With the dashboard, you can 

* Start a new CARTA session (using the same backend)
* Restart a CARTA service (a.k.a., backend)
* Show backend log
* Logout

Note that the dashboard may look differently per site deployment. 

.. raw:: html

   <img src="_static/carta_gui_dashboard.png" 
        style="width:100%;height:auto;">




File browser
------------
The file browser, accessible via the menu "**File**" -> "**Open image**" or the menu "**File**" -> "**Append image**", provides a list of images and their information supported by CARTA. The supported image formats are:  

* CASA format
* HDF5 format (IDIA schema)
* FITS format
* MIRIAD format 

By default, only images matched these formats will be shown in the file list. If you usually work with directories containing lots files, you may switch to a different file list generation mode via "**File**" -> "**Preferences**" -> "**Global**" -> "**File list**". The performance of the file list generation can be improved by just using the file extension as the parser or by simply listing all files without parsing the image type.

When an image is selected, a brief summary of image properties is provided on the right hand side of the dialog. Full image header is available in the second tab. To view an image, click the "**Load**" button at the bottom-right corner. You can also double-click an image to load it directly. To view a new image and close all the loaded images, use "**File**" -> "**Open image**" -> "**Load**" button. To view a new image without closing all the loaded images, use "**File**" -> "**Append image**" -> "**Append**" button. 

.. raw:: html

   <img src="_static/carta_fn_fileBrowser.png" 
        style="width:100%;height:auto;">


If multiple images are required to perform joint visualization and analysis (e.g., CO 2-1, 13CO 2-1, and C18O 2-1), you can select *multiple* files in the file list with "**shift+click**"/"**command+click**" (macOS) or "**shift+click**"/"**ctrl+click**" (Linux) and load or append them all at once.  

.. raw:: html

   <img src="_static/carta_fn_fileBrowser_multiple_selection.png" 
        style="width:100%;height:auto;">


Files and sub-directories can be searched via the filter field near the bottom of the file browser. Three different methods are supported:

* Fuzzy search: free typing
* Unix pattern: e.g., \*.fits
* Regular expression: e.g., colou?r

The file browser remembers the last path where an image was opened within one CARTA session and the path is displayed (as breadcrumbs) at the top of the file browser. Therefore, when the file browser is re-opened to load other images, a file list will be displayed at the last path where the previous image was loaded. CARTA can also remember the last path for a *new* CARTA session via "**File**" -> "**Preferneces**" -> "**Global**" -> "**Save last used directory**".

You can use the breadcrumbs to navigate to one of the parent directories or click the home button to navigate to the base (i.e., initial) directory directly. To get an updated file list from the server side, you can click the reload button.

For the CARTA deployed in the "Site Deployment Mode", the server administrator can limit the global directory access through the :code:`--top_level_folder` flag when a CARTA backend service is initialized. 

.. code-block:: bash

   exec carta_backend /scratch/images/Orion --top_level_folder /scratch/images

In the above example, you will see a list of images at the directory "/scratch/images/Orion" when you access the file browser dialog for the first time in a new session. You can navigate to any other folders inside "/scratch/images/Orion". By clicking the home button, you will navigate to the directory "/scratch/images/Orion" directly. You can also navigate one level up to "/scratch/images", but not beyond that (neither "/scratch" nor "/") as limited by the :code:`--top_level_folder` flag. 

An image can be closed via "**File**" -> "**Close image**". The active image (the image in the single-panel view or the image highlighted with a red box in the multi-panel view) will be closed. Alternatively, you can close an image via the context menu (right-click) in the image list widget. Note that if the image being closed is a WCS reference image, any other matched images to this reference image will be unmatched. Therefore, they will be just like individual images. 


.. tip::
   An image may be opened directly using a modified URL. For example, if you want to open an image file "/home/acdc/CARTA/Images/jet.fits", you can append
     
   .. code-block:: text 
     
      &folder=/home/acdc/CARTA/Images&file=jet.fits

   or

   .. code-block:: text 
     
      &file=/home/acdc/CARTA/Images/jet.fits
        
   to the end of the URL (e.g., http://192.168.0.128:3002/?token=E1A26527-8226-4FD5-8369-2FCD00BACEE0). In this example the full URL is 
     
   .. code-block:: text 
    
      http://192.168.0.128:3002/?token=E1A26527-8226-4FD5-8369-2FCD00BACEE0&folder=/home/acdc/CARTA/Images&file=jet.fits 
   
   or

   .. code-block:: text 
    
      http://192.168.0.128:3002/?token=E1A26527-8226-4FD5-8369-2FCD00BACEE0&file=/home/acdc/CARTA/Images/jet.fits

   Please note that it is necessary to supply a *full* path. Tilde (~) as your home directory is not allowed.


.. note::
   CARTA image loading performance

   The per-channel rendering approach helps to improve the performance of loading an image significantly. Traditionally when an image is loaded, the minimum and maximum of the entire image (cube) are computed first before image rendering. This becomes a serious performance issue if the image (cube) size is extraordinarily large (> several GB). In addition, applying the global minimum and maximum to render a raster image usually (if not often) results in a poorly rendered image if the dynamic range is high. Then you will need to re-render the image repeatedly with refined boundary values. Re-rendering such a large image repeatedly with CPUs further deduces user experiences.

   CARTA improves the image viewing experience by adopting GPU-accelerated rendering techniques in the web browser environment. In addition, CARTA only renders an image with just sufficient image resolution (image tiles with a proper down-sampling factor) for your screen. This combination results in a scalable and high-performance remote image viewer. The total file size is no longer a bottleneck. The determinative factors are: 1) image size in x and y dimensions, 2) internet bandwidth, and 3) storage I/O performance, instead. For a laptop with 8 GB of RAM, the largest image it can load without swapping is about 40000 pixels by 40000 pixels (assuming most of the RAM is free before loading the image). 

   The approximated RAM usage of loading an image with various spatial sizes is summarized below.
   
   +----------------------------------+----------------------------+
   | Image size (x, y) [pixel]        | RAM usage                  |
   +==================================+============================+
   | 512                              | 1 MB                       | 
   +----------------------------------+----------------------------+
   | 1024                             | 4 MB                       |
   +----------------------------------+----------------------------+
   | 2048                             | 16 MB                      | 
   +----------------------------------+----------------------------+
   | 4096                             | 64 MB                      |
   +----------------------------------+----------------------------+
   | 8192                             | 256 MB                     | 
   +----------------------------------+----------------------------+
   | 16384                            | 1 GB                       |
   +----------------------------------+----------------------------+
   | 32768                            | 4 GB                       | 
   +----------------------------------+----------------------------+
   | 65536                            | 16 GB                      |
   +----------------------------------+----------------------------+

HDF5 (IDIA schema) image support
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Except the CASA image format, the FITS format, and the MIRIAD format, CARTA also supports images in the HDF5 format under the IDIA schema.  The IDIA schema is designed to ensure that efficient image visualization is retained even with extraordinary large image cubes (hundreds GB to a few TB). The HDF5 image file contains extra data to skip or to speed up expensive computations, such as per-cube histogram or spectral profile, etc. An outline of the content of an HDF5 image is provided below:

* XYZW dataset (spatial-spatial-spectral-Stokes): similar to the FITS format
* ZYXW dataset: rotated dataset
* per-channel statistics: basic statistics of the XY plane
* per-cube statistics: basic statistics of the XYZ cube
* per-channel histogram: histogram of the pixel values of the XY plane
* per-cube histogram: histogram of the XYZ cube
* per-channel mip map: downsampled image tiles

A FITS-to-HDF5 convertor is provided by the CARTA development team for you to convert a FITS image to the HDF5 (IDIA schema) format. You can refer to :ref:`fits2idia_installation` on how to install "fits2idia" program on your platform.

The "fits2idia" usage is the following:

.. code-block:: text

   IDIA FITS to HDF5 converter version 0.1.15 using IDIA schema version 0.3
   Usage: fits2idia [-o output_filename] [-s] [-p] [-m] input_filename

   Options:
   -o	Output filename
   -s	Use slower but less memory-intensive method (enable if memory allocation fails)
   -p	Print progress output (by default the program is silent)
   -m	Report predicted memory usage and exit without performing the conversion
   -q	Suppress all non-error output. Deprecated; this is now the default.



.. note::
   Currently the per-plane beam table is not supported in the HDF5 (IDIA schema) format. 


.. _forming_hypercube:

Forming a Stokes hypercube
^^^^^^^^^^^^^^^^^^^^^^^^^^
If a set of individual Stokes images needs to be loaded into CARTA for data inspection with the Stokes analysis widget, you can multi-select individual Stokes images (i.e., image_I.fits, image_Q.fits, image_U.fits, and image_V.fits) in the file list with "**shift+click**"/"**command+click**" (macOS), or "**shift+click**"/"**ctrl+click**" (Linux). If the selected images are qualified to form a Stokes hypercube (a virtual cube from multiple image files), a "**Load as hypercube**" button will show up. When the button is clicked, a dialog will show up for you to confirm the identification of the Stokes parameters of the selected images. After clicking the "**Load**" button, the backend will form a hypercube from the selected images. *Effectively*, there is only one image with multiple Stokes parameters loaded in CARTA.

.. raw:: html

   <img src="_static/carta_fn_fileBrowser_multiple_selection_hypercube.png" 
        style="width:100%;height:auto;">
 
If you want to save a Stokes hypercube as a new image file, you can use the menu "**File**" -> "**Save image**".

Loading images with the Lattice Expression Language (LEL)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
CARTA supoorts loading images via the Lattice Expression Language (LEL) interface. To enable this feature, click the "**Filter**" dropdown menu in the file browser and switch to the "**Image arithmetic**" mode. Please refer to the `Lattice Expression Language`_ section of the CASA user manual for detailed usages.

.. _Lattice Expression Language: https://casacore.github.io/casacore-notes/223.html

With the LEL interface, you can apply arithmetics on images and load the result as an image in CARTA. For example, with the expression

.. code-block:: text

   "line_plus_continuum.fits" - "continuum.fits"

a "line only" image will be computed and loaded in CARTA.

When the LEL interface is enabled, you can either enter the expression manually in the expression field or you can use mouse click to auto-complete an image file name to speed up the process. 

.. raw:: html

   <img src="_static/carta_fn_fileBrowser_LEL.png" 
        style="width:100%;height:auto;">

If you want to save the image computed via the LEL interface, you can use the menu "**File**" -> "**Save image**".


Loading a complex-valued image
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A complex-valued CASA image is suppored in CARTA. When a CASA image is detected as complex-valued, the "**Load as**" button includes the following components:

* Amplitude
* Phase
* Real
* Imaginary

as loading options. You can select a desired component to load or to append. 

.. raw:: html

   <img src="_static/carta_fn_fileBrowser_complexImage.png" 
        style="width:100%;height:auto;">

If you want to save a component (e.g., Amplitude) as a new image file with the float data type, you can use the menu "**File**" -> "**Save image**".




Image viewer
------------

.. warning::
    If you are running a VNC session from a headless server, CARTA may fail to render images properly (they may appear as a block with a uniform color or as an empty plot). This is due to the fact that CARTA renders images using WebGL2 which uses GPU to accelerate the rendering process. Most headless servers have neither discrete nor integrated GPUs. In such cases, it is highly recommended to use your *local* web browser to access the backend as it is much more efficient than VNC. Please refer to the section :ref:`how_to_run_carta`.


CARTA can render images in different ways, such as:

1. a single raster image
2. a single raster image plus its own contours
3. a single raster image plus a set of contour images with matched world coordinates from other image files 
4. a set of contour images without a background raster image

.. raw:: html

   <img src="_static/carta_fn_imageViewer_examples.png" 
        style="width:100%;height:auto;">

When an image is loaded in CARTA, it is shown as a raster image by default, such as the first example in the above figure. Users then could generate contour images (see :ref:`contourrendering`) and enable WCS matching between different images (see :ref:`wcsmatching`), such as the other three examples above.

In addtion, a vector overlay from a vector field (e.g., a linear polarization field or a magnetic field, etc.) or from a scalar field (e.g., a temperature field or a column density field, etc) can be added in the image view (see :ref:`vectorrendering`).

.. raw:: html

   <img src="_static/carta_fn_imageViewer_examples2.png" 
        style="width:100%;height:auto;">

By default, a colorbar is displayed along with the raster image at the right hand side. You can configure its properties in the settings dialog (the "**cog**" button at the top-right corner) of the image viewer widget. In "**File**" -> "**Preferences**" -> "**WCS and image overlay**", you can set colorbar properties persistent for new images, such as the orientation of the colorbar, for example. When you hover over the colorbar, a colorscale value is displayed at the bottom of the colorbar and a realtime color clip of the colorscale value is applied to the image viewer to assist you investigating features in the image. The pixels less than the colorscale are rendered in grayscale temporarily. This interactive feature can be disabled in "**File**" -> "**Preferences**" -> "**WCS and image overlay**".


.. raw:: html

   <img src="_static/carta_fn_imageViewer_colorbar.png" 
        style="width:100%;height:auto;">



.. note::
   Tiled rendering techniques

   CARTA utilizes an efficient approach, "tiled rendering", to display a raster image. What you see in the image viewer is an ensemble of image tiles (default 256 pixel by 256 pixel) processed in parallel. As an example shown in the figure below, if we have an image with 2048 pixels by 2048 pixels, tiles will be constructed in four layers with different downsample factors. The zero-th layer contains only one tile with a size of 256 pixels by 256 pixels. A downsample factor of 8 is applied to the original image to create this tile. The first layer contains four tiles with each a size of 256 pixels by 256 pixels. The downsample factor of 4 is applied to the original image to create these four tiles. This process continues until no downsampling is required. In this case, the tiles of the third layer are not downsampled. When you change the field of view, or the size of the image viewer, tile data of the *right* layer matching your screen resolution will be used. For example, if you are interested in the field of the blue box and the image viewer has a screen size of 512 pixels by 384 pixels, tiles of the 2nd layer will be used for rendering. In this case, nine tiles will be used. If you pan a little bit around the blue box, no new tile data are required. However, if you pan the view to the green box with the same viewer size, two additional tiles from the 2nd layer are required and four tiles will be *re-used* for rendering. With this tiled rendering approach, tiles will be re-used at different zoom levels and with different fields of view to minimize the amount of data transfer while keeping the image sharp on screen. Effectively, you will see that the image becomes sharper and sharper at higher and higher zoom levels.


   .. raw:: html

      <img src="_static/carta_fn_tiledRendering.png" 
           style="width:80%;height:auto;">

   Below is a demonstration of the tiled rendering in action. Note that the video clip is made under a special internet condition for you to see the process clearly. Normally images are rendered much faster.

   .. raw:: html

      <video controls style="width:100%;height:auto;">
         <source src="_static/carta_fn_tiledRendering_demo.mp4" type="video/mp4">
      </video>


   The performance of the tiled rendering can be customized with the preferences dialog, "**File**" -> "**Preferences**" -> "**Performance**". The default values are chosen to assure raster images are displayed efficiently with sufficient accuracy. Advanced users may refine the setup if necessary. For example, when accessing a remote backend under a poor internet condition, the compression quality might be lowered down a bit to make the tile data smaller. Note that a lower compression quality might introduce noticeable artifacts on the raster image. Please adjust with caution. Alternatively, you may enable the low bandwidth mode, which will reduce required image resolutions by a factor of 2 (so that image will look a bit blurry) and cursor responsiveness from 200 ms to 400 ms (HDF5 images: from 100 ms to 400 ms). Under good internet conditions, you may enable streaming image tiles while zooming to see progressive updates of image resolutions at different zoom levels. 

   .. raw:: html

      <img src="_static/carta_fn_tiledRendering_preference.png" 
           style="width:80%;height:auto;">



In addition to displaying images, the image viewer displays cursor information at the top and provides a set of tool buttons at the bottom-right corner when you use the mouse to hover over the image. 

.. raw:: html

   <img src="_static/carta_fn_imageViewer_intro.png" 
        style="width:100%;height:auto;">

The tool buttons allow users to:

* measure an angular distance
* select a source from the catalog overlay (if applicable)
* create region of interest
* perform zoom actions
* enter pan mode
* trigger matching images in world coordinates and/or in the spectral domain
* change reference coordinate grid lines and labels
* export image as a png file
* hide/show the toolbar

.. raw:: html

   <img src="_static/carta_fn_imageViewer_toolButtons.png" 
        style="width:70%;height:auto;">

The aspect ratio of the image view is determined by the panel geometry. When the image viewer panel is resized, a tooltip with a ratio in screen pixel will be displayed (c.f., :ref:`resizing_a_panel` ).


When the cursor is on the image viewer, the pixel information at the cursor position is shown at the top side of the image. The information includes:

* World coordinate of the current coordinate system. 
* Image coordinate in pixel (0-based).
* Pixel value.
* Frequency, velocity, reference frame (if applicable), and polarization parameter (if applicable).


.. raw:: html

   <img src="_static/carta_fn_imageViewer_cursorInfo.png" 
        style="width:100%;height:auto;">

When the coordinate system is changed (e.g., ICRS to Galactic), the displayed world coordinate will be changed accordingly. By default, they are displayed in decimal degrees for Galactic and Ecliptic systems, while for FK5, FK4, and ICRS systems, they are displayed in sexagesimal format. The precision of both formats is determined dynamically based on the image header and the image zoom level. 

The reference image coordinate (0, 0) locates at the center of the bottom-left pixel of the image. Regardless of whether the displayed image is down-sampled or not, the image coordinate always refers to the full resolution image.

When the cursor is moving, a pixel value of the full resolution image is displayed. If the image header provides sufficient information in the frequency/velocity domain, a frequency and a velocity with the reference frame of the current channel will be shown. If the polarization information is available in the image header, a polarization parameter (e.g., Stokes I) will be displayed as well.

To stop/resume cursor update, press the "**F**" key. When the cursor stops updating, the cursor information bar, cursor spatial profiler, and cursor spectral profiler will stop updating too.


Single-panel view and multi-panel view
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The image viewer provides two modes for you to view images: single-panel view and multi-panel view. By default, a *dynamic* multi-panel view mode is enabled. You can use the "**view mode**" button at the top-right corner of the image viewer widget to switch in between the two modes. The view mode is persistent in a new CARTA session (i.e., it is an implicit preference). Additional view mode configuration options are available in the settings dialog of the image viewer widget. You can have a dynamic multi-panel view layout (with a configurable maximum n rows by m columns) based on the number of loaded images, or have a fixed layout regardless how many images are loaded. You can use the "**next page**" and "**previous page**" buttons at the top-right corner of the image viewer to view images if the current grid layout cannot show all loaded image at once.  

.. raw:: html

   <img src="_static/carta_fn_imageViewer_panelMode.png" 
        style="width:100%;height:auto;">

When the view mode is single-panel, the image in the view is the "active" image. When the view mode is multi-panel, the "active" image is highlighted with a red box. In the above example, the image on the right hand side is the "active" image. In the image list widget (the widget at the bottom-right corner in the above example), the "active" image is highlighted in boldface. There is always an "active" image, except the case when no image is loaded in CARTA. You can use the animator widget or the image list widget to select a new "active" image. 

In analytics widgets, such as the statistics widget or the spectral profiler widget, etc., the "**Image**" dropdown menu contains a list of loaded images, as well as an option as "Active" (default) which refers to the "active" image in the image viewer. This feature allows you to view the analytics of the "active" image efficiently without the need of extra configurations in all analytics widgets. If you use the "**Image**" dropdown menu to seelct an image other than "Active", the analytics widgets will stop updating if you set a new "active" image. For example, you can enable two statistics widgets and use the "**Image**" dropdown menu to configure the widgets to show the statistics from two different images, respectively.

Raster rendering
^^^^^^^^^^^^^^^^
The render configuration widget controls how a raster image is rendered in the image viewer. On the top, there is a row of buttons with different clip levels plus a custom button. Below there is a plot showing the per-channel histogram (with logarithmic scale in y) with a bin count equal to the geometric mean of the image size (x and y). The two vertical red bars indicate the two clip values of a color map. The green dashed line marks the mean value and the green box marks the range from mean minus one standard deviation to mean plus one standard deviation. The gray curve between the two red vertical bars shows the applied scaling function including bias and contrast parameters. 

Interaction with a chart, such as the histogram, is demonstrated in the section :ref:`mouse_interaction_with_charts`. On the right, there is a column of options, such as histogram type, scaling function, color map, invert color map, clip values, control parameter of a scaling function (if applicable), and bias/contrast adjustment (i.e., a 2D box with x as bias and y as contrast). Extra options to configure the histogram plot are placed in the settings dialog of the render configuration widget, enabled by the "**cog**" button at the top-right corner of the render configuration widget. The histogram can be exported as a png image or a text file in TSV format.

By default, CARTA calculates a per-channel histogram. When a per-cube histogram is requested, a warning message and a progress dialog will show up. Calculating a per-cube histogram can be time-consuming for large image cubes. You may cancel the request at any time by pressing the "**cancel**" button in the progress dialog. If the image is in the HDF5 format (IDIA schema), the pre-calculated per-cube histogram will be loaded directly and displayed instantly. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_renderConfig_widget_poster.png" preload="none">
     <source src="_static/carta_fn_renderConfig_widget.mp4" type="video/mp4">
   </video>

CARTA determines the boundary values of a color map on a **per-channel** basis by default. That is, a default "99.9%" clip level is applied to the per-channel histogram to look for the two clip values. Then apply the values in "linear" scale with zero bias and zero contrast to the default color map "inferno" to render a raster image. This helps to inspect an image in detail without suffering from improper image rendering in most cases. Below is an example of this per-channel rendering approach.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_renderConfig_perFrame_poster.png" preload="none">
     <source src="_static/carta_fn_renderConfig_perFrame.mp4" type="video/mp4">
   </video>

However, when comparing images channel by channel, color scales need to be fixed. This can be easily achieved by dragging the two vertical red bars, or typing in the values. When this happens, the "custom" button is enabled automatically and *all* channels will be rendered with the fixed boundary values. By clicking one of the clip buttons, CARTA switches back to the per-frame rendering mode *if a per-channel histogram is requested*. Users may request the per-cube histogram to determine proper clip values. Below is an example of custom rendering with the per-cube histogram. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_renderConfig_perCustom_poster.png" preload="none">
     <source src="_static/carta_fn_renderConfig_perCustom.mp4" type="video/mp4">
   </video>

CARTA provides a set of scaling functions, including:

* linear: :math:`y = x`
* log: :math:`y = {\log}_{{\alpha}x+1}({\alpha}x+1)`
* square root: :math:`y = {\sqrt{x}}`
* squared: :math:`y = x^2`
* gamma: :math:`y = x^{\gamma}`
* power: :math:`y = ({\alpha}^x-1)/({{\alpha}-1})`

A set of color maps adopted from `matplotlib <https://matplotlib.org/tutorials/colors/colormaps.html?highlight=colormap>`_ is provided in CARTA.

.. raw:: html

   <img src="_static/carta_fn_renderConfig_colormaps.png" 
        style="width:100%;height:auto;">

The default scaling function, color map, percentile rank (clip level), and a color for NaN pixels can be customized via the menu "**File**"" -> "**Preferences**"" -> "**Render Configuration**". When the "**Smoothed bias/contrast**" toggle is disabled, bias and contrast are applied in the way that the resulting scaling function is piecewise-smooth. 

.. raw:: html

   <img src="_static/carta_gui_preferences_renderConfig.png" 
        style="width:80%;height:auto;">


.. note::
   Viewing a position-velocity image

   When a position-velocity image is loaded as a raster image, CARTA switches to the mode of using *rectangular* pixels for rendering in order to have a better readability. The pixel aspect ratio is flexible based on the aspect ratio of the image viewer widget. By default, the "spectral" axis is displayed in velocity if it is possible based on the image header. You may use the image viewer settings dialog to apply a conversion to other spectral conventions, such as frequency or wavelength. The frequency to velocity conversion requires a reference rest frequency. This reference rest frequency is derived from the image header. You may use the settings dialog of the image list widget to set a new reference rest frequency so that the velocity axis can be recomputed. 

   .. raw:: html

      <img src="_static/carta_fn_imageviewer_pv_rendering.png" 
           style="width:100%;height:auto;">


.. _contourrendering:

Contour rendering
^^^^^^^^^^^^^^^^^
In addition to raster rendering, CARTA supports contour rendering as well. A contour image layer can be created on the same raster image or on a different raster image with world coordinates matched properly. The contour generation process is achieved with the contour configuration dialog which can be launched via the dialog bar.

.. raw:: html

   <img src="_static/carta_fn_contourConfig.png" 
        style="width:65%;height:auto;">

You can follow the steps to generate a contour image:

1. Define contour levels. There are several ways to define a set of contour levels to be calculated at the server side:
  
  a. by typing in individual level in the "**Levels**" field manually
  b. by using the "**Generator**" to generate a series of levels
  c. by clicking directly on the histogram plot to create levels (right-click on an existing level to remove)

  Note that the "**Levels**" field is editable even if a set of levels has been generated with the level generator. 

2. (optional) Define a smooth scheme and a kernel size in the "**Configuration**" tab. The default is Gaussian smooth with a kernel size of 4 by 4 pixels. 

3. (optional) Define the appearance of contours to be rendered at the client side in the "**Styling**" tab. The appearance of contours can be modified after a set of contours has been rendered at the client side without triggering new contour calculations at the server side. This is the advantage of utilizing WebGL2 at the client side. 

Once a set of levels has been defined, you can click the "**Apply**" button to visualize the contour image. Contour image is rendered progressively if there are lots of contour vertices.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_contourRendering_poster.png" preload="none">
     <source src="_static/carta_fn_contourRendering.mp4" type="video/mp4">
   </video>

In the above demonstration, a contour image is generated on top of its raster image. If you would like to plot a contour image on top of another raster image (e.g., velocity field as contour, integrated intensity image as raster), you need to enable WCS matching of the two raster images first (see :ref:`wcsmatching`). Then you can generate a contour image just like the example above. The contour image will be visible on *all* the images that are matched to the spatial reference image in world coordinates, including the spatial reference image.


.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_contourMatching2_poster.png" preload="none">
     <source src="_static/carta_fn_contourMatching2.mp4" type="video/mp4">
   </video>


If there are multiple images loaded in the append mode, you may use the "**Data Source**" dropdown menu to select an image as the input data for contour calculations. If the state of the "**lock**" button is locked, the image viewer will show the selected image as a raster image and the image slider in the animator widget will be updated to the selected image too. To disable this synchronization, click the "**lock**" button to set the state to unlocked. 

CARTA provides four different level generators to assist you defining a set of contour levels. 

* "start-step-multiplier"

  A set of "**N**" levels will be computed from "**Start**" with a (variable) "**Step**" and a "**Multiplier**". For example, if start = 1.0, step = 0.1, N = 5, and multiplier = 2, five levels will be generated as "1.0, 1.1, 1.3, 1.7, 2.5". The function of the multiplier is to make the step increase per next new level. Default parameters derived from the full image statistics (per-channel) are:

  - start: mean + 5 * standard deviation
  - step: 4 * standard deviation
  - N: 5
  - multiplier: 1

* "min-max-scaling"

  A set of "**N**" levels will be calculated between "**Min**" and "**Max**" based on the "**Scaling**" function. For example, if min = 2, max = 10, N = 5, scaling = "linear", five levels will be generated as "2, 4, 6, 8, 10". Default parameters derived from the full image statistics (per-channel) are:

  - min: lower bound of 99.9% clip
  - max: upper bound of 99.9% clip
  - N: 5
  - scaling: "linear"

* "percentages-ref.value"

  A set of "**N**" levels will be derived as the percentages ("**Lower(%)**" and "**Upper(%)**") of the "**Reference**" in linear spacing. For example, if reference = 1.0, N = 5, lower(%) = 20, upper(%) = 100, five levels will be generated as "0.2, 0.4, 0.6, 0.8, 1.0".

  - reference: upper 99.9% clip
  - N: 5
  - lower(%): 20
  - upper(%): 100

* "mean-sigma-list"

  A set of "**N**" levels will be generated as "**Mean**" plus multiples of "**Sigma**" based on the "**Sigma list**". For example, if mean = 1, sigma = 0.1, and sigma list = [-5, 5, 10, 15, 20], five levels will be generated as "0.5, 1.5, 2.0, 2.5, 3.0". Default parameters derived from the full image statistics (per-channel) are:

  - mean: full image mean value
  - sigma: full image standard deviation
  - sigma list: [-5, 5, 9, 13, 17]

CARTA provides three different contour smoothing methods, including "no smooth", "Gaussian smooth", and "block smooth", in the "**Configuration**" tab. The kernel for smoothing is in N by N pixels. The default is to apply "Gaussian smooth" with 4 by 4 pixels as the kernel size. Depending on science cases, you may choose a different smooth method and a different kernel size. 

.. raw:: html

   <img src="_static/carta_fn_contourSmooth.png" 
        style="width:100%;height:auto;">

The appearance of contours can be customized in the "**Styling**" tab. As an example, you may use the options to plot contours like below. Iso-velocity contours are rendered in different colors to present Doppler shifts of the source kinematics.

.. raw:: html

   <img src="_static/carta_fn_contourStyling.png" 
        style="width:50%;height:auto;">


.. _vectorrendering:

Vector field rendering
^^^^^^^^^^^^^^^^^^^^^^
A vector overlay can be added to the image viewer from a vector field derived from an image, such as a linear polarization field or a magnetic field, or from a scalar field derived from an image, such as a temperature field or a column density field via the vector overlay configuration dialog.  

.. raw:: html

   <img src="_static/carta_fn_vectorOverlay.png" 
        style="width:65%;height:auto;">

There are different ways to configure how a vector element is derived from the "**Data Source**" via the "**Angular Source**" and the "**Intensity Source**" dropdown menus:

1. For visualization of linear polarization from a Stokes IQU or QU cube with *variable* vector length and angle: set the "**Angular Source**" to "Computed PA" and set the "**Intensity Source**" to "Computed PI".
2. For visualization of linear polarization from a Stokes IQU or QU cube with *fixed* vector length and variable angle: set the "**Angular Source**" to "Computed PA" and set the **"Intensity Source**" to "None".
3. For visualization of linear polarization from a pre-computed position angle image in degrees: set the "Angular Source" to "Current image" and set the "**Intensity Source**" to "None". 
4. For visualization of a scalar field by interpreting pixel value as the strength or intensity: set the "**Angular Source**" to "None" and set the "**Intensity Source**"" to "Current image". With this mode, a filled square marker is rendered instead of a line segment.

Examples of the four different vector overlay rendering are shown in the following figure.

.. raw:: html

   <img src="_static/carta_fn_vectorOverlay_examples.png" 
        style="width:100%;height:auto;">



Usually block smoothing is applied to the "**Data Source**" image to enhance signal-to-noise ratio before computing vector elements. You can enable the "**Pixel Averaging**" toggle (enabled by default) and set the "**Averaging Width (px)**" (default 4 pixel by 4 pixel) to apply pixel averaging. 

When the "**Intensity Source**"" is "Computed PI", you can select "Absolute"; or "Fractional" polarization intensity with the "**Polarization Intensity**" radio buttons. A threshold for Stokes I may be applied to mask out noisy parts of the image with the "**Threshold**" field when the "**Threshold Enabled**" toggle is switched on. If Stokes I is not available (i.e., the input image has Stokes Q and U only), the threshold is applied to Stokes Q and Stokes U to construct a mask. Optionally, you may apply "debiasing" to the polarization intensity and angle calculations by enabling the "**Debiasing**" toggle and set errors for Stokes Q and U in the "**Stokes Q Error**" and the "**Stokes U Error**" fields, respectively.

Once the control parameters of how a vector overlay is computed are set, you can click the "**Apply**" button to trigger the computation and rendering process. The vector overlay data will be streamed progressively similarly to the raster rendering with image tiles. Click the "**Clear**" button to remove the vector overlay.

On spatially matched images, vector elements are reprojected precisely based on the projection schemes. This behaves the same as the contour overlay and catalog image overlay. You can use the image list widget to tigger image matching. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_vectorOverlayMatching_poster.png" preload="none">
     <source src="_static/carta_fn_vectorOverlayMatching.mp4" type="video/mp4">
   </video>


With the "**Styling**" tab, you can configure how vector elements are rendered, including:

* line thickness
* intensity to vector length mapping
* additional rotation offset to vector angle
* color modes of vector elements


As an example, you may use the options to plot a vector overlay like below. Vector elements are rendered in different colors to represent the relative strength of the linear polarization intensity. An angle offset of 90 degrees is applied to the vector elements to *infer* the magetic field morphology. 

.. raw:: html

   <img src="_static/carta_fn_vectorOverlayStyling.png" 
        style="width:50%;height:auto;">



.. _wcsmatching:

Matching images spatially and spectrally
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When there are multiple images loaded in CARTA, you may trigger image matching based on their world coordinates. It is a common practice to compare images from different telescopes or even from the same telescope with different spectral and spatial setups. You can use the "Matching" column of the image list widget to trigger the image matching process,  

.. raw:: html

   <img src="_static/carta_fn_layerList.png" 
        style="width:80%;height:auto;">

or the tool button in the image viewer.

.. raw:: html

   <img src="_static/carta_fn_triggerMatch.png" 
        style="width:50%;height:auto;">

The image list widget shows a list of all loaded images, including their:

* file name
* rendering type ("Layers" column): "**R**" means raster, "**C**" means contour, and "**V**" means vector overlay
* image matching state ("Matching" column): 
   
  * "**XY**" means spatial domain
  * "**Z**" means spectral domain
  * "**R**" means the color range for raster rendering

* channel index
* polarization component 

The first loaded image with valid spatial world coordinates serves as the default spatial reference and is highlighted with an open black box (e.g., HD163296_CO_2_1.image.mom0 in the above example). Similarly, the first loaded image with valid spectral coordinates serves as the default spectral reference and is highlighted with an open black box (e.g., HD163296_CO_2_1.fits in the above example). To match world coordinates of other loaded images, you can click the "**XY**" button to match in the spatial domain and click the "**Z**" button to match in the spectral domain. If you would like to apply the same color range for different raster images, click the "**R**" button so that matched images will have the same color range with respect to the reference image highlighted with an open black box (e.g., HD163296_CO_2_1.image.mom0 in the above example).


You may change a spatial reference image or a spectral reference image or a raster scaling reference by right-clicking an image in the image list widget and use the context menu.

.. raw:: html

   <img src="_static/carta_fn_layerList2.png" 
      style="width:80%;height:auto;">

For raster images, matching in the spatial domain is achieved by applying translation, rotation, and scaling to images with respect to the reference image. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_spatialMatching_poster.png" preload="none">
     <source src="_static/carta_fn_spatialMatching.mp4" type="video/mp4">
   </video>

For contour images, matching in the spatial domain is achieved by reprojecting contour vertices to the raster image in the view. Multiple contour images can be displayed on top of a raster image if spatial matching of the target contour image is enabled. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_contourMatching_poster.png" preload="none">
     <source src="_static/carta_fn_contourMatching.mp4" type="video/mp4">
   </video>

For image cubes, matching in the spectral domain is achieved by nearest interpolation with the target spectral convention. The default is "radio velocity". The reference convention of spectral matching is configurable with the settings dialog of the image list widget. When spectral matching is enabled by clicking the "**Z**" button, the matched channel indices are updated in the image list widget. Images and spectral profiles in the image viewer widget and in the spectral profiler widget are updated, respectively, as well.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_spectralMatching_poster.png" preload="none">
     <source src="_static/carta_fn_spectralMatching.mp4" type="video/mp4">
   </video>

.. note::
   Projection effects of raster images

   As raster images are matched spatially by applying translation, rotation, and scaling, projection effects between different images might be visible if images have a wide field of view and/or images have very different projection schemes. In the following video, projection effects in raster images are demonstrated. However, projection effects of contour images are properly handled in CARTA. Contours are reprojected with sufficient accuracy with respect to the raster image as seen in the image viewer.  

   .. raw:: html

      <video controls style="width:100%;height:auto;" poster="_static/carta_fn_projectionEffect_poster.png" preload="none">
        <source src="_static/carta_fn_projectionEffect.mp4" type="video/mp4">
      </video>


.. note::
   If a spatial reference image or a spectral reference image is closed via "**File**" -> "**Close image**", all matched images will be unmatched and a new reference image will be automatically registered.


Raster image, contour image, or vector overlay image may be hidden in the image viewer by clicking the "**R**" button, the "**C**" button, or the "**V**" button of the "Layers" column in the image list widget, respectively. For example, to create an image with contours only, you can click the "**R**" button to hide the raster image. 
 
.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_hideLayer_poster.png" preload="none">
     <source src="_static/carta_fn_hideLayer.mp4" type="video/mp4">
   </video>

When there are multiple images loaded in CARTA, their loading sequence determines the order in the "**Image**" slider of the animator widget and the image order in the image list widget. With the image list widget, this order can be changed by dragging an entry to a desired place. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_reorderFrame_poster.png" preload="none">
     <source src="_static/carta_fn_reorderFrame.mp4" type="video/mp4">
   </video>





Exploring an image
^^^^^^^^^^^^^^^^^^
CARTA provides different ways to change the image view. With a mouse, image zoom is achieved by scrolling up/down. Image pan is achieved by drag-and-drop or "**command+click**" (macOS) or "**ctrl+click**" (Linux). Alternatively, the image can be changed to fit the image viewer, or to fit the screen resolution (one image pixel to one screen pixel), by using the buttons at the bottom-right corner of the image viewer. Zoom in and zoom out buttons are provided as well.  To change to different images, channels, or polarization, please refer to the section :ref:`animator_intro`.

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_imageViewer_changeView_poster.png" preload="none">
     <source src="_static/carta_fn_imageViewer_changeView.mp4" type="video/mp4">
   </video>

When an image is zoomed in or out, the precision of the coordinate tick values is dynamically adjusted based on the zoom levels. 


Configuring an image plot
^^^^^^^^^^^^^^^^^^^^^^^^^
CARTA provides flexible options to configure the appearance of an image plot. The image settings dialog is accessible by clicking the "**cog**" at the top-right corner of the image viewer widget.

.. raw:: html

   <img src="_static/carta_fn_astOptions.png" 
        style="width:80%;height:auto;">


As an example, below is an image with default overlay settings.

.. raw:: html

   <img src="_static/carta_fn_astOptions_before.png" 
        style="width:100%;height:auto;">

And, this is a customized one. The coordinate system has been switched from FK5 to Galactic. Font type, size, and color are customized, as well as the axis border and grid lines. 

.. raw:: html

   <img src="_static/carta_fn_astOptions_after.png" 
        style="width:100%;height:auto;">


The restoring beam is shown at the bottom-left corner, if applicable.

The image can be exported as a PNG image by clicking the "**Export image**" button at the bottom-right corner of the image viewer, or by "**File**" -> "**Export image**". High-resolution PNG images can be requested with the addtional "200%" and "400%" options. With the "100%" option, the resolution is the same as the screen resolution. You can set the resolution as 1X, 2X or 4X the screen resolution with these options. Note that if you use a high-resolution screen to export a PNG image and the request resolution exceeds the limitation of WebGL2, the final resolution of the PNG image will be reduced automatically. 

.. raw:: html

   <img src="_static/carta_fn_exportImagePNG.png" 
        style="width:100%;height:auto;">


By default a background layer in white or black, depending on the theme, will be added to the PNG file. If you prefer a transparent background, please go to "**File**" -> "**Preferences**" -> "**Global**" and set the "**Transparent image background**" toggle to false. 


.. _animator_intro:

Animator
--------
The animator widget provides controls of image frames, channels, and Stokes. When multiple images are loaded via "**File**" -> "**Append image**", the "**Image**" slider will show up and allow you to switch to a different image. You can also use the image list widget for image switching. If an image file has multiple channels and/or polarization components, the "**Channel**" and/or the "**Polarization**" slider will appear. The double slider right below the "**Channel**" slider allows you to specify a range of channels for animation playback. On the top, there is a set of animation control buttons such as "**Play**", "**Next**", etc. Playback modes, including "forward", "backward", "Bouncing" and "Blink", are supported. Playback action will be applied to the slider with the activated radio button. 


.. raw:: html

   <img src="_static/carta_fn_animator_widget.png" 
        style="width:80%;height:auto;">


The polarization slider shows all the polarization components (Stokes I/Q/U/V, XX/YY/XY/YX, or RR/LL/RL/LR) as defined in the image header. If the Stokes parameters are defined in the image header, additional *computed* compoments, including:

* Ptotal: total polarization intensity (computed from Stokes QU or QUV)
* Plinear: linear polarization intensity (computed from Stokes QU)
* PFtotal: fractional total polarization intensity (computed from Stokes IQU or IQUV)
* PFlinear: fractional linear polarization intensity (computed from Stokes IQU)
* Pangle: linear polarization angle (computed from Stokes QU)

are appended as well. You may save a computed component as a new image file via "**File**" -> "**Save image**".

The "**Frame Rate**" spin box controls the *desired* frame per second (fps). The *actual* frame rate depends on image size and internet condition. Optionally, you can set a step for the animation playback (default as unity). By clicking the "**Frame Rate**" dropdown, the "**Step**" option will show up. 

When there are multiple images loaded in the append mode, their order determines the order in the image slider of the animator widget and the rendering order in the multi-panel view (left-right then top-down). With the image list widget, this order can be changed by dragging an entry to a desired place. 

.. raw:: html

   <video controls style="width:100%;height:auto;" poster="_static/carta_fn_reorderFrame_poster.png" preload="none">
     <source src="_static/carta_fn_reorderFrame.mp4" type="video/mp4">
   </video>



File header dialog
------------------
A brief summary and the full header of an image file can be viewed via the file browser dialog. Alternatively, they can be viewed via the file header dialog (from the dialog bar). In the header tab, you may use the "**search**" button to look for a keyword. You can also use the "**export**" button to save the header as a text file.

.. raw:: html

   <img src="_static/carta_fn_fileHeader.png" 
        style="width:90%;height:auto;">

