Image cube visualization
========================
With version 2.0, CARTA provides the following widgets and dialogues for image cube visualization:

* Widget
  
  * image viewer: to view raster images and contour images
  * render configuration: to configure how a raster image is rendered
  * animator: to navigate through different images, different channels, or different Stokes
  * image list: to configure image matching in world coordinates

* Dialogue

  * file browser: to view image headers, and to load or to append an image
  * contour configuration: to configure how a contour image is rendered
  * file header: to view image header
  * overlay settings: to configure the appearance of an image in the image viewer


Server-side status and session resume
-------------------------------------
As CARTA is fundamentally a client-server application, it would be essential to know the status of the server side at the client side. This is also useful for the standalone version to know if the application runs normally or not. The server (also known as the carta_backend) status is displayed as a circular icon at the top-right corner of the main window. The connection latency and a session ID can be seen by hovering over the icon. There are three kinds of status:

* Green: this means that the server side is connected successfully.
* Orange: this means that the initial connection to the server side was broken (e.g., unstable internet) but has been reconnected. Users will be asked to resume the previous session or not.  
* Red: this means that the server side is not accessible, either due to broken internet or backend crash. CARTA is not functional in this case. 

.. raw:: html

   <img src="_static/carta_gui_server_status.png" 
        style="width:100%;height:auto;">

.. note::
   If CARTA behaves abnormally or stops responding, please check the server-side status icon and the connection latency. If it becomes red, the connection between the client side and the server side is interrupted. At this point, CARTA is not functional. When the connection is re-established automatically, the status icon becomes orange and a prompt will be shown to ask users whether or not to resume the previous CARTA session. By clicking the OK button, CARTA will try to resume the previous session if possible. If users choose not to resume the previous session, please reload CARTA to establish a new session. Interacting with CARTA when the status icon is in orange may lead to abnormal behaviors. 
   
   .. raw:: html

      <img src="_static/carta_gui_session_resume.png" 
           style="width:100%;height:auto;">
   


File browser
------------
File browser, accessible via the menu **File** -> **Open image** or the menu **File** -> **Append image**, provides information of images supported by CARTA. Currently CARTA supports images in:  

* CASA format
* HDF5 format (IDIA schema)
* FITS format
* MIRIAD format 

Only the images matched these formats will be shown in the file list with image type and file size. When an image is selected, a brief summary of image properties is provided on the right side of the dialogue. Full header is also available in the second tab. To view an image, click the **Load** button at the bottom-right corner. To view a new image and close all the loaded images, use **File** -> **Open image** -> **Load** button. To view a new image without closing all the loaded images, use **File** -> **Append image** -> **Append** button.

.. raw:: html

   <img src="_static/carta_fn_fileBrowser.png" 
        style="width:100%;height:auto;">


If a set of images needs to be loaded into CARTA for visualization and analysis (e.g., CO 2-1, 13CO 2-1, and C18O 2-1), users may select *multiple* files in the file list with shift+click or command+click (macOS) or ctrl+click (linux) and load them all at once. Images will be loaded sequentially by clicking the "Load selected" button. 

.. raw:: html

   <img src="_static/carta_fn_fileBrowser_multiple_selection.png" 
        style="width:100%;height:auto;">


If a set of individual Stokes images needs to be loaded into CARTA for data inspection with the Stokes analysis widget, users can select indivisual Stokes images (i.e., image_I.fits, image_Q.fits, image_U.fits, and image_V.fits) in the file list with shift+click or command+click (macOS) or ctrl+click (linux). If the selected images are qualified to form a Stokes hypercube (a virtual cube from multiple image files), a "Load as hypercube" button will show up. When the button is clicked, a dialogue will pop up for users to confirm the identification of the Stokes parameters for selected images. After clicking the "Load" button, the backend will form a hypercube from the selected images. To users, *effectively* there is only one image with multiple Stokes parameters loaded in CARTA.

.. raw:: html

   <img src="_static/carta_fn_fileBrowser_multiple_selection_hypercube.png" 
        style="width:100%;height:auto;">


Files and sub-directories can be searched via the filtering field. Three different methods are supported:

* Fuzzy search: free typing
* Unix pattern: e.g., \*.fits
* Regular expression: e.g., colou?r

File browser remembers the last path where an image was opened within one CARTA session and the path is displayed (as breadcrumbs) at the top of the dialogue. Therefore, when the file browser is re-opened to load other images, a file list will be displayed at the last path where the previous image was loaded. Users can use the breadcrumbs to navigate to one of the parent directories or click the home button to navigate to the base (i.e., initial) directory directly. To get an updated file list from the server side, users can click the reload button.

**[TODO]** For the CARTA-server application, the server administrator can limit the global directory access through the "*top_level_folder*" keyword argument when launching the CARTA backend service. 

.. code-block:: bash

   exec carta_backend port=6002 base=/scratch/images/Orion root=/scratch/images

In the above example, users will see a list of images at the "*base*" directory "/scratch/images/Orion" when accessing the file browser dialogue for the first time in a new session. Users can navigate to any other folders inside "/scratch/images/Orion". By clicking the home button, users will navigate to the "*base*" directory "/scratch/images/Orion" directly. Users can also navigate one level up to "/scratch/images", but not beyond that (neither "/scratch" nor "/") as limited by the "*root*" keyword. 


.. note::
   An image might be closed via **File** -> **Close image**. The image currently displayed in the image viewer will be closed. If the image being closed is a WCS reference image, any other matched images to this reference image will be unmatched, thus they behave like individual images. 

.. note::
   Currently CARTA does not fully support the following types of CASA images:

   * complex image
   * boolean image
   * LEL image 


.. tip::
   **[TODO]** When using CARTA in the remote mode, an image may be opened directly using a modified URL. For example, if we wanted to open a remote image file "/home/acdc/CARTA/Images/jet.fits", we would append
     
   .. code-block:: bash 
     
      &folder=/home/acdc/CARTA/Images&file=jet.fits
        
   to the end of the URL (e.g., http://www.carta.edu:2000/?socketUrl=ws://www.carta.edu:3000). In this example our full URL is 
     
   .. code-block:: bash 
    
      http://www.carta.edu:2000/?socketUrl=ws://www.carta.edu:3000&folder=/home/acdc/CARTA/Images&file=jet.fits 
        
   Please note that it is necessary to take a *full* path. Tilde (~) is not allowed.


HDF5 (IDIA schema) image support
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Except the CASA image format, the FITS format, and the MIRIAD format, CARTA also supports images in the HDF5 format under the IDIA schema.  The IDIA schema is designed to ensure that efficient image visualization is retained even with extraordinary large image cubes (hundreds GB to a few TB). The HDF5 image file contains extra data to skip or to speed up expensive computations, such as per-cube histogram or spectral profile, etc. A brief outline of the content of an HDF5 image is provided below:

* XYZW dataset (spatial-spatial-spectral-Stokes): similar to the FITS format
* ZYXW dataset: rotated dataset
* per-channel statistics: basic statistics of the XY plane
* per-cube statistics: basic statistics of the XYZ cube
* per-channel histogram: histogram of the pixel values of the XY plane
* per-cube histogram: histogram of the XYZ cube

.. note::

   Additional tiled image data (mip map), which will speed up the process of loading very large images significantly, will be added to the HDF5 image file in v3.0. 

.. note::
   Currently per-plane beam is not handled properly when converting a FITS image to the HDF5 format. 

**[TODO]** add instructions of using fits2idia to convert a fits image to hdf5 format. 


File header dialogue
--------------------
A brief summary and the full header of an image file can be viewed via the file browser dialogue. Alternatively, they can be viewed via the file header dialogue (from the dialogue bar). In the header tab, users may use the search function to look for a keyword.

.. raw:: html

   <img src="_static/carta_fn_fileHeader.png" 
        style="width:90%;height:auto;">



Image viewer
------------
CARTA can render images in different ways, such as:

1. a single raster image
2. a single raster image plus its own contours
3. a single raster image plus a set of contour images with matched world coordinates from other image files 
4. a set of contour images without a background raster image

.. raw:: html

   <img src="_static/carta_fn_imageViewer_examples.png" 
        style="width:100%;height:auto;">

When an image is loaded in CARTA, it is shown as a raster image by default, such as the first example in the above figure. Users then could generate contour images (see :ref:`contourrendering`) and enable WCS matching between different images (see :ref:`wcsmatching`), such as the other three examples above.

.. warning::
    **[TODO]** If you are running a VNC session from a headless server, CARTA may fail to render images properly (they may appear as a solid color or as an empty plot). This is due to the fact that CARTA renders images using WebGL which uses GPU to accelerate the rendering process. Most headless servers have neither discrete nor integrated GPUs. In such cases, it is highly recommended to use your *local* web browser to access the backend as it is much more efficient than VNC.

In addition to displaying images, the image viewer displays cursor information at the top and provides a set of tool buttons at the bottom-right corner when hovering on the image. 

.. raw:: html

   <img src="_static/carta_fn_imageViewer_intro.png" 
        style="width:100%;height:auto;">

The tool buttons allow users to:

* select a source from the catalog overlay (if applicable)
* create region of interest
* perform zoom actions
* enter pan mode
* trigger matching images in world coordinates and/or in spectral domain
* change reference coordinate grid lines and labels
* export image as a png file

.. raw:: html

   <img src="_static/carta_fn_imageViewer_toolButtons.png" 
        style="width:50%;height:auto;">

The aspect ratio of the image view is determined by the panel geometry. When the image viewer panel is resized, a tooltip with a ratio in screen pixel will be displayed (c.f., :ref:`resizing_a_panel` ).



Tiled rendering
---------------
CARTA utilizes an efficient approach, "tiled rendering", to display a raster image. What users see in the image viewer is an ensemble of tiles (default 256 pixel by 256 pixel) processed in parallel. As an example shown in the figure below, if we have an image with 2048 pixels by 2048 pixels, tiles will be constructed in four layers with different downsample factors. The zero-th layer contains only one tile with a size of 256 pixels by 256 pixels. A downsample factor of 8 is applied to the original image to create this tile. The first layer contains four tiles with each a size of 256 pixels by 256 pixels. The downsample factor of 4 is applied to the original image to create these four tiles. This process continues until no downsampling is required. In this case, the tiles of the third layer are not downsampled. As users change the field of view, or the size of the image viewer, tile data of the *right* layer will be used. For example, if a user is interested in the field of the blue box and the image viewer has a screen size of 512 pixels by 384 pixels, tiles of the layer 2 will be used for rendering. In this case, nine tiles will be used. If the user pans a little bit around the blue box, no new tile data are required. If the user pans the view to the green box with the same viewer size, only the additional two tiles of layer 2 are required and four tiles will be *re-used* for rendering. With this tiled rendering approach, tiles will be re-used for different zoom levels and different fields of view to minimize the amount of data transfer while keeping the image sharp on screen. Effectively, users will see that the image becomes sharper and sharper at higher and higher zoom levels.


.. raw:: html

   <img src="_static/carta_fn_tiledRendering.png" 
        style="width:80%;height:auto;">

Below is a demonstration of tiled rendering in action. Note that the video clip is made under a special internet condition for users to see the process clearly. Normally images are rendered much faster.

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_tiledRendering_demo.mp4" type="video/mp4">
   </video>


The performance of tiled rendering can be customized with the preferences dialogue, **File** -> **Preferences** -> **Performance**. The default values are chosen to assure raster images are displayed efficiently with sufficient accuracy. Advanced users may refine the setup if necessary. For example, when accessing a remote backend under a poor internet condition, compression quality might be lowered down a bit to make the tile data smaller. Note that a lower compression quality might introduce noticeable artifacts on the raster image. Please adjust with caution. Alternatively, users may enable the low bandwidth mode, which will reduce required image resolutions by a factor of 2 (so that image will look a bit blurry) and cursor responsiveness from 200 ms to 400 ms (HDF5 images: from 100 ms to 400 ms). Under good internet conditions, users may enable streaming image tiles while zooming to see progressive updates of image resolutions at different zoom levels. 

.. raw:: html

   <img src="_static/carta_fn_tiledRendering_preference.png" 
        style="width:80%;height:auto;">


.. note::
   CARTA image loading performance

   The per-channel rendering approach helps to improve the performance of loading an image significantly. Traditionally when an image is loaded, the minimum and maximum of the entire image (cube) are computed first before image rendering. This becomes a serious performance issue if the image (cube) size is extraordinarily large (> several GB). In addition, applying the global minimum and maximum to render a raster image usually (if not often) results in a poorly rendered image if the dynamical range is high. Then users need to re-render the image repeatedly with refined boundary values. Re-rendering such a large image repeatedly with CPUs further deduces user experiences.

   CARTA hopes to improve the image viewing experience by adopting GPU accelerated rendering with web browser technology. In addition, CARTA only renders an image with just enough image resolution (tiles and down-sampling) for your screen. This combination results in a scalable and high-performance remote image viewer. The total file size is no longer a bottleneck. The determinative factors are: 1) image size in x and y dimensions, 2) internet bandwidth, and 3) storage I/O, instead. For a laptop with 8 GB of RAM, the largest image it can load without swapping is about 40000 pixels by 40000 pixels (assuming most of the RAM is free before loading the image). 

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


Render configuration of a raster image
--------------------------------------
The render configuration widget controls how a raster image is rendered in the image viewer. On the top, there is a row of buttons with different clip levels plus a custom button. Below there is a plot showing the per-channel histogram (with logarithmic scale in y) with a bin count equal to the geometric mean of the image size (x and y). The two vertical red bars indicate the two clip values of a colormap. The green dashed line marks the mean value and the green box marks the range from mean - one standard deviation to mean + one standard deviation. The grey curve between the two red vertical bars shows the applied scaling function including bias and contrast parameters. 

Interaction with a chart, such as the histogram, is demonstrated in the section :ref:`mouse_interaction_with_charts`. On the right, there is a column of options, such as histogram type, scaling function, color map, invert color map, clip values, control parameter of a scaling function (if applicable), and bias/contrast adjustment (i.e. a 2D box with x as bias and y as contrast). Extra options to configure the histogram plot are placed in the render configuration settings dialogue enabled by the cog icon at the top-right corner of the render configuration widget. The histogram can be exported as a png image or a text file in tsv format.

By default, CARTA calculates a per-channel histogram. When a per-cube histogram is requested, a warning message and a progress dialogue will show up. Calculating a per-cube histogram can be time-consuming for large image cubes. Users may cancel the request at any time by pressing the cancel button in the progress dialogue. If the image is in the HDF5 format (IDIA schema), the pre-calculated per-cube histogram will be loaded directly and displayed mostly instantly. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_renderConfig_widget.mp4" type="video/mp4">
   </video>

CARTA determines the boundary values of a colormap on a **per-channel** basis by default. That is, a default "99.9%" clip level is applied to the per-channel histogram to look for the two clip values. Then apply the values in "linear" scale to the default colormap "inferno" to render a raster image. This helps to inspect an image in detail without suffering from improper image rendering in most cases. Below is an example of this per-channel rendering approach.

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_renderConfig_perFrame.mp4" type="video/mp4">
   </video>

However, when comparing images channel by channel, color scales need to be fixed. This can be easily achieved by dragging the two vertical red bars, or typing in the values. When this happens, the "custom" button is enabled automatically and *all* channels will be rendered with the fixed boundary values. By clicking one of the clip buttons, CARTA switches back to the per-frame rendering mode *if a per-channel histogram is requested*. Users may request the per-cube histogram to determine proper clip values. Below is an example of custom rendering with the per-cube histogram. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_renderConfig_perCustom.mp4" type="video/mp4">
   </video>

CARTA provides a set of scaling functions, such as:

* linear: :math:`y = x`
* log: :math:`y = {\log}_{{\alpha}x+1}({\alpha}x+1)`
* square root: :math:`y = {\sqrt{x}}`
* squared: :math:`y = x^2`
* gamma: :math:`y = x^{\gamma}`
* power: :math:`y = ({\alpha}^x-1)/({{\alpha}-1})`

A set of colormaps adopted from `matplotlib <https://matplotlib.org/tutorials/colors/colormaps.html?highlight=colormap>`_ is provided in CARTA.

.. raw:: html

   <img src="_static/carta_fn_renderConfig_colormaps.png" 
        style="width:100%;height:auto;">

The default scaling function, colormap, percentile rank, and a color for NaN pixels can be customized via the menu **File** -> **Preferences** -> **Render Configuration**. When the toggle of "Smoothed Bias/Contrast" is disabled, bias and constrast are applied in the way that discontinuity presents in the  resulting scaling function. 

.. raw:: html

   <img src="_static/carta_fn_renderConfig_preferences.png" 
        style="width:80%;height:auto;">


.. _contourrendering:

Contour rendering
-----------------
In addition to raster rendering, CARTA supports contour rendering as well. A contour image layer can be created on the same raster image or on a different raster image with world coordinates properly matched. The contour generation process is achieved with the contour configuration dialogue which can be launched via the dialogue bar.

.. raw:: html

   <img src="_static/carta_fn_contourConfig.png" 
        style="width:65%;height:auto;">

Users may follow the following steps to generate a contour image:

1. Define contour levels. There are several ways to define a set of contour levels to be calculated at the server side:
  
  a. by typing in individual level in the "Levels" field manually
  b. by using the "Generator" to generate a series of levels
  c. by clicking directly on the histogram plot to create levels (right-click on an existing level to remove)

  Note that the "Levels" field is editable even if a set of levels has been generated with the level generator. 

2. (optional) Define a smooth scheme and a kernel size in the "Configuration" tab. The default is Gaussian smooth with a kernel size of 4 by 4 pixels. 

3. (optional) Define the appearance of contours to be rendered at the client side in the "Styling" tab. The appearance of contours can be modified after a set of contours has been rendered at the client side  without triggering new contour calculations at the server side. This is the advantage of utilizing WebGL at the client side. 

Once a set of levels has been defined, users can click the "Apply" button to visualize the contour image. Contour image is rendered progressively if there are lots of contour vertices.

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_contourRendering.mp4" type="video/mp4">
   </video>

In the above demonstration, a contour image is generated on top of its raster image. If users would like to plot a contour image on top of other raster image (e.g., velocity field as contour, integrated intensity image as raster), users need to enable WCS matching of the two raster images first (see :ref:`wcsmatching`). Then users can generate the contour image just like the above example. When the contour image is generated, use the image list widget or the animator widget to switch to the integrated intensity image. Users should see the velocity field image as contours on top of the integrated intensity image as raster. In short, a set of contour images are visible on top of a given raster image in the view if *all* the images are matched in world coordinates. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_contourMatching2.mp4" type="video/mp4">
   </video>


If there are multiple images loaded in the append mode, users may use the "Data Source" dropdown to select an image as the data source of contour calculations. If the state of the "lock" button is locked, the image viewer will show the selected image as a raster image and the image slider in the animator widget will be updated to the selected image too. To disable this synchronization, click the "lock" button to set the state to unlock. 

CARTA provides four different level generators to assist users to construct a set of contour levels. 

* "start-step-multiplier"

  A set of "N" levels will be computed from "start" with a (variable) step. For example, if start = 1.0, step = 0.1, N = 5, and multiplier = 2, five levels will be generated as "1.0, 1.1, 1.3, 1.7, 2.5". The function of the multiplier is to make the step increase per next new level. Default parameters derived from full image statistics (per-channel) are:

  - start: mean + 5 * standard deviation
  - step: 4 * standard deviation
  - N: 5
  - multiplier: 1

* "min-max-scaling"

  A set of "N" levels will be calculated between "min" and "max" with a spacing according to the "scaling" function. For example, if min = 2, max = 10, N = 5, scaling = "linear", five levels will be generated as "2, 4, 6, 8, 10". Default parameters derived from full image statistics (per-channel) are:

  - min: lower bound of 99.9% clip
  - max: upper bound of 99.9% clip
  - N: 5
  - scaling: "linear"

* "percentages-ref.value"

  A set of "N" levels will be derived as the percentages ("Lower(%)" and "Upper(%)") of the "reference" in linear spacing. For example, if reference = 1.0, N = 5, lower(%) = 20, upper(%) = 100, five levels will be generated as "0.2, 0.4, 0.6, 0.8, 1.0".

  - reference: upper 99.9% clip
  - N: 5
  - lower(%): 20
  - upper(%): 100

* "mean-sigma-list"

  A set of "N" levels will be generated as "mean" plus multiples of "sigma" based on the "sigma list". For example, if mean = 1, sigma = 0.1, and sigma list = [-5, 5, 10, 15, 20], five levels will be generated as "0.5, 1.5, 2.0, 2.5, 3.0". Default parameters derived from full image statistics (per-channel) are:

  - mean: full image mean value
  - sigma: full image standard deviation
  - sigma list: [-5, 5, 9, 13, 17]

CARTA provides three different contour smoothing methods, including no smooth, Gaussian smooth, and block smooth, in the "Configuration" tab. The kernel for smoothing is in N by N pixels. The default is to apply Gaussian smooth with 4 by 4 pixels as the kernel size. Depending on science cases, users may choose different smooth methods and different kernel sizes. 

.. raw:: html

   <img src="_static/carta_fn_contourSmooth.png" 
        style="width:100%;height:auto;">

The appearance of contours can be customized in the "Styling" tab. As an example, users may use the options to plot contours like below. Iso-velocity contours are rendered in different colors to present Doppler shifts of the source kinematics.

.. raw:: html

   <img src="_static/carta_fn_contourStyling.png" 
        style="width:50%;height:auto;">



Viewing a position-velocity image
---------------------------------
When a position-velocity image is loaded as a raster image, CARTA switches to the mode of using *rectangular* pixels for rendering in order to have a better readability. The aspect ratio is flexible based on the aspect ratio of the image viewer widget. By default, the "spectral" axis is displayed in velocity if possible based on the image header. Users may use the image viewer settings to apply conversions to other spectral conventions, such as frequency or wavelength. In the video below, a demonstration of how to apply spectral conversion to a position-velocity image is provided. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_pv_rendering.mp4" type="video/mp4">
   </video>


.. _wcsmatching:

Match images in world coordinates
---------------------------------
When multiple images are loaded in the append mode, users may optionally trigger image matching based on their world coordinates. It is a common practice to compare images from different telescopes or even from the same telescope with different spectral and spatial setups. Users can use the "Matching" column of the "Image list widget" to trigger image matching process,  

.. raw:: html

   <img src="_static/carta_fn_layerList.png" 
        style="width:90%;height:auto;">

or the tool button in the image viewer.

.. raw:: html

   <img src="_static/carta_fn_triggerMatch.png" 
        style="width:40%;height:auto;">

The image list widget shows a list of all loaded images, including their:

* file name
* rendering type ("Layers" column): "R" means raster and "C" means contour
* image matching state ("Matching" column): 
   
  * "XY" means spatial domain
  * "Z" means spectral domain
  * "R" means the color range for raster rendering

* channel index
* Stokes index 

The first loaded image with valid spatial world coordinates serves as the default spatial reference and is highlighted with an open black box (e.g., HD163296_CO_2_1.image.mom0). Similarly, the first loaded image with valid spectral coordinates servers as the default spectral reference and is highlighted with an open black box (e.g., HD163296_CO_2_1.fits). To match world coordinates of other loaded images, users can click "XY" to match in the spatial domain and click "Z" to match in the spectral domain. If users would like to apply the same color range for different raster images, click "R" so that matched images will have the same color range with respect to the reference image highlighted with an open black box (e.g., HD163296_CO_2_1.image.mom0)

.. hint::
   Users may change a spatial reference image or a spectral reference image or a raster scaling reference by right-clicking a cell in the "Matching" column in the image list widget.

   .. raw:: html

      <img src="_static/carta_fn_layerList2.png" 
        style="width:90%;height:auto;">

For raster images, matching in the spatial domain is achieved by applying translation, rotation, and scaling to images with respect to the reference image. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_spatialMatching.mp4" type="video/mp4">
   </video>

For contour images, matching in the spatial domain is achieved by reprojecting contour vertices to the raster image in the view. Multiple contour images are displayed on top of a raster image if spatial matching is enabled. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_contourMatching.mp4" type="video/mp4">
   </video>

For image cubes, matching in the spectral domain is achieved by nearest interpolation in radio velocity. When spectral matching is enabled by clicking "Z", the matched channel and Stokes indices are shown in the image list widget. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_spectralMatching.mp4" type="video/mp4">
   </video>

.. note::
   Projection effects of raster images

   As raster images are matched spatially by applying translation, rotation, and scaling, projection effects between different images might be visible if images have a wide field of view and/or images have very different projection schemes. In the following video, projection effects in raster images are demonstrated. However, projection effects of contour images are properly handled in CARTA. Contours are reprojected with sufficient accuracy with respect to the raster image as seen in the image viewer by users.  

   .. raw:: html

      <video controls style="width:100%;height:auto;">
        <source src="_static/carta_fn_projectionEffect.mp4" type="video/mp4">
      </video>


.. note::
   If a spatial reference image or a spectral reference image is closed via "**File**" -> "**Close image**", all matched images will be unmatched and a new reference image will be automatically registered.


Raster image or contour image may be hidden in the image viewer by clicking "R" or "C" of the "Layers" column in the image list widget. For example, to create an image with contours only, users can click the "R" button to hide the raster image. 
 
.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_hideLayer.mp4" type="video/mp4">
   </video>

When multiple images are loaded in the append mode, their order determines the order in the image slider of the animator widget. With the image list widget, this order can be changed by dragging an entry to a desired place. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_reorderFrame.mp4" type="video/mp4">
   </video>





Changing image view
-------------------
CARTA provides different ways to change the image view. With a mouse, image zoom is achieved by scrolling up/down. Image pan is achieved by dragging or command+clicking (mac) or ctrl+clicking (linux). Alternatively, the image can be changed to fit the image viewer, or to fit the screen resolution (i.e., screen resolution equals full image resolution), by using the buttons at the bottom-right corner of the image viewer. Zoom in and zoom out buttons are provided as well.  To change to different images, channels, or stokes, please refer to the section :ref:`animator_intro`.

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_imageViewer_changeView.mp4" type="video/mp4">
   </video>

When an image is zoomed in or out, the precision of the coordinate tick values is dynamically adjusted based on the zoom level. 


Cursor information
------------------
When the cursor is on the image viewer, pixel information at the cursor position is shown at the top side of the image. The information includes:

* World coordinate of the current coordinate system. 
* Image coordinate in pixel (0-based).
* Pixel value.
* Frequency, velocity, reference frame (if applicable), and Stokes parameter (if applicable).


.. raw:: html

   <img src="_static/carta_fn_imageViewer_cursorInfo.png" 
        style="width:100%;height:auto;">

When the coordinate system is changed (e.g., ICRS to Galactic), the displayed world coordinate will be changed accordingly. By default, they are displayed in decimal degrees for Galactic and Ecliptic systems, while for FK5, FK4, and ICRS systems, they are displayed in sexagesimal format. The precision of both formats is determined dynamically based on the image header and image zoom level. 

The reference image coordinate (0,0) locates at the center of the bottom-left pixel of the image. Regardless of whether the displayed image is down-sampled or not, the image coordinate always refers to the full resolution image.

When the cursor is moving, the pixel value of the full resolution image is displayed. If the image header provides sufficient information in the frequency/velocity domain, the frequency and velocity with the reference frame of the current channel will be shown. If Stokes information is available in the image header, a Stokes parameter will be displayed as well.

To stop/resume cursor update, press "**F**" key. When the cursor stops updating, the cursor information bar, cursor spatial profiler, cursor spectral profiler will stop updating too. 



Configuring an image plot
-------------------------
CARTA provides flexible options to configure the appearance of an image plot. The image settings dialogue are accessible by clicking the "cog" at the top-right corner of the image viewer widget.

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_astOptions.mp4" type="video/mp4">
   </video>


As an example, below is an image with default overlay settings.

.. raw:: html

   <img src="_static/carta_fn_astOptions_before.png" 
        style="width:100%;height:auto;">

And, this is a customized one. The coordinate system has been switched from FK5 to Galactic. Font type, size, and color are customized, as well as the axis border and grid lines. 

.. raw:: html

   <img src="_static/carta_fn_astOptions_after.png" 
        style="width:100%;height:auto;">


The restoring beam is shown at the bottom-left corner, if applicable.

The image can be exported as a png image by clicking the "Export image" button at the bottom-right corner of the image viewer, or by "**File**" -> "**Export image**". By default a background layer in white or black, depending on the theme, will be added to the png file. If users prefer a transparent background, please go to "**File**" -> "**Preferences**" -> "**Global**" and set the "transparent image background" toggle to false. 


.. _animator_intro:

Animator
--------
The animator widget provides controls of image frames, channels, and stokes. When multiple images are loaded via **File** -> **Append image**, "Image" slider will show up and allow users to switch between different loaded images. If an image file has multiple channels and/or Stokes, "Channel" and/or "Stokes" slider will appear. The double slider right below the "Channel" slider allows users to specify a range of channels for animation playback. On the top there is a set of animation control buttons such as play, next, etc. Playback modes, including "forward", "backward", "Bouncing" and "Blink", are supported. Playback action will be applied to the slider with the activated radio button. 


.. raw:: html

   <img src="_static/carta_fn_animator_widget.png" 
        style="width:90%;height:auto;">



The frame rate spin box controls the *desired* frame per second (fps). The *actual* frame rate depends on image size and internet condition. Optionally, users can set a step for the animation playback (default as unity). By clicking the "Frame rate" dropdown, the "step" option will show up. 

When multiple images are loaded in the append mode, their order determines the order in the image slider of the animator widget. With the image list widget, this order can be changed by dragging an entry to a desired place. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_reorderFrame.mp4" type="video/mp4">
   </video>

