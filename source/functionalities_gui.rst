Functionality
=============
With version 1.3, CARTA provides the following widgets/dialogues for image view or analysis:

* Widget
  
  * image viewer: to view raster images
  * render configuration: to configure how a raster image is rendered
  * animator: to navigate through different images, different channels, or different Stokes
  * layer list: to configure image matching in world coordinates
  * region list: to view and configure region properties
  * spatial profiler: to view x and y spatial profiles at the cursor position
  * spectral profiler: to view spectral profile from a region of interest
  * histogram: to view histogram from a region of interest
  * statistics: to view basic statistics from a region of interest
  * Stokes analysis: to view basic polarization quantities
  * log: to view program logs

* Dialogue

  * file browser: to view image headers and to load an image
  * contour configuration: to configure how a contour image is rendered
  * file information: to view image headers
  * preferences: to configure user preferneces of the graphical user interface
  * overlay settings: to configure the appearance of an image in the image viewer

In addition, the server version of version 1.3 supports server authentication via the "Lightweight Directory Access Protocol" (LDAP). When using the server version, users can log in with their user name and password identical to the server hosting their images (either local or network storage). To share access of a given folder to collaborators, users can just change the permission via the "chmod" command. 

The support of the HDF5 image (IDIA schema) is further enhanced in verson 1.3. Rotated dataset and pre-calculated quantities, such as statistics or histograms, are properly utilized to enhance performance and user experience.  


Server-side status and session resume
-------------------------------------
As CARTA is fundamentally a client-server application, it would be good to know the status of the server side at the client side. This is also useful for the desktop version to know if the application runs normally or not. The server status is displayed as a circular icon at the top-right corner of the main window. The connection latency can be seen by hovering over the icon. There are three kinds of status:

* Green: this means that the server side is connected successfully.
* Orange: this means that the initial connection to the server side was broken (e.g., unstable internet) but has been reconnected. Users will asked to resume the previous session or not.  
* Red: this means that the server side is not accessible. CARTA is not functional in this case. 

.. raw:: html

   <img src="_static/carta_gui_server_status.png" 
        style="width:100%;height:auto;">

.. note::
   If CARTA behaves abnormally or stops responding, please check the server-side status icon and connection latency. If it becomes red, the connection between the client side and the server side is interrupted. At this point, CARTA is not funtional. When the connection is re-established automatically, the status icon becomes orange and a prompt will be shown to ask users wheater or not to resume the previous CARTA session. By clicking the OK button, CARTA will try to resume the previous session if possible. If users choose not to resume the previous session, please reload CARTA to establish a new session. Interacting with CARTA when the status icon is orange may lead to abnormal behaviors. 
   
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

Only the images matched these formats will be shown in the file list with image type and file size. When an image is selected, a brief summary of image properties is provided on the right side of the dialogue. Full header is also available in the second tab. To view an image, click the **Load** button at the bottom-right corner. To view a new image and close all the loaded images, use **File** -> **Open image** -> **Load** button. To view multiple images, use **File** -> **Append image** -> **Append** button.

.. raw:: html

   <img src="_static/carta_fn_fileBrowser.png" 
        style="width:100%;height:auto;">

File browser remembers the last path where an image was opened within one CARTA session and the path is displayed (breadcrumbs) at the top of the dialogue. Therefore, when the file browser is re-opened to load other images, a file list will be displayed at the last path where the previous image was loaded. Users can use the breadcrumbs to navigate to one of the parent directories or click the home button to navigate to the base (i.e., initial) directory directly. To get an updated file list from the server side, users can click the reload button.

For the CARTA-server application, the server administrator can limit the global directory access through the "*root*" keyword argument when launching the CARTA backend service. 

.. code-block:: bash

   exec carta_backend port=6002 base=/scratch/images/Orion root=/scratch/images

In the above example, users will see a list of images at the "*base*" directory "/scratch/images/Orion" when accessing the file browser dialogue for the first time in a new session. Users can navigate to any other folders inside "/scratch/images/Orion". By clicking the home button, users will navigate to the "*base*" directory "/scratch/images/Orion" directly. Users can also navigate one level up to "/scratch/images", but not beyond that (neither "/scratch" nor "/") as limited by the "*root*" keyword. 


.. note::
   An image might be closed via **File** -> **Close image**. The image currently displayed in the image viewer will be closed. If the image being closed is a WCS reference image, any other matched images to this reference image will be unmatched, thus they behave like individual images. See Section XXX for more information.  

.. note::
   Currently CARTA does not support the following types of images:

   * integer image
   * complex image
   * concatenated image
   * boolean image
   * componentlist image
   * image with uv coordinates
   * position-velocity image
   * LEL image 


.. tip::
   When using remote mode, an image may be opened directly using a modified URL. For example, if we wanted to open a remote image file "/home/acdc/CARTA/Images/jet.fits", we would append
     
   .. code-block:: bash 
     
      &folder=/home/acdc/CARTA/Images&file=jet.fits
        
   to the end of the URL (e.g., http://www.carta.edu:2000/?socketUrl=ws://www.carta.edu:3000). In this example our full URL is 
     
   .. code-block:: bash 
    
      http://www.carta.edu:2000/?socketUrl=ws://www.carta.edu:3000&folder=/home/acdc/CARTA/Images&file=jet.fits 
        
   Please note that it is necessary to give *full* path. Tilde (~) is not allowed.


HDF5 (IDIA schema) image support
--------------------------------
Except the CASA image format, the FITS format, and the MIRIAD format, CARTA also support images in the HDF5 format under the IDIA schema.  The IDIA schema is designed to ensure that efficient image visualization is retained even with extraordinary large image cubes (hundreds GB to a few TB). The HDF5 image file contains extra data to skip or to speed up expensive computations, such as per-cube histogram or spectral profile, etc. A brief outline of the content of an HDF5 image is provided below:

* XYZW dataset (spatial-spatial-spectral-Stokes): similar to the FITS format
* ZYXW dataset: rotated dataset
* per-channel statistics: basic statistics of the XY plane
* per-cube statistics: basic statistics of the XYZ cube
* per-channel histogram: histogram of the pixel values of the XY plane
* per-cube histogram: histogram of the XYZ cube

Additional tiled image data, which will speed up the process of loading very large images significantly, will be added to the HDF5 image file in v1.4. 

.. note::
   Currently per-plane beam is not handled properly when converting a FITS image to the HDF5 format. 


Image viewer
------------
Starting from v1.3, CARTA can display images in differnt ways, such as:

1. a single raster image
2. a single raster image plus its own contours
3. a single raster image plus a set of contour images with matched world coordinates from other image files 
4. a set of contour images without a background raster image

.. raw:: html

   <img src="_static/carta_fn_imageViewer_examples.png" 
        style="width:100%;height:auto;">

When an image is loaded in CARTA, it is shown as a raster image by default, such as the first example in the above figure. Users then could generate contour images (ref XXX) and enable WCS matching between different images (ref XXX), such as the other three examples above.

.. warning::
    If you are running a VNC session from a headless server, CARTA may fail to render images properly (they may appear as a solid color). This is due to the fact that CARTA renders images using WebGL which uses GPU to accelerate rendering process. Most headless servers have neither discrete nor dedicated GPUs. In such cases, it is highly recommended to use the "remote" mode of CARTA (see :ref:`commandLineStartup` for instructions).

In addition to displaying images, the image viewer displays cursor information at the top and provides a set of tool buttons at the bottom-right corner when hovering on the image. 

.. raw:: html

   <img src="_static/carta_fn_imageViewer_intro.png" 
        style="width:100%;height:auto;">

The tool buttons allow users to:

* create region of interests
* perform zoom or pan actions
* trigger matching images in world coordinates
* change reference coordinate grid lines and labels
* export image as a png file

.. raw:: html

   <img src="_static/carta_fn_imageViewer_toolButtons.png" 
        style="width:50%;height:auto;">

The aspect ratio of the image view is determined by the panel geometry. When the image viewer panel is resized, a tip with a ratio in screen pixel will be displayed (c.f., :ref:`resizing_a_panel` ).



Tiled rendering
^^^^^^^^^^^^^^^
CARTA utilizes an efficient approach, "tiled rendering", to display a raster image. What users see in the image viewer is an ensemble of tiles (default 256 pixel by 256 pixel) processed in parallel. As an example shown in the figure below, if we have an image with 2048 pixels by 2048 pixels, tiles will be constructed in four layers with differnt downsample factors. The zero-th layer contains only one tile with a size of 256 pixels by 256 pixels. A downsample factor of 8 is applied to the original image to create this tile. The first layer contains four tiles with each a size of 256 pixels by 256 pixels. The downsample factor of 4 is applied to the original image to create these four tiles. This process continues until no downsampling is required. In this case, the tiles of the third layer are not downsampled. As users change the field of view, or the size of the image viewer, tile data of the *right* layer will be used. For example, if a user is interested in the field of the blue box and the image viewer has a screen size of 512 pixels by 384 pixels, tiles of the layer 2 will be used for rendering. In this case, nine tiles will be used. If the user pans a little bit around the blue box, no new tile data are required. If the user pans the view to the green box with the same viewer size, only the additional two tiles of layer 2 are required and four tiles will be *re-used* for rendering. With this tiled rendering approach, tiles will be re-used for different zoom levels and different field of views to minimize the amount of data transfer while keeping the image sharp on screen. Effectively, users will see that the image becomes sharper and sharper at higher and higher zoom levels.


.. raw:: html

   <img src="_static/carta_fn_tiledRendering.png" 
        style="width:80%;height:auto;">

Below is a demonstration of tiled rendering in action. Note that the video clip is made under a special internet condition in order for users to see the process clearly. Normally images are rendered much faster.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_tiledRendering_demo.mp4" type="video/mp4">
   </video>


The performace of tiled rendering can be customized with the preferences dialogue, **File** -> **Preferences** -> **Performance**. The default values are chosen to assure raster images are displayed efficiently with sufficient accuracy. Advanced users may refine the setup if necessary. For example, when using the server version under poor internet condition, compression quality might be lowered down a bit to make the tile data smaller. Note that a smaller compression quality might introduce noticible artifacts on the raster image. Please adjust with caution. Alternatively, users may enable the low bandwidth mode, which will reduce required image resolutions by a factor of 2 (so that image will look a bit blurry) and cursor responsiveness from 200 ms to 400 ms (HDF5 images: from 100 ms to 400 ms). Under good internet conditions, users may enable streaming image tiles while zooming to see progressive updates of image resolutions at different zoom levels. 

.. raw:: html

   <img src="_static/carta_fn_tiledRendering_preference.png" 
        style="width:80%;height:auto;">


.. warning::
   To make remote visualization of large images possible and efficient, CARTA adopts the above mentioned tiled rendering approach together with an efficient image compression algorithm. At rare circumstance, artifacts may be seen on the images. A known issue is viewing an image with all pixels as zeros but one with a very high value. At low or default zoom level, some artifacts will be observed around that pixel. At higher zoom levels, the artifacts may disappear. CARTA has been tuned to localize the artifacts within few screen pixels in order to minimize the impact of scientific analysis on such special cases. The compression quality is adjustable via the preferences dialogue, **File** -> **Preferences** -> **Performance**. Advanced users may need to chose a higher compression quality for those special cases with caution. Should this become a problem in any kinds of analysis of yours, please contact `carta_helpdesk`_ for help.

   .. _carta_helpdesk: carta_helpdesk@asiaa.sinica.edu.tw


.. note::
   CARTA image loading performance

   The per-channel rendering approach helps to improve the performance of loading an image significantly. Traditionally when an image is loaded, the minimum and maximum of the entire image (cube) are computed first before image rendering. This becomes a serious performance issue if the image (cube) size is extraordinary large (> several GB). In addition, applying the global minimum and maximum to render a raster image usually (if not often) results in a poorly rendered image if the dynamical range is high. Then users need to re-render the image repeatedly with refined boundary values. Re-rendering such a large image repeatedly further deduces user experiences.

   CARTA hopes to improve the image viewing experience by adopting GPU accelerated rendering with web browser technology. In addition, CARTA only renders an image with just enough image resolution (tiles and down-sampling). This combination results in a scalable and high-performance remote image viewer. The total file size is no longer a bottleneck. The determinative factors are: 1) image size in x and y dimensions, 2) internet bandwidth, and 3) storage I/O, instead. For a laptop with 8 GB of RAM, the largest image it can load without swapping is about 40000 pixels by 40000 pixels (assuming most of the RAM are free before loading image). 

   The approximated RAM usage of loading images with various spatial sizes is summarized below.
   
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
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The render configuration widget controls how a raster image is rendered in the image viewer. On the top, there is a row of buttons with different clip levels plus a custom button. Below there is a plot showing the per-channel histogram (in logarithmic scale) with a bin count equals to the geometric mean of the image size (x and y). The two vertical red bars indicate the two clip values of a colormap. The green dashed line marks the mean value and the green box marks the range from mean - one standard deviation to mean + one standard deviation. Interaction with a chart, such as the histogram, is demonstrated in the section :ref:`mouse_interaction_with_charts`. On the right, there is a column of options, such as histogram type, scaling function, color map, invert color map, clip values, and control parameter of a scaling function (if applicable). Extra options to configure the histogram plot are placed in the render configuration settings dialogue enabled by the cog icon at the top-right corner of the render configuration widget. The histogram can be exported as a png image or a text file in tsv format.

By default, CARTA calculates per-channel histogram. When per-cube histogram is requested, a warning message and a progress dialogue will show up. Calculating a per-cube histogram can be time-consuming for large image cubes. Users may cancel the request at any time by pressing the cancel button in the progress dialogue. If the image is in the HDF5 format (IDIA schema), the pre-calculated per-cube histogram will be loaded directly and displayed mostly instantly. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_renderConfig_widget.mp4" type="video/mp4">
   </video>

CARTA determines the boundary values of a colormap on **per-channel** basis by default. That is, a default "99.9%" clip level is applied to the per-channel histogram to look for the two clip values. Then apply the values in "linear" scale to the default colormap "inferno" to render a raster image. This helps to inspect an image in detail without suffering from improper image rendering in most of cases. Below is an example of this per-channel rendering approach.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_renderConfig_perFrame.mp4" type="video/mp4">
   </video>

However, when comparing images channel by channel, color scales need to be fixed. This can be easily achieved by dragging the two vertical red bars, or typing in the values. When this happens, the "custom" button is enabled automatically and *all* frames will be rendered with the fixed boundary values. By clicking one of the clip buttons, CARTA switches back to the per-frame rendering mode *if per-channel histogram is requested*. Users may request the per-cube histogram to determine proper clip values. Below is an example of custom rendering with the per-cube histogram. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_renderConfig_perCustom.mp4" type="video/mp4">
   </video>

CARTA provides a set of scaling functions, such as:

* linear: :math:`y = x`
* log: :math:`y = {\log}_{\alpha}({\alpha}x+1)`
* square root: :math:`y = {\sqrt{x}}`
* squared: :math:`y = x^2`
* gamma: :math:`y = x^{\gamma}`
* power: :math:`y = ({\alpha}x-1)/{\alpha}`

A set of colormaps adopted from `matplotlib <https://matplotlib.org/tutorials/colors/colormaps.html?highlight=colormap>`_ is provided in CARTA.

.. raw:: html

   <img src="_static/carta_fn_renderConfig_colormaps.png" 
        style="width:100%;height:auto;">

The default scaling function, colormap, percentile rank, and a color for NaN pixels can be customized via the menu **File** -> **Preferences** -> **Render Configuration**.

.. raw:: html

   <img src="_static/carta_fn_renderConfig_preferences.png" 
        style="width:80%;height:auto;">



Contour rendering
^^^^^^^^^^^^^^^^^
In addition to raster rendering, CARTA supports contour rendering as well. A contour image layer can be created on the same raster image or on a different raster image with world coordiantes properly matched. The contour generation process is achieved with the contour configuration dialogue which can be launched via the main tool bar.

.. raw:: html

   <img src="_static/carta_fn_contourConfig.png" 
        style="width:65%;height:auto;">

Users may follow the following steps to generate a contour image:

1. Define contour levels. There are several ways to define a set of contour levels to be calculated at the server side:
  
  a. by typing in individual level in the "Levels" field 
  b. by using the "Generator" to generate a series of levels
  c. by clicking directly on the histogram plot to create levels (right-click on an existing level to remove)

  Note that the "Levels" field is editable even if a set of levels has been generated with the level generator. 

2. (optional) Define a smooth scheme and a kernel size in the "Configuration" tab. The default is Gaussian smooth with a kernel size of four pixels. 

3. (optional) Define the appearance of contours to be rendered at the client side in the "Styling" tab. The appearance of contours can be modified after a set of contours has been rendered without triggering new contour calculations at the server side. This is the advantage of utilizing WebGL at the client side. 

Once a set of levels has been defined, users can click the "Apply" button to visualize the contour image. Contour image is rendered progressively.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_contourRendering.mp4" type="video/mp4">
   </video>

In the above demostration, a contour image is generated on top of its raster image. If users would like to plot a contour image on top of other raster image (e.g., CO 2-1 image as contour, 1 mm continuum image as raster), users need to enable WCS matching of the two raster images first (Section XXX). Then users can generate the contour image just like the above example. When the contour image is generated, use the layer list widget or the animator widget to switch to the 1 mm continuum image. Users should see the CO 2-1 contour image on top of the 1 mm continuum raster image. In short, contour images are visible for raster images matched in world coordinates. 


**ADD VIDEO!!!**


If there are multiple images loaded in append mode, users may use the "Data Source" dropdown to select an image as the data source of contour calculations. If the state of the "lock" button is locked, image viewer will show the selected image as a raster image and the frame slider in the animator widget will be updated to the selected image too. To disable this synchronization, click the "lock" button to set the state to unlock. 

CARTA provides four different level geneators to assist users to construct a set of contour levels. 

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

CARTA provides three different contour smoothing methods, including no smooth, Gaussian smooth, and block smooth, in the "Configuration" tab. The kernel for smoothing is in number of pixels. The default is to apply Gaussian smooth with four pixels as the kernel size. Depending on science cases, users may choose different smooth methods and differnt kernel sizes. 

.. raw:: html

   <img src="_static/carta_fn_contourSmooth.png" 
        style="width:100%;height:auto;">

The appearance of contours can be customized in the "Styling" tab. As an example, users may use the options to plot contours like below. Iso-velocity contours are rendered in different colors to present Doppler shifts of the source kinematics.

.. raw:: html

   <img src="_static/carta_fn_contourStyling.png" 
        style="width:50%;height:auto;">


Match images in world coordinates
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When multiple images are loaded in the append mode, users may optionally trigger image matching based on their world coordinates. It is a common practice to compare images from different telescopes or even from the same telescope with different spectral and spatial setups. Users can use the "Layer list widget" to trigger image matching process,  

.. raw:: html

   <img src="_static/carta_fn_layerList.png" 
        style="width:70%;height:auto;">

or the tool button in the image viewer.

.. raw:: html

   <img src="_static/carta_fn_triggerMatch.png" 
        style="width:40%;height:auto;">

The layer list widget lists up all load images, including their:

* file name
* rendering type ("Type"): "R" means raster and "C" mean contour
* image matching state ("Matching"): "XY" means spatial domain and "Z" means spectral domain. 
* channel index
* Stokes index 

The first loaded image with valid spatial world coordinates serves as the spatial reference and is highlighted with an open black box (e.g., HD163296_CO_2_1.image.mom0). Similarly, the first loaded image with valid spectral coordinates servers as the spectral reference and is highlighted with an open black box (e.g., HD163296_CO_2_1.fits). To match world coordinates of other loaded image, users can click "XY" to match in the spatial domain and click "Z" to match in the spectral domain. 

For raster images, matching in the spatial domain is achieved by applying translation, rotation, and scaling to images with respect to the reference image. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_spatialMatching.mp4" type="video/mp4">
   </video>

For contour images, matching in the spatial domain is achieved by reprojecting contour vertices to the raster image in the view. Multiple contour images are displayed on top of a raster image if spatial matching is enabled. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_contourMatching.mp4" type="video/mp4">
   </video>

For image cubes, matching in the spectral domain is achieved by nearest interpolation in radio velocity. When spectral matching is enabled by clicking "Z", the matched channel and Stokes indices are shown in the layer list widget. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_spectralMatching.mp4" type="video/mp4">
   </video>

.. note::
   Animation playback does not work properly with spectrally matched cubes in v1.3. This will be improved in v1.4.

.. hint::
   Users may change spatial or spectral reference image by right-clicking a cell in the "Matching" column in the layer list widget.

.. note::
   If spatial reference image or spectral reference image is closed via "**File**" -> "**Close image**", all matched images will be unmatched and a new reference image will be automatically registered.

Raster image or contour image may be hidden in the image viewer by clicking "R" or "C" in the layer list widget. For example, to create an image with contours only, users can click the "R" button to hide the raster image. 
 
.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_hideLayer.mp4" type="video/mp4">
   </video>

When multiple images are loaded in the append mode, their order determines the order in the frame slider of the animator widget. With the layer list widget, this order can be changed by dragging an entry to a desired place. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_reorderFrame.mp4" type="video/mp4">
   </video>





Changing image view
^^^^^^^^^^^^^^^^^^^
CARTA provides different ways to change the image view. With a mouse, image zoom is achieved by scrolling up/down. Image pan is achieved by dragging or command+clicking (mac) or ctrl+clicking (linux). Alternatively, image can be changed to fit the image viewer, or to fit the screen resolution (i.e., screen resolution equals full image resolution), by using the buttons at the bottom-right corner of the image viewer. Zoom in and zoom out buttons are provided as well.  To change to different frames, channels, or stokes, please refer to the section :ref:`animator_intro`.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_imageViewer_changeView.mp4" type="video/mp4">
   </video>

When an image is zoomed in or out, the precision of the coordinate tick values is dynamically adjusted based on the zoom level. 


Cursor information
^^^^^^^^^^^^^^^^^^
When the cursor is on the image viewer, pixel information at the cursor position is shown at the top side of the image. The information includes:

* World coordinate of the current coordinate system. 
* Image coordinate in pixel.
* Pixel value.
* Frequency, velocity, and reference frame (if applicable).


.. raw:: html

   <img src="_static/carta_fn_imageViewer_cursorInfo.png" 
        style="width:100%;height:auto;">

When the coordinate system is changed (e.g., ICRS to Galactic), the displayed world coordinate will be changed accordingly. By default, they are displayed in decimal degrees for Galactic and Ecliptic systems, while for FK5, FK4, and ICRS systems, they are displayed in sexagesimal format. The precision of both formats is determined dynamically based on the image header and image zoom level. 

The reference image coordinate (0,0) locates at the center of the bottom-left pixel of the image. Regardless the displayed image is down-sampled or not, the image coordinate always refers to full resolution image.

When cursor is moving, pixel value of the full resolution image is displayed. If image header provides sufficient information in the frequency/velocity domain, the frequency and velocity with the reference frame of the current channel will be shown.

To stop/resume cursor update, press "**F**" key. When the cursor stops updating, the cursor information bar, cursor spatial profiler, cursor spectral profiler will stop updating too. 



Configuring an image plot
^^^^^^^^^^^^^^^^^^^^^^^^^
CARTA provides flexible options to configure the appearance of an image plot. The overlay settings are accessible via "**View**" -> "**Overlay**" -> "**Customize**".

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
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

The image can be exported as a png image by clicking the "Export image" button at the bottom-right corner of the image viewer, or by "**File**" -> "**Export image**".


.. note::
   Currently displaying beams of a cube with per-plane-beam is not supported.  


.. _animator_intro:

Animator
--------
The animator widget provides controls of image frames, channels, and stokes. When multiple images are loaded via **File** -> **Append image**, "Frame" slider will show up and allows users to switch between different loaded images. If an image file has multiple channels and/or stokes, "Channel" and/or "Stokes" slider will appear. The double slider right below the "Channel" slider allows users to specify a range of channels for animation playback. On the top there is a set of animation control buttons such play, next, etc. Playback modes, including "forward", "backward", "Bouncing" and "Blink", are supported. Playback action will be applied to the slider with the activated radio button. As an example below, the action will be applied to the *channel* axis of the second stokes axis of the third image file, and the animation range is from the second channel to the last channel. 


.. raw:: html

   <img src="_static/carta_fn_animator_widget.png" 
        style="width:80%;height:auto;">



The frame rate spin box controls the *desired* frame per second (fps). The *actual* frame rate depends on image size and internet condition. 

.. note::
   Step for animation playback will be added in future releases. Currently the step is unity. 


Region of interest
------------------
As of v1.3, CARTA supports the following region types:

* rectangle (rotatable)
* ellipse (rotatable)
* square (rotatable; as a special case of rectangle; "**shift**" key + drag)
* circle (as a special case of ellipse; "**shift**" key + drag)
* point
* polygon


The creation and modification of regions are demonstrated in the section :ref:`mouse_interaction_with_regions`. To create a region, use the region button at the bottom-right corner of the image viewer, then use cursor to draw a region. CARTA allows regions to be created even if the region is outside the image. Keyboard shortcuts associated with regions are listed below.

+----------------------------------+----------------------------+-----------------------------+
|                                  | macOS                      | Linux                       |
+==================================+============================+=============================+
| Region properties                | double-click               | double-click                | 
+----------------------------------+----------------------------+-----------------------------+
| Delete selected region           | del / backspace            | del / backspace             |
+----------------------------------+----------------------------+-----------------------------+
| Toggle region creation mode      | C                          | C                           |
+----------------------------------+----------------------------+-----------------------------+
| Deselect region                  | esc                        | esc                         |
+----------------------------------+----------------------------+-----------------------------+
| Switch region creation mode      | cmd + drag                 | ctrl + drag                 |
+----------------------------------+----------------------------+-----------------------------+
| Symmetric region creation        | shift + drag               | shift + drag                |
+----------------------------------+----------------------------+-----------------------------+
| Pan image (inside region)        | cmd + click / middle-click | ctrl + click / middle-click |
+----------------------------------+----------------------------+-----------------------------+
| Toggle current region lock       | L                          | L                           |
+----------------------------------+----------------------------+-----------------------------+
| Unlock all regions               | shift + L                  | shift + L                   |
+----------------------------------+----------------------------+-----------------------------+

.. tip::
  "**backspace**" does not delete a region...

  If using CARTA remote mode in Firefox on MacOS, you may find the "**backspace**" key navigates back a page instead of removing a region. This behaviour can be prevented by modifying your Firefox web browser settings:

  1. Enter about:config in the address bar.
  2. Click "I accept the risk!"
  3. A search bar appears at the top of a long list of preferences. Search for "browser.backspace_action"
  4. It will likely have a value of 0. Double click it, and then modify it to a value of "2".
  5. Close the about:config tab and now backspace will no longer navigate back a page.

All created regions are listed in the region list widget with basic region properties. To select a region (region state changes to "selected"), simply click on the region in the image viewer, or click on the region in the region list widget. To modify the properties of a selected region, double-click on a region in the image viewer or a region in the region list widget. The color, line style, name, location, and shape, of a region are all configurable with the region property dialogue. To de-select a region, press "**esc**" key. To delete a selected region, press "**delete**" or "**backspace**" key. The activated region can be locked by pressing "**L**" key or by clicking the "lock" icon in the region list widget or region property dialogue. When a region is locked, it cannot be modified (resize, move, or delete) with mouse actions and the "**delete**" or "**backspace**" key. A locked region, however, can still be modified or delected via the region property dialogue. Locking a region could help the stituation when users want to modify overlapping regions, or could prevent modifying a region accidentally. The "eye" icon is to show the corresponding region at the center of image view. 

.. raw:: html

   <img src="_static/carta_fn_roi.png" 
        style="width:100%;height:auto;">


CARTA checks if a polygon is simple or complex. If a polygon is detected as complex, its color will be in pink as a warning. Spectral profile, statistics, or histogram of a complex polygon can still be requested. However, the outcome may be beyond users' expectation. The enclosed pixels depend on *how* a complex polygon is constructed. Please use complex polygon with caution. 

Region of interest enables practical image cube analysis through statistics, histogram, and spectral profiler widgets. When a region is selected, the region associated widgets will be highlighted with a persistent blue box as demonstrated below.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_roi_widgetHighlight.mp4" type="video/mp4">
   </video>



As of v1.3, CARTA supports basic region import and export capability. Regions, in world coordinate or in image coordinate, can be exported to a text file or imported from a text file. To import a region file, use the menu **File** -> **Import regions**. 

.. raw:: html

   <img src="_static/carta_fn_regionImport.png" 
        style="width:100%;height:auto;">

To export regions to a region file, use the meun **File** -> **Export regions**. All regions, except cursor, will be exported. 

.. raw:: html

   <img src="_static/carta_fn_regionExport.png" 
        style="width:100%;height:auto;">

As of v1.3, CASA region text format (.crtf) and ds9 region text formate (.reg) are supported with some limitations. Currently only the 2D region defination is supported. Other properties, such as spectral range, reference frame, or decoration (line style, line width, etc.) will be supported in future releases.  

The currently supported CRTF region syntax is summerized below:

* Rectangle

  * box[[x1, y1], [x2, y2]]
  * centerbox[[x, y], [x_width, y_width]]
  * rotbox[[x, y], [x_width, y_width], rotang]

* Ellipse

  * circle[[x, y], r]
  * ellipse[[x, y], [bmaj, bmin], pa]

* Polygon

  * poly[[x1, y1], [x2, y2], [x3, y3], ...]

* Point

  * symbol[[x, y], .]

Please refer to https://casa.nrao.edu/casadocs/casa-5.6.0/imaging/image-analysis/region-file-format for more detailed descriptions about the CRTF syntax. 


The currently supported ds9 region syntax is summerized below:

* Rectangle

  * box x y width height angle

* Ellipse

  * ellipse x y radius radius angle
  * circle x y radius

* Polygon

  * polygon x1 y1 x2 y2 x3 y3 ...

* Point

  * point x y

Please refer to http://ds9.si.edu/doc/ref/region.html for more detailed descriptions about the ds9 region syntax. 


Spatial profiler
----------------
Spatial profiler provides the spatial profiles of the current image at the cursor position. When the cursor is moving on the image, profiles derived from the full resolution raster image are displayed. The "F" key will disable or enable profile update. When cursor update is disabled, a marker "+" will be placed on the image to indicate the position of the profiles taken. 

When displaying a spatial profile with the number of pixels more than the number of screen pixels of the spatial profiler widget, a *decimated* profile will be derived and displayed to users as an enhancement of performance. Min/max decimation of a profile is adopted to ensure profile features are preserved. In other words, positive and negative peaks should stay at the same screen pixels just like displaying the full resolution profile. When users keep zooming in the profile, decimation with narrower and narrower interval is applied dynamically. Full resolution profile is displayed when the number of screen pixels is more than the number of pixels of the profile to be displayed.  

The interactions of the spatial profiler widget are demonstrated in the section :ref:`mouse_interaction_with_charts`. The red vertical bar indicates the pixel where the profile is taken. The bottom axis shows the image coordinate, while optional world coordinate is displayed on the top axis. Extra options to configure the profile plot are available to the right border. The option "Show Mean/RMS" will adopt the data in the current view to derive a mean value and an rms value, and visualize the results on the plot. Numerical values are also displayed at the bottom-left corner. The profile can be exported as a png image or a text file in tsv format via the buttons at the bottom-right corner.

When the cursor is on the image in the image viewer, the pointed pixel value (pixel index and pixel value) will be displayed at the bottom-left corner of the spatial profiler. When the cursor is on the spatial profiler graph, the pointed profile data will be displayed instead. 

.. raw:: html

   <img src="_static/carta_fn_spatialProfiler_widget.png" 
        style="width:100%;height:auto;">


.. note::
   More flexibilities on how mean and rms values are derived will be provided in future releases. Profile fitting capability will be available in future releases.   


Spectral profiler
-----------------
Spectral profiler provides the spectral profile of the current image cube at the selected region. The default region is set to "Cursor". The "**F**" key will disable or enable cursor profile update. When cursor update is disabled, a marker "+" will be placed on the image to indicate the position of the profile taken. 

When requesting a spectral profile, a common disappointing user experience is that users may have to wait for an unknown amount of time to see the final result if the image cube is large. As an improvement on this aspect, CARTA supports *partial update* of spectral profile. Partial profiles will be periodically delivered to users while the full profile calculations are still ongoing. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_spectralProfiler_partialUpdate.mp4" type="video/mp4">
   </video>


When the property of a region (cursor or a regular region) is modified while the profile of the original region is being updated, the partial profile will disappear and a new partial profile cooresponding to the new region will start updating. If users modify the request of a spectral profile via the spectral profile widget before it is fully delivered, the original profile calculations will be cancelled and new profile calculations will start. In short, now CARTA should just focus on calculating and showing the profiles that users pay attention to. If a profile is no longer needed to be shown on the screen, the profile calculation will be cancelled immediately, instead of blocking and queueing up new profile requests. 


.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_spectralProfiler_profileCancellation.mp4" type="video/mp4">
   </video>


When displaying a spectral profile with the number of channels more than the number of screen pixels of the spectral profiler widget, a *decimated* profile will be derived and displayed to users as an enhancement of performance. Min/max decimation of a profile is adopted to ensure profile features are preserved. In other words, positive and negative peaks should stay at the same screen pixels just like displaying the full resolution profile. When users keep zooming in the profile, decimation with narrower and narrower interval is applied dynamically. Full resolution profile is displayed when the number of screen pixels is more than the number of pixels of the profile to be displayed. 

When regions are created, the spectral profiler widget can be configured to display a profile from a specific region with the "*region*" dropdown menu. Additional statistic types to compute the region spectral profile are available with the "*statistic*" dropdown menu (default to mean). If the image cube has multiple Stokes, the "*Stokes*" dropdown menu will be activated and defaulted to "current" which is synchronized with the selection in the animator. To view a specific Stokes, select with the "*Stokes*" dropdown menu.


Multiple spectral profile widgets can be configured to display different region spectral profiles. The widget with the selected region will be highlighted with a persistent blue box.

.. raw:: html

   <img src="_static/carta_fn_spectralProfiler_multiwidget.png" 
        style="width:100%;height:auto;">


The interactions of the spectral profiler widget are demonstrated in the section :ref:`mouse_interaction_with_charts`. The red vertical bar indicates the channel of the image displayed in the image viewer. Clicking directly on the spectral profiler graph will change the displayed image to the clicked channel. Alternatively, the red vertical bar is draggable and acts just like the animator slider. 

The bottom axis shows the spectral coordinate, while optional channel coordinate can be displayed instead. Extra options to configure the profile plot are available to the right border. The option "Show Mean/RMS" will adopt the data in the current view to derive a mean value and an rms value, and visualize the results on the plot. Numerical values are also displayed at the bottom-left corner. When the cursor is on the image in the image viewer, the pointed pixel value (frequency or velocity or channel index, and pixel value) will be displayed at the bottom-left corner of the spectral profiler. When the cursor is on the spectral profiler graph, the pointed profile data will be displayed instead. The profile can be exported as a png image or a text file in tsv format via the buttons at the bottom-right corner.


.. raw:: html

   <img src="_static/carta_fn_spectralProfiler_widget.png" 
        style="width:100%;height:auto;">


.. note::
   More flexibilities on how mean and rms values are derived will be provided in future releases. Enhancement of the spectral profile widget will be available in future releases.


Stokes analysis widget
----------------------
Stokes analysis widget allows users to view basic polarization quantities of a multi-channel (number of channel > 1), multi-Stokes (IQU or IQUV) cube efficiently. The widget includes the following plots:

* Stokes Q intensity and Stokes U intensity over the spectral axis
* Linearly polarized intensity over the spectral axis
* Linear polarization angle over the spectral axis
* Stokes Q intensity versus Stokes U intensity

The profiles can be zoomed and panned with mouse similar to the spatial profile widget or the  spectral profile widget (:ref:`mouse_interaction_with_charts`). The Stokes Q versus Stokes U scatter plot is color-encoded from red to blue with increasing frequencies. The profiles can be requested at the cursor position (single pixel) or over a region of interest. Fractional polarization quantities are also supported. Examples are given in the following figures. The first one is from real ALMA data, while the second one is from an artifical Stokes cube. 

.. raw:: html

   <img src="_static/carta_fn_Stokes_widget.png" 
        style="width:100%;height:auto;">


.. raw:: html

   <img src="_static/carta_fn_Stokes_widget2.png" 
        style="width:100%;height:auto;">


Statistics widget
-----------------
Statistics widget allows users to see statistics with respect to a selected region. The "Region" dropdown menu can be used to select which region statistics to be displayed. The default is "Image" which means the entire image of the displayed channel is adopted to compute statistics. Multiple statistics widgets can be created to display statistics of different regions as demonstrated below. The widget with the selected region will be highlighted with a persistent blue box. 

.. raw:: html

   <img src="_static/carta_fn_statistics_widget.png" 
        style="width:100%;height:auto;">

.. note::
   Flux density (Jy) will be supported in a patch release before v1.3.


Histogram widget
----------------
Histogram widget allows users to visualize data in a histogram with respect to a selected region. The "Region" dropdown menu can be used to select which region histogram to be displayed. The default is "Image" which means the entire image of the displayed channel is adopted to construct a histogram. Multiple histogram widgets can be created to display histograms of different regions as demonstrated below. The widget with the selected region will be highlighted with a persistent blue box.

.. raw:: html

   <img src="_static/carta_fn_histogram_widget.png" 
        style="width:100%;height:auto;">

.. note::
   With v1.2, histogram bin width and bin count are automatically decided. Enhancement of the histogram widget, including histogram fitting, will be available in future releases. 
