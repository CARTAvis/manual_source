Image cube analysis tools
=========================
With version 4.0.0, CARTA provides the following widgets and tools for image cube analysis:

* Widget
  
  * Region List Widget: to view and configure region properties
  * Spatial Profiler Widget: to view x or y spatial profile at the cursor position
  * Spectral Profiler Widget: to view one or multiple spectral profiles
  * PV Generator Widget: to generate a position-velocity slice of a cube
  * Histogram Widget: to view histogram from a region of interest
  * Statistics Widget: to view basic statistics from a region of interest
  * Stokes Analysis Widget: to view fundamental polarization quantities (e.g., polarized intensity and angle)
  * Spectral Line Query Widget: to make a query to the Splatalogue service and create labels on a spectral profile plot
  * Cursor Info Widget: to view image pixel information from all matched images at the cursor position
  * Catalog Widget: to visualize a catalog as an image overlay, a 2D scatter plot, or a histogram


* Tool

  * File Header Dialog: to display a summary of the image file and the full image header
  * Profile Smoothing Dialog: to smooth a spectral or spatial profile for a better S/N
  * Moment Map Generator Dialog: to collapse an image cube with various moments and statistics
  * Spectral Profile Fitting Dialog: to fit an observed spectrum with a model profile
  * Image Fitting Dialog: to fit an image with multiple 2D Gaussian models
  * Distance Measurement Dialog: to compute a geodesic distance on the image
  * Online Catalog Query Dialog: to retrieve remote catalogs from SIMBAD or VizieR


File Header
-----------
Using the File Header Dialog, you can view a summary or full header of an image file. To search for a keyword, click the "**search**" button in the header tab. If you want to save the file header as a text file, use the "**export**" button.

.. raw:: html

   <img src="_static/carta_fn_fileHeader.png" 
        style="width:80%;height:auto;">

Region of interest
------------------
As of v4.0.0, CARTA supports the following region types:

* rectangle (rotatable)
* ellipse (rotatable)
* square (rotatable; as a special case of rectangle; "**shift**" key + drag)
* circle (as a special case of ellipse; "**shift**" key + drag)
* point
* polygon
* line (rotatable)
* polyline

The creation and modification of regions are demonstrated in the section :ref:`mouse_interaction_with_regions`. To create a region, use the region button from the toolbar at the bottom-right corner of the Image Viewer or use the region buttons from the region bar at the top of the GUI, then use the cursor drag-and-drop action to draw a region. CARTA allows regions to be created even if the region is outside the image. Keyboard shortcuts associated with regions are listed below.

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
| Pan image (inside region)        | cmd + click / middle-click | ctrl + click / middle-click |
+----------------------------------+----------------------------+-----------------------------+

.. tip::
  "**backspace**" does not delete a region...

  If using CARTA remote mode in Firefox on macOS, you may find the "**backspace**" key navigates back a page instead of removing a region. This behavior can be prevented by modifying your Firefox web browser settings:

  1. Enter about:config in the address bar.
  2. Click "I accept the risk!"
  3. A search bar appears at the top of a long list of preferences. Search for "browser.backspace_action"
  4. It will likely have a value of 0. Double-click it, and then modify it to a value of "2".
  5. Close the about:config tab, and now backspace will no longer navigate back a page.

All created regions are listed in the Region List Widget with basic region properties. To select a region (region state changes to "active"), click on the region in the Image Viewer or the region in the Region List Widget. 

To modify the properties of a selected region, double-click on a region in the Image Viewer or a region in the Region List Widget to bring up the Region Configuration Dialog. A region's color, line style, name, location, and shape are all configurable with the Region Configuration Dialog. The location and shape properties can be edited in the image coordinates or in the world coordinates with angular scales (default). 

To de-select a region or cancel a region creation process, press the "**esc**" key. Press the "**delete**" or "**backspace**" key to delete a selected region. 

An active region can be locked by pressing the "**L**" key or clicking the "**lock**" button in the Region List Widget or region property dialog. You may lock all regions at once by clicking the "**lock**" button in the top-left corner of the Image List Widget. When a region is locked, it cannot be modified (resize, move, or delete) with mouse actions and the "**delete**" or  "**backspace**" key. A locked region, however, can still be modified or deleted via the Region Configuration Dialog. Locking a region could help the situation when you want to modify overlapping regions or prevent accidentally modifying a region. 

The "**focus**" button is to show the corresponding region at the center of the image view. Suppose you have many regions blocking the image view. In that case, you may temporarily reduce the opacity of the regions or hide all the regions by clicking the "**hide**" button in the top-left corner of the Image List Widget.

.. raw:: html

   <img src="_static/carta_fn_roi.png" 
        style="width:100%;height:auto;">

CARTA checks if a polygon is *simple* or *complex*. If a polygon is detected as *complex* (i.e., polygon line segments intersect), its color will become pink as a warning. Spectral profile, statistics, or histogram of a complex polygon can still be requested. However, the outcome may be beyond your expectations. The enclosed pixels depend on *how* a complex polygon is constructed. Please use complex polygons with caution. 

The coordinate reference system can be changed with the dropdown menu when editing region properties in the world coordinates. The default reference system is the one defined in the image header and is the same as the one defining the grid line overlay in the Image Viewer. When you switch to a different reference frame, the Image Viewer's grid line overlay is also changed. The coordinate is in sexagesimal format if the reference system is ICRS, FK5, or FK4. The coordinate is in decimal degrees if the reference system is GALACTIC or ECLIPTIC. The region size property can be defined in arcsecond with :code:`"`, in arcminute with :code:`'`, or in degrees with :code:`deg`.



Shared region with conserved solid angle
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When a region is created on one of the spatially matched images, effectively, the region is created on the image served as the spatial reference. Then, the region is *shared* and rendered to other spatially matched images considering projection effects and differences in coordinate reference systems. Under the scene, regions (except the point region) are approximated by polygons with many control points. Each control point is transformed from the spatial reference image to the spatially matched secondary image. In this way, the solid angles of the regions before and after polygonal approximation are nearly identical; thus, analytics of the *same* region among different spatially matched images can be compared directly. 

In the following exaggerated example, two images with different coordinate systems and projection schemes are spatially matched. Regions on the spatial reference image retain their shapes. Depending on the projection schemes, polygon-approximated regions on the spatially matched secondary image may have visible distortions. In most use cases, the region distortion effect should be much less noticeable if the field of view of the image is small.

.. raw:: html

  <img src="_static/carta_fn_roi_sharedRegion.png" 
      style="width:100%;height:auto;">


Shared line/polyline region with conserved angular length
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Like the polygon approximation of closed regions, the line and polyline regions are approximated as a polyline with many control points on the spatially matched secondary image. In this way, the angular length of the trajectory traced by the line or polyline region before and after polyline approximation is nearly identical. 

.. raw:: html

  <img src="_static/carta_fn_roi_sharedRegion2.png" 
      style="width:100%;height:auto;">

When a spatial profile is derived from a line or a polyline region, a set of boxes with a "height" (parallel to the trajectory) of three unit steps and a custom "width" (perpendicular to the trajectory) in the number of unit steps are created along the trajectory. These *hidden* boxes are created on the reference image first. Then, similar to the polygon approximation of closed regions, these "boxes" are transformed into the spatially matched secondary image to derive a spatial profile. The unit step refers to an image pixel if the image is “flat” without noticeable distortion. However, if the image is considered "wide" with noticeable distortion, the unit step refers to the angular size of an image pixel as defined in the image header. In this case, the boxes retain approximately a fixed solid angle. All these approximations allow spatial profiles of the same trajectory among different spatially matched images to be compared directly. The same idea is applied to the position-velocity image generator with a line region.


Shared region management
^^^^^^^^^^^^^^^^^^^^^^^^
When regions are created on one of the spatially matched images, they are *all* registered to the spatial reference image for matching. The regions are shared with all the matched images; thus, analytics can be derived and compared directly. When an image is unmatched from the spatial reference image, the image will get a copy of all regions. This set of regions is now independent of the region set belonging to the matched images. Suppose there are modifications of the regions, and you try to match the image to the matched images again. In that case, only those modified regions will be copied to the region set of the matched images. The following diagram illustrates the idea.

.. raw:: html

  <img src="_static/carta_fn_roi_sharedRegion_management.png" 
      style="width:100%;height:auto;">

Analytics with shared regions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Shared region of interest enables practical image cube analysis through 

* Statistics Widget
* Histogram Widget
* Spectral Profiler Widget
* Spatial Profiler Widget
* Stokes Analysis Widget
* PV Generator Widget 

These widgets contain an "**Image**" dropdown menu and a "**Region**" dropdown menu. The former allows you to select which loaded image cube to show its analytics. The latter allows you to select which region to show the region analytics. By combining the two menus, CARTA provides a flexible user interface to explore image data. When the selected image has the polarization axis, you can use the "**Polarization**" dropdown menu to select which polarization component to use for deriving image analytics. 

As an example below, two image cubes representing 12CO 2-1 and 13CO 2-1 are matched spatially and spectrally. Three shared regions are created to highlight different features. Three Spectral Profiler Widgets are placed to show different profiles. The top one shows the square region profile from 12CO 2-1. The middle one shows the polygon region profile of 13CO 2-1. The bottom one shows 12CO 2-1 and 13CO 2-1 profiles from the square region. Please refer to the section :ref:`spectral_profiler` to learn how to plot *multiple* profiles in one Spectral Profiler Widget. In addition, one Statistics Widget is configured to show the statistics of 13CO 2-1 from the circle region.

.. raw:: html

  <img src="_static/carta_fn_roi_sharedRegion_analytics.png" 
      style="width:100%;height:auto;">



Region import and export
^^^^^^^^^^^^^^^^^^^^^^^^
CARTA supports region import and export capability. In world coordinates or image coordinates, regions can be exported to a text file or imported from a text file. To import a region file, use the menu "**File**" -> "**Import Regions**". A shortcut button can be found in the Region List Widget, too. 

.. raw:: html

   <img src="_static/carta_fn_regionImport.png" 
        style="width:100%;height:auto;">

To export regions to a region file, use the menu "**File**"" -> "**Export Regions**". A shortcut button can be found in the Region List Widget, too. You can use the dialog to select a subset of regions to be saved in a region text file. 

.. raw:: html

   <img src="_static/carta_fn_regionExport.png" 
        style="width:100%;height:auto;">

As of v4.0.0, CASA region text format (:code:`.crtf`) and ds9 region text format (:code:`.reg`) are supported with some limitations. Currently, only the 2D region definition is supported. Other properties, such as spectral range or reference frame, will be supported in future releases.  

The supported CRTF region syntax is summarized below:

* Rectangle

  * box[[x1, y1], [x2, y2]]
  * centerbox[[x, y], [x_width, y_width]]
  * rotbox[[x, y], [x_width, y_width], rotang]

* Ellipse

  * circle[[x, y], r]
  * ellipse[[x, y], [bmaj, bmin], pa]

* Polygon

  * poly[[x1, y1], [x2, y2], [x3, y3], ...]

* Polyline

  * polyline[[x1, y1], [x2, y2], [x3, y3], ...]

* Line

  * line[[x1, y1], [x2, y2]]

* Point

  * symbol[[x, y], .]

Please refer to https://casadocs.readthedocs.io/en/latest/notebooks/image_analysis.html#Region-File-Format for more detailed descriptions of the CRTF syntax. 


The currently supported ds9 region syntax is summarized below:

* Rectangle

  * box x y width height angle

* Ellipse

  * ellipse x y radius radius angle
  * circle x y radius

* Polygon

  * polygon x1 y1 x2 y2 x3 y3 ...

* Polyline

  * polyline x1 y1 x2 y2 x3 y3 ...

* Line

  * line x1 y1 x2 y2

* Point

  * point x y

Please refer to http://ds9.si.edu/doc/ref/region.html for more detailed descriptions of the ds9 region syntax. 


Image annotation
----------------
Image annotation and region of interest share most attributes, except the ability to derive image analytics. Image annotation is for presentation purposes only.

In CARTA, the following image annotation objects are supported:

* point (with different marker shapes)
* line (rotatable)
* rectangle (rotatable)
* ellipse (rotatable)
* square (rotatable; as a special case of rectangle; "**shift**" key + drag)
* circle (as a special case of ellipse; "**shift**" key + drag)
* polygon
* polyline
* vector (rotatable)
* text (rotatable)
* compass
* ruler


.. raw:: html

   <img src="_static/carta_fn_annotationObjects.png" 
        style="width:100%;height:auto;">



Image annotation objects created with the graphical user interface can be exported as a "region" text file in the CRTF or ds9 format.



Spatial Profiler
----------------
The Spatial Profiler provides the spatial profiles at the cursor position, point region, line region, and polyline region. 

When the "**Region**" dropdown menu is set to "cursor", or a point region, a horizontal or a vertical profile is extracted from the "**Image**" depending on the selection in the Spatial Profiler Settings Dialog (the "**cog** button at the top right corner"). When the cursor moves on the image, profiles derived from the full-resolution raster image are displayed. The "**F**" key will turn the profile update on or off. When cursor update is disabled, a marker "+" will be placed on the image to indicate the position of the profiles taken.

.. raw:: html

   <img src="_static/carta_fn_spatialProfiler_widget.png" 
        style="width:100%;height:auto;">

When a spatial profile is derived from a line or a polyline region, a set of boxes with a “height” (parallel to the trajectory) of three unit steps and a custom “width” (perpendicular to the trajectory; set with the "**Computation**" tab of the Spatial Profiler Settings Dialog) in number of unit steps are created along the trajectory. These hidden boxes are created on the reference image first. Then, similar to the polygon approximation of closed regions, these “boxes” are transformed into the spatially matched secondary image to derive a spatial profile. If the image is considered “flat” without noticeable distortion, the unit step refers to an image pixel. However, if the image is considered “wide” with noticeable distortion, the unit step refers to the angular size of an image pixel as defined in the image header. In this case, the boxes retain approximately a fixed solid angle. All these approximations allow spatial profiles of the same trajectory among different spatially matched images to be compared directly.

.. raw:: html

   <img src="_static/carta_fn_spatialProfiler_widget2.png" 
        style="width:100%;height:auto;">


An “offset” axis is constructed to compute a spatial profile for a line region. The origin is the middle point of the line region. A “distance” axis is constructed for a polyline region to compute a spatial profile along the trajectory. The origin is the first control point of the polyline. Note that sampling artifacts may be seen near the endpoints of a line region or each control point of a polyline due to the rounding effect of the sampling process.


.. raw:: html

   <img src="_static/carta_fn_linePolylineSampling.png" 
        style="width:100%;height:auto;">


.. note::

   When the sampling process is made along a line region or a polyline region in a "non-flat" image, the solid angle of the sampling boxes is approximately conserved. In some cases, especially when the image is highly distorted, some computed boxes may cover no image pixel for profile calculations. Therefore, you may see NaN values in the final spatial profile. When this happens, you can consider increasing the averaging "width" with the "**Computation**" tab of the Spatial Profiler Settings Dialog.
   
   In a future release, the averaging "height" (parallel to the trajectory) can be customized too. With the v4.0.0 release, the "height" is fixed to three (three pixels for flat image or three unit angular size for non-flat image). 

The interactions of the Spatial Profiler Widget are demonstrated in the section :ref:`mouse_interaction_with_charts`. The red vertical bar indicates the pixel where the cursor profile is taken. The bottom axis shows the image coordinate, while the optional world coordinate is displayed on the top axis. Extra options to configure the profile plot are available in the Spatial Profiler Settings Dialog, which is launched by clicking the "**cog**" button at the top-right corner. The option "**Show mean/RMS**" in the "**Styling**" tab will use the data in the current view to derive a mean value and an RMS value and visualize the results on the plot. Numerical values are also displayed at the bottom-left corner. Optionally, the profile can be smoothed with different methods in the "**Smoothing**" tab (see section :ref:`profile_smoothing`). The profile can be exported as a PNG image or a text file in TSV format via the buttons at the bottom-right corner when you hover over the plot.

When the cursor is on the image in the Image Viewer, the pointed pixel value (pixel index and pixel value) will be displayed at the bottom-left corner of the Spatial Profiler. When the cursor is on the Spatial Profiler graph, the pointed profile data will be displayed instead. 


.. note::
   Rendering performance

   When displaying a spatial profile with the number of pixels more than the number of screen pixels of the Spatial Profiler Widget, a *decimated* profile will be derived and displayed as an enhancement of performance. Min/max decimation of a profile is adopted to ensure profile features are preserved. In other words, positive and negative peaks should stay at the same screen pixels, just like displaying the full-resolution profile. Decimation with narrower and narrower intervals is applied when you keep zooming in the profile. A full-resolution profile is displayed when the number of screen pixels is more than the number of pixels of the profile to be displayed.  

.. note::
   
   Profile fitting capability will be added in a future release.
   
   


.. _spectral_profiler:

Spectral Profiler
-----------------
The Spectral Profiler Widget allows you to view region spectra from image cubes. There are two modes:

* single-profile mode (when *none* of the "**Image**"/"**Region**"/"**Statistic**"/"**Polarization**" checkboxes is selected)
* multiple-profile mode (when *one* of the "**Image**"/"**Region**"/"**Statistic**"/"**Polarization**" checkboxes is selected)

The single-profile mode allows you to create multiple Spectral Profiler Widgets and compare spectra side by side. The multiple-profile mode, however, shows multiple spectra in one plot with the same x and y ranges so that spectra can be compared directly.

**Single-profile mode**

The four dropdown menus and their selection states determine how spectral profiles are extracted from image cubes and displayed. When there is no checkbox selected, the Spectral Profiler Widget displays one spectrum only depending on the selection of each dropdown menu ("**Image**", "**Region**", "**Statistic**", and "**Polarization**"). When regions are created, the Spectral Profiler Widget can be configured to display a profile from a specific region with the "**Region**" dropdown menu. The default of the "**Region**" dropdown menu is "Active", which points to the active (selected) region. If no region is active, it defaults to the cursor region. Additional statistic types to compute the region spectral profile are available with the "**Statistic**" dropdown menu (default to mean). If the image cube has multiple polarization components, the "**Polarization**" dropdown menu will be activated and defaulted to "Current", which is synchronized with the selection in the Animator. Select the "**Polarization**" dropdown menu to view a specific polarization component.

Multiple Spectral Profiler Widgets can be configured to display different region ("**Region**" dropdown menu) spectral profiles from different image cubes ("**Image**" dropdown menu) and polarization ("**Polarization**" dropdown menu, if applicable) with different statistics ("**Statistic**" dropdown menu), allowing a side-by-side comparison of spectra.

.. raw:: html

   <img src="_static/carta_fn_spectralProfiler_multiwidget.png" 
        style="width:100%;height:auto;">


**Multiple-profile mode**

When one of the "**Image**", "**Region**", "**Statistic**", and "**Polarization**" checkboxes is selected, the Spectral Profiler Widget switches to the multiple-profile mode. CARTA supports four different use cases as the following:

* **Comparing spectra from different image cubes**: When the "**Image**" checkbox is selected, spectral profiles from different *spatially and spectrally matched* cubes can be displayed. The "**Image**" dropdown menu shows the matching state of each image as configured via the Image List Widget. The dropdown menu allows single-selection only. The selected image *and* its matched images are used for spectral profile computations based on the selected region (single selection), statistic (single selection), and polarization (if applicable, single selection). In the following example, CO 2-1, 13CO 2-1, and C18O 2-1 lines from the source HD163296 are plotted for comparison. The profiles are derived from the rectangle region with mean statistics. 

   .. raw:: html

      <img src="_static/carta_fn_spectralProfiler_multiple_image.png" 
        style="width:100%;height:auto;">

* **Comparing spectra from different regions**: When the "**Region**"" checkbox is selected, spectral profiles from different regions of an image cube can be displayed. The "**Region**" dropdown menu allows multiple selections of different regions. The region spectral profiles will be computed based on the selected image (single selection), statistic (single selection), and polarization (if applicable, single selection). The following example compares CO 2-1 mean spectra from different parts of the protoplanetary disk HD163296.

   .. raw:: html

      <img src="_static/carta_fn_spectralProfiler_multiple_region.png" 
         style="width:100%;height:auto;">

* **Comparing spectra with different statistical quantities**: When selecting the "**Statistic**" checkbox, region spectral profiles with different statistical quantities can be displayed. The "**Statistic**" dropdown menu allows multiple selections of different statistical quantities. The region spectral profiles will be computed based on the selected image (single selection), region (single selection), and polarization (if applicable, single selection). In the following example, CO 2-1 mean, standard deviation, and max spectra are compared. The profiles are derived from the ellipse region.

   .. raw:: html

      <img src="_static/carta_fn_spectralProfiler_multiple_statistic.png" 
         style="width:100%;height:auto;">


* **Comparing spectra with different Stokes parameters**: When the "**Polarization**" checkbox is selected, region spectral profiles with different polarization components can be displayed. The  "**Polarization**" dropdown menu allows multiple selections of polarization components, including computed components. The region spectral profiles will be computed based on the selected image (single selection), region (single selection), and statistic (single selection). The following example compares Stokes Q, U, and V region spectra from IRC+10216. 

   .. raw:: html

      <img src="_static/carta_fn_spectralProfiler_multiple_stokes.png" 
         style="width:100%;height:auto;">



.. note::
   Only one of the "**Image**", "**Region**", "**Statistic**", and "**Polarization**" checkboxes can be selected at a time. For example, plotting spectral profiles from different images *and* multiple regions in the same plot is prohibited.


The default region is set to "Cursor". The "**F**" key will turn the cursor profile update on or off. When cursor update is disabled, a marker "+" will be placed on the image to indicate the position of the profile taken. 



The interactions of the Spectral Profiler Widget are demonstrated in the section :ref:`mouse_interaction_with_charts`. The red vertical bar indicates the channel of the image displayed in the Image Viewer. Clicking directly on the spectral profile plot will change the displayed image to the clicked channel. Alternatively, the red vertical bar is draggable and acts just like the channel slider of the Animator Widget. 

.. raw:: html

      <img src="_static/carta_fn_spectralProfiler_channel_switching.png" 
         style="width:100%;height:auto;">



The bottom axis shows the spectral coordinate. Additional options to configure the profile plot are available in the Spectral Profile Settings Dialog, which can be launched by clicking the "**cog**" button in the top-right corner. In the dialog, you may select a different spectral convention (e.g., optical velocity), a different reference system (e.g., TOPO), and a different intensity unit (e.g., K) with the "**Conversion**" tab. You can enable the display of a secondary spectral value at the bottom of the Spectral Profiler Widget. 

The option "**Show mean/RMS**" in the "**Styling**" tab will use the data in the current view to derive a mean value and an RMS value and visualize the results on the plot. Numerical values are also displayed in the bottom-left corner of the Spectral Profiler Widget. When the cursor is on the image in the Image Viewer, the pointed pixel value (frequency, velocity, or channel index, and pixel value) will be displayed in the bottom-left corner of the Spectral Profiler Widget. When the cursor is on the spectral profile plot, the pointed profile data will be displayed instead. 

The displayed profile can be smoothed via the options in the "**Smoothing**" tab (see section :ref:`profile_smoothing`). Image collapsing is available in the "**Moments**" tab. Various image moments and statistics are supported (see section :ref:`moment_generator`). Profile fitting is available in the "**Fitting**" tab (see section :ref:`profile_fitting`). The profile can be exported as a PNG image or a text file in TSV format via the buttons at the bottom-right corner.


.. raw:: html

   <img src="_static/carta_fn_spectralProfiler_widget.png" 
        style="width:100%;height:auto;">

A custom reference rest frequency can be applied to an image cube to temporarily overwrite the :code:`RESTFRQ` header with the settings dialog of the Image List Widget. The velocity axis will be recomputed once a custom rest frequency is given. This feature allows you to compare different spectral line profiles in the velocity domain efficiently without changing the :code:`RESTFRQ` header repeatedly and permanently. Note that with the "**File**" -> "**Save image**" dialog, you can set a new rest frequency to the saved image (i.e., overwriting the :code:`RESTFRQ` header).


In the following example, a cube containing five major spectral lines is loaded twice in CARTA. Two custom rest frequencies are applied to the cubes, respectively. We can directly compare the two target profiles in the velocity domain with the multiple-profile plotting mode, as their velocities have been recomputed based on the custom rest frequencies instead of the :code:`RESTFRQ` header. As the velocity axis of each cube is recomputed, spectral matching in the velocity domain is re-applied automatically. Images from the two target lines can be compared directly near the systemic velocity of the source.

.. raw:: html

   <img src="_static/carta_fn_customRestFrequency.png" 
        style="width:100%;height:auto;">

.. note::
   Rendering performance

   When displaying a spectral profile with the number of channels more than the number of screen pixels of the Spectral Profiler Widget, a *decimated* profile will be derived and displayed to you as an enhancement of performance. Min/max decimation of a profile is adopted to ensure profile features are preserved. In other words, positive and negative peaks should stay at the same screen pixels, just like displaying the full-resolution profile. Decimation with narrower and narrower intervals is applied when you keep zooming in the profile. A full-resolution profile is displayed when the number of screen pixels is more than the number of pixels of the profile to be displayed. 



.. _moment_generator:

Moment Map Generator
--------------------
Moment images (i.e., collapsed cube along the spectral axis) can be generated and viewed with CARTA. A shortcut button linked to the "**Moments**" tab of the Spectral Profiler Settings Dialog can be found at the top-right corner of the Spectral Profiler Widget. 

.. raw:: html

   <img src="_static/carta_fn_momentGenerator_tool.png" 
        style="width:100%;height:auto;">

The "**Moments**" tab provides several control parameters to define how moment images are calculated, including:
                
* **Image**: The input image file for moment calculations. "Active" refers to the image displayed in the Image Viewer.
* **Region**: A region can be selected so that moment calculations are limited inside the region. "Active" refers to the selected region in the Image Viewer. The full image is included in the moment calculations if no region is selected.
* **Coordinate**, **System**, and **Range**: The spectral range (e.g., velocity range) used for moment calculations is defined with these options. The range can be defined via the text input fields or the cursor by dragging horizontally in the Spectral Profiler Widget.
* **Mask** and **Range**: These options define a pixel value range used for moment calculations. If the mask is "None", all pixels are included. If the mask is "Include" or "Exclude", the pixel value range defined in the text input fields is included or excluded, respectively. Alternatively, the pixel value range can be defined via the cursor by dragging vertically in the Spectral Profiler Widget.
* **Moments**: The moment images to be calculated are defined here. Supported options are:
                        
  - -1: Mean value of the spectrum
  - 0: Integrated value of the spectrum
  - 1: Intensity weighted coordinate
  - 2: Intensity weighted dispersion of the coordinate
  - 3: Median value of the spectrum
  - 4: Median coordinate
  - 5: Standard deviation about the mean of the spectrum
  - 6: Root mean square of the spectrum
  - 7: Absolute mean deviation of the spectrum
  - 8: Maximum value of the spectrum
  - 9: Coordinate of the maximum value of the spectrum
  - 10: Minimum value of the spectrum
  - 11: Coordinate of the minimum value of the spectrum


When all the parameters are defined, moment calculations will begin by clicking the "**Generate**" button. Depending on the file size, moment calculations may take a while. If that happens, you may optionally cancel the calculations and redefine a region and a spectral range.

.. raw:: html

   <img src="_static/carta_fn_momentGenerator_tool2.png" 
        style="width:100%;height:auto;">


Once generated, images will be appended, displayed, and spatially matched (optional if the original input image is the spatial reference) in the Image Viewer. They are named as :code:`$image_filename.moment.$keyword`. For example, if moment 0, 1, and 2 images are generated from the image :code:`M51.fits`, they will be named as :code:`M51.fits.moment.integrated`, :code:`M51.fits.moment.weighted_coord`, and :code:`M51.fits.moment.weighted_dispersion_coord`, respectively. These images are kept in RAM per session, and if there is a new request for moment calculations, these images will be deleted first. If you want to regenerate moment images but keep the previously generated moment images, you can enable the "**Keep previous moment image(s)**" toggle. Optionally, calculated moment images can be saved in CASA or FITS format via "**File**" -> "**Save Image**".


.. warning::
   In a resumed session after a broken connection to the backend, all in-memory images, such as those generated with the Moment Map Generator, are lost. Those images will not be accessible in the resumed session.

.. note::
   As of v4.0.0, the moment images are computed along the spectral axis only. In future release, calculations along other axes will be provided (e.g., R.A.). 


.. _pv_generator:

Position-Velocity (PV) Generator
--------------------------------------
The PV Generator has two operation modes:
* Production mode: A full-resolution PV image is computed from the full-resolution image cube, suitable for detailed analysis.
* Preview mode: A downsampled preview PV image is computed from the downsampled image cube on the fly when the PV cut moves, suitable for real-time interactive feature exploration.

Production mode
^^^^^^^^^^^^^^^

When studying source kinematics, it is common to utilize a position-velocity (PV) image. You can generate a PV image with the PV Generator Widget from the widget bar. As of v4.0.0, only a line region can be selected as the PV cut. In a future release, a polyline region will be supported.

.. raw:: html

   <img src="_static/carta_fn_pvGenerator.png" 
        style="width:100%;height:auto;">

A line region must be selected from the "**PV cut**" dropdown menu to generate a PV image. A spectral range (flexible in spectral convention) can be defined with the "**Range**" input fields to focus on the features in interest to save computation time. The axes' order (position vs. velocity or velocity vs. position) of the PV image can be configured as well. You can click the "**Generate**" button to start the PV image generation process. A progress bar will be displayed with a "**Cancel**" button during the PV image generation process. The process can be canceled at any time.

When a PV image is derived from a line region, a set of boxes with a “height” (parallel to the trajectory) of three unit steps and a custom “width” (perpendicular to the trajectory; set with the "**Averaging width**" input and spinbox) in the number of unit steps are created along the trajectory. These hidden boxes are created on the reference image first. Then, similar to the polygon approximation of closed regions, these "boxes" are transformed into the spatially matched secondary image to derive a PV image. The unit step refers to an image pixel if the image is “flat” without noticeable distortion. However, if the image is considered "wide" with noticeable distortion, the unit step refers to the angular size of an image pixel as defined in the image header. In this case, the boxes retain approximately a fixed solid angle. With all these approximations, PV images of the same trajectory can be compared directly among different spatially matched images.

.. raw:: html

   <img src="_static/carta_fn_pvGenerator2.png" 
        style="width:100%;height:auto;">


As a scalable approach for large image cubes, CARTA constructs a PV image from a series of *region spectral profiles* along the line region (PV cut) instead of re-gridding the input image cube first so that the PV cut becomes a horizontal one for the temporary cube. The final PV image is an ensemble of region spectral profiles at different sampled offset locations. 

.. note::

   When the sampling process is made along a line region in a "non-flat" image, the solid angle of the sampling boxes is approximately conserved. In some cases, especially when the image is highly distorted, some computed boxes may cover zero image pixels for spectral profile calculations. Therefore, you may see NaN stripes in the final PV image. When this happens, you can consider increasing the averaging "width" with the "**Averaging width**"  input and spinbox.

   In a future release, the averaging "height" (parallel to the trajectory) can be customized too. With the v4.0.0 release, the "height" is fixed to *three* (three pixels for flat image or three unit angular size for non-flat image). 


Once a PV image is generated, it will be loaded and displayed in the Image Viewer. It is named with an additional :code:`_pv` string in the original input file name.  The generated PV image is kept in RAM per session, and if there is a new request for PV image generation, the old PV image will be deleted first. If you want to regenerate a PV image but keep the old one, you can enable the "**Keep previous PV image(s)**" toggle. Optionally, a calculated PV image can be exported in CASA or FITS format via "**File**" -> "**Save Image**".


.. warning::
   In a resumed session after a broken connection to the backend, all in-memory images, such as those generated with the PV generator, are lost. Those images will not be accessible in the resumed session.


.. note::
   The generation of a PV image along a polyline region will be available in a future release.


Preview mode
^^^^^^^^^^^^
The PV Generator supports a preview mode to explore the PV image interactively in real time. As a scalable implementation, CARTA creates a downsampled image cube in RAM first, based on the configurations in the "**Preview region**" dropdown menu and the "**Preview rebin (px)**" inputs and spinboxes. The estimated memory usage of the downsampled cube is displayed in "**Preview cube size (MB)**". The upper limit is set to 1 GB as an experimental feature (configurable in the "**Performance**" tab of the Preferences Dialog). If the value exceeds the limit (displayed in red), you must reconfigure how the downsampled cube is constructed to use the preview mode. 

.. raw:: html

   <img src="_static/carta_fn_pvGenerator_preview.png" 
        style="width:100%;height:auto;">

By clicking the "**Start preview**" button, the PV Generator will enter the preview mode and launch a PV Preview Viewer Widget with a preview PV image derived from the downsampled cube along the PV cut. If you reconfigure the PV cut in the Image Viewer with the mouse, such as move, rotate, and resize, new preview PV images will be streamed in real-time. You can utilize this feature to explore your image cube and identify a PV cut configuration to generate a full-resolution PV image with the "**Generate**" button.






.. _image_fitter:

Image fitting
-------------
The Image Fitting Dialog can fit multiple 2D Gaussian components to your image. The default "**Data source**" is the active image, which is the current image in the Image Viewer in single-panel mode or the image highlighted with a red box if it is in multi-panel mode. You may select other images as the input image with the "**Data source**" dropdown menu.

By default, the image pixels used for the fitting process are coupled to the field of view of the Image Viewer. You can use zoom and pan actions to focus on the target image feature for the fit. Alternatively, you can select a region of interest or use a full image for the fitting process.

You can use the "**Components**" spinbox to define the number of Gaussian components in the fit. For each component, you need to define a set of initial guesses to describe a 2D Gaussian, including "**Center**", "**Amplitude**", "**FWHM**", and "**P.A. (deg)**" (position angle). A constant "**Background**" value can be added to the fit as well. Free parameters may be fixed in the fitting process when it is necessary. You need to specify a set of initial guesses for each Gaussian component. Please note that if multiple Gaussian components exist, a more accurate initial guess helps the fitter to converge more quickly to a stable location on the hypersurface.

The major FWHM axis is aligned to the North-South direction of the sky, while the minor FWHM axis is aligned to the East-West direction of the sky. The origin (0 degrees) of the P.A. points to the North, and the P.A. increases toward the East.

.. raw:: html

   <img src="_static/carta_fn_imageFitting.png" 
        style="width:100%;height:auto;">



Once the initial solutions of Gaussian components are set, you can click the "**Fit**" button to trigger the image fitting process. The fitting result is displayed in the "**Fitting Result**" tab. In the "**Full Log**" tab, more information about the fitting results is provided, including the best-fit solution in the image coordinate. Optionally, via the "**Create ellipse region**" button in the bottom-right corner of the "**Fitting Result**" tab, you can generate a set of ellipse regions to represent the FWHM of the best-fit Gaussians. You can export the fitting result or log as a text file by using the "**Export**" button in the bottom-right corner of the "**Fitting Result**" tab. The model and residual images will be generated in RAM and appended by default once the fitting process succeeds. You can use the toggles to turn off the feature if these are not required. If you want to keep the model and residual images, use the menu "**File**" -> "**Save Image**" to save them to disk.

.. warning::
   In a resumed session after a broken connection to the backend, all in-memory images, such as the model and residual images from image fitting, are lost. Those images will not be accessible in the resumed session.

Three different solvers ("Cholesky", "QR", "SVD") are provided in the "**Solver**" dropdown menu (see `Nonlinear Least-Squares Fitting <https://www.gnu.org/software/gsl/doc/html/nls.html>`_ for more information). During the fitting process, you may cancel it if necessary. By clicking the "**Clear**" button, the widget is reset to its initial state.


.. note::
   The error estimate is based on the paper by `J. J. Condon (1997; PASP 109, 166) <https://ui.adsabs.harvard.edu/abs/1997PASP..109..166C>`_.

.. note::

   In a future release, the image fitting function will be enhanced by adding the capability to set the initial guess *automatically* based on the image feature (i.e., similar to the "guess" function in the spectral profile fitting function).


.. _profile_fitting:

Profile fitting
---------------
As of v4.0.0, the profile fitting function can be applied to the Spectral Profiler Widget to estimate of the spectral line properties, such as amplitude, FWHM, center, and integrated area. The profile fitting function is available via the "**Fitting**" button in the top-right corner of the Spectral Profiler Widget. 


.. raw:: html

   <img src="_static/carta_fn_profile_fitting.png" 
        style="width:100%;height:auto;">

.. note::
   In a future release, the profile fitting function will be added to the Spatial Profiler Widget and the Histogram Widget.

CARTA supports two model profile functions in v4.0.0 (more will be added in a future release):

* Gaussian: thermal or random motion broadening
* Lorentzian: pressure broadening

In addition, the profile fitting process can include a continuum emission as a constant distribution (0th-order polynomial) or a linear distribution (1st-order polynomial).

In order to work correctly, a set of reasonable initial solutions needs to be provided to the fitting engine. CARTA provides flexible ways of setting up the initial solutions. They can be set manually with the text fields or cursor by drawing a box (for the profile function) or a line (for the continuum function) on the spectral profile plot. An amplitude, a FWHM, and a center must be configured for each component. Up to 20 components are supported in one single fit. When more than one component is required in the fit, the "**components**" slider can be used to switch to different components. The "**delete**" button can be used to delete a selected component.


.. raw:: html

   <img src="_static/carta_fn_profile_fitting_manual.png" 
        style="width:100%;height:auto;">


Alternatively, the "**auto detect**" function (experimental) tries to analyze your spectral profile data and sets up the initial solutions *automatically*. If there is a prominent continuum emission or offset, please enable the "**w/ cont.**" toggle before clicking the "**auto detect**" button. If the "**auto fit**" toggle is enabled, the fitting engine will be triggered if the "**auto detect**" function finds a set of initial solutions. When the "**auto detect**" function is applied, you may edit the initial solutions manually afterward, such as adding a new component, deleting an existing component, refining a parameter, etc.


.. raw:: html

   <img src="_static/carta_fn_profile_fitting_auto.png" 
        style="width:100%;height:auto;">


The fitting results are visualized in the spectral profile plot, including the individual model profiles, the synthetic model profile, and the residual profile. The numeric values of the fitting results are displayed in the "**Fitting result**" box. The fitting log is available by clicking the "**View log**" button. When the "**Reset**" button is clicked, the profile fitting function will be reset.


.. raw:: html

   <img src="_static/carta_fn_profile_fitting_log.png" 
        style="width:100%;height:auto;">

In some cases, a given free parameter, such as the center of a Gaussian component, may need to be fixed to obtain a *sensible* fit. A parameter can be fixed by clicking its "**lock**" button. Note that there needs to be at least one free parameter to request a fit. 

.. raw:: html

   <img src="_static/carta_fn_profile_fitting_lock.png" 
        style="width:100%;height:auto;">



.. note::
   The profile fitting function is unavailable when multiple profiles are plotted in the Spectral Profiler Widget. Please ensure that there is only one profile in the plot to use the profile fitting function.

.. note::
   In a future release, the spectral profile fitting function will be enhanced by referencing the spectral line catalog so that the relative positions of the model components can be locked. Line width and relative amplitude can be constrained, too. 



.. _profile_smoothing:

Profile smoothing
-----------------
Profile smoothing may be applied to profiles in the Spatial Profiler Widget, the Spectral Profiler Widget, and the Stokes Analysis Widget to enhance the signal-to-noise ratio. You can access the settings from the "**Smoothing**" tab of the settings dialogs of these widgets. 

.. raw:: html

   <img src="_static/carta_fn_profileSmoothing.png" 
        style="width:100%;height:auto;">

Optionally, the original profile can be overplotted with the smoothed profile. The appearance of the smoothed profile, including color, style, width, and size, can be customized.

CARTA provides the following smoothing methods:

* Boxcar: convolution with a boxcar function
* Gaussian: convolution with a Gaussian function
* Hanning: convolution with a Hanning function
* Binning: averaging channels with a given width
* Savitzky-Golay: fitting successive sub-sets of adjacent data points with a low-degree polynomial by the method of linear least squares
* Decimation: min-max decimation with a given width    

.. raw:: html

   <img src="_static/carta_fn_profileSmoothing_examples.png" 
        style="width:100%;height:auto;">




Spectral Line Query
-------------------
CARTA supports an *initial* implementation of spectral line ID overlay on a Spectral Profiler Widget based on the data from the Splatalogue service (https://splatalogue.online). The query is made by defining a spectral range in frequency or wavelength and, optionally, a lower limit of CDMS/JPL line intensity (logarithmic). The spectral range can be defined as "from-to" or "center-width". Other filters, such as filtering by species name, energy range, etc., can be applied *after* the data are retrieved from the Splatalogue. By clicking the "**Query**" button, molecular data will be retrieved from the Splatalogue service. 

.. note::
   The current implementation has some limitations when making a query to the Splatalogue service:

   * The allowed maximum query range, equivalent in frequency, is 20 GHz.
   * The actual query is made with a frequency range in MHz rounded to integer.
   * Only the lines from CDMS and JPL catalogs will be returned when an intensity limit is applied.
   * Up to 100,000 lines are displayed. 

   Improvements to the above limitations will be made in future releases.


.. raw:: html

   <img src="_static/carta_fn_linequery_widget.png" 
        style="width:100%;height:auto;">

Once a query is successfully made, the line catalog will be displayed in the tables. The upper table shows the column information in the catalog with options to show or hide a specific column. The actual line catalog is displayed in the lower table. The line catalog table accepts sub-filters such as partial string match or value range. For numeric columns, supported operators are:

* :code:`>` : greater than
* :code:`>=` : greater than or equal to
* :code:`<` : less than
* :code:`<=` : less than or equal to
* :code:`==` : equal to
* :code:`!=` : not equal to
* :code:`..` : between (exclusive)
* :code:`...` : between (inclusive)
                    
For examples:

* To filter everything less than 10, use :code:`< 10`
* To filter entries equal to 1.23, use :code:`== 1.23`
* To filter everything between 10 and 50 (exclusive), use :code:`10..50`
* To filter everything between 10 and 50 (inclusive), use :code:`10...50`

For string columns, a partial match is adopted. For example, :code:`CH3` (no quotation) will return entries containing the "CH3" string.

The "Shifted Frequency" column is computed based on the user input of a velocity or a redshift. This "Shifted Frequency" is adopted for line ID overlay on a Spectral Profiler Widget. You can use the checkbox to select a set of lines to be overplotted on a Spectral Profiler Widget. The maximum number of line ID overlays is 1000.


The text labels of the line ID overlay are shown dynamically based on the zoom level of a profile. Different line ID overlays (with different velocity shifts) can be created on different Spectral Profiler Widgets via the "**Spectral Profiler**" dropdown menu. By clicking the "**Clear plot**" button, the line ID overlay on the selected Spectral Profiler will be removed.

.. note::
   The sorting function in the line table will be available in a future release.

.. note::
   When there are multiple profiles from different image cubes in the plot, and the x-axis is in velocity, the line ID overlay function is disabled.



Stokes Analysis Widget
----------------------
The Stokes Analysis Widget helps you efficiently view fundamental polarization quantities of a multi-channel cube with multi-Stokes (IQU, QU, or IQUV). Suppose different Stokes images are stored as individual files (i.e., image_I.fits, image_Q.fits, image_U.fits, and image_V.fits). In that case, you can use the File Browser Dialog to create a Stokes hypercube by selecting multiple Stokes images and clicking the “Load as hypercube” button (see :ref:`forming_hypercube`). Effectively, you will see only one image loaded with multiple Stokes in CARTA. 


The widget includes the following plots:

* Stokes Q intensity and Stokes U intensity over the spectral axis
* Linear polarization intensity over the spectral axis
* Linear polarization angle over the spectral axis
* Stokes Q intensity versus Stokes U intensity as a scatter plot

The profiles can be zoomed and panned with a mouse, similar to the Spatial Profiler Widget or the Spectral Profiler Widget (:ref:`mouse_interaction_with_charts`). The Stokes Q versus Stokes U scatter plot is color-encoded from red to blue with increasing frequencies. The profiles can be requested at the cursor position (single pixel) or over a region of interest. Fractional polarization quantities are also supported when the Stokes I component is available. 

.. raw:: html

   <img src="_static/carta_fn_Stokes_widget.png" 
        style="width:100%;height:auto;">



When profiles are zoomed in, the scatter plot will highlight those channels in the profile view. Similarly, when the scatter plot is zoomed, the profile plot will highlight those channels just in the scatter plot view. The profile plots and the scatter plot are interlinked.

.. raw:: html

   <img src="_static/carta_fn_Stokes_widget_linkView1.png" 
        style="width:100%;height:auto;">

.. raw:: html

   <img src="_static/carta_fn_Stokes_widget_linkView2.png" 
        style="width:100%;height:auto;">

Additional options to customize the plots in the Stokes Analysis Widget are provided in the settings dialog, which can be launched by clicking the "**cog**" button at the top-right corner. With the options in the dialog, you can configure the appearance of the profile plots and the scatter plot. Optionally, profile smoothing can be applied with the "**Smoothing**" tab (see section :ref:`profile_smoothing`). A shortcut button to the "**Smoothing**" tab can be found in the top-right corner of the Stokes Analysis Widget.



Statistics Widget
-----------------
The Statistics Widget allows you to view statistics from a selected region and a selected image with a polarization component (if it exists). The following statistic quantities are supported:

* NumPixels: number of pixels included in the statistics computation
* Sum: summation
* Mean: average
* FluxDensity: flux density (requiring beam information)
* StdDev: standard deviation
* Min: minimum
* Max: maximum
* Extrema: extrema
* RMS: root mean square
* SumSq: summation of squared pixel values

The "**Region**" dropdown menu and the "**Image**" dropdown menu can be used to select which region statistics from which image to be displayed. When the selected image has the polarization axis, you can use the "**Polarization**" dropdown menu to select a target polarization component to compute statistics. The default is "Active", which means the active (selected) region and the active image in the Image Viewer. The “Active” option refers to the entire image if no region is active. Multiple Statistics Widgets can be created to display statistics computed with a combination of "**Image**", "**Region**", and "**Polarization**" (if it is available). 


.. raw:: html

   <img src="_static/carta_fn_statistics_widget.png" 
        style="width:100%;height:auto;">

The statistics table can be exported as a text file with the "**export data**" button at the bottom-right corner when you hover over the widget. 


Histogram Widget
----------------
The Histogram Widget allows you to visualize image data as a histogram. The "**Image**" dropdown menu and the "**Region**" dropdown menu can select which region from which image to display. When the selected image has the polarization axis, you can use the "**Polarization**" dropdown menu to select a target polarization component to compute a histogram. The default is "Active", which means the active (selected) region and the active image in the Image Viewer. The “Active” option refers to the entire image if no region is active. Multiple Histogram Widgets can be created to display histograms computed with a combination of "**Image**", "**Region**", and "**Polarization**" (if it is available).


.. raw:: html

   <img src="_static/carta_fn_histogram_widget.png" 
        style="width:100%;height:auto;">

The histogram plot can be zoomed and panned with a mouse, similar to the Spatial Profiler Widget or the Spectral Profiler Widget (:ref:`mouse_interaction_with_charts`).

Additional options to customize the histogram plot are provided in the settings dialog which can be launched by clicking the "**cog**" icon at the top-right corner. In the "**Configuration**" tab, you can apply a custom range and the number of bins to compuate the histogram. 

With the toolbar at the bottom-left of the histogram width, you can export the plot as a PNG file or as a TSV text file.

.. note::
   Histogram fitting functions will be added in a future release.

.. _distance_measure_tool:

Distance Measurement Tool
-------------------------
The distance measurement tool is available from the toolbar of the Image Viewer or the dialog bar at the top of the GUI. To measure a geodesic distance on an image, you can use two mouse clicks to define a starting point and a finishing point, respectively, for the distance calculations. Alternatively, you can use the Distance Measurement Dialog to enter a pair of coordinates for the same purpose. 

The result is visualized on the image, including the iso-longitude and iso-latitude geodesic lines. The appearance of the rendered geodesic lines can be customized in the "**Styling**" tab of the Distance Measurement Dialog. 

You can have new measurements with pairs of clicks. Click the "**pan**" button in the toolbar to leave the state. A distance in pixel values will be provided if the geodesic distance cannot be calculated.

.. raw:: html

   <img src="_static/carta_fn_distance_measure.png" 
        style="width:100%;height:auto;">



.. _cursor_info_widget:

Cursor Info Widget
------------------
When there are multiple matched images, comparing pixel quantities from the images at the cursor position is a common practice. The Cursor Info Widget is a centralized place to show the cursor information for all the matched images in this use case. You can use the Image List Widget to trigger image matching. The Cursor Info Widget includes

* image name
* pixel value
* spatial image and world coordinates
* spectral coordinate and channel index
* polarization component

.. raw:: html

   <img src="_static/carta_fn_cursor_info.png" 
        style="width:100%;height:auto;">

You can press the "G" key to enable mirrored cursors on the matched images.



.. tip::

   A cursor info bar is displayed at the top of the active image plot by default in the Image Viewer. When it is the single-panel view mode, the image in the current view is the active image. When it is the multi-panel view mode, the active image is highlighted with a red box. With the "**File**" -> "**Preferences**" -> "**WCS and image overlay**" -> "**Cursor Info Visible**" dropdown menu, you can switch to a different mode. Available modes are

   * Always: Always show the cursor info bar per image
   * Active image only: Only show the cursor info bar on the active image (default)
   * Hide when tiled: Do not show the cursor info bar when it is in the multi-panel view mode.
   * Never: Do not show the cursor info bar regardless of whether it is the single-panel view mode or the multi-panel view mode.

The entry for the active image is highlighted in boldface. When you see a cursor value with a "*", the CARTA frontend is waiting for the value update from the backend. Therefore, the displayed value may not represent the pixel value at the latest cursor position. This behavior sometimes happens with intermittent internet conditions.


Catalog Widget and Online Catalog Query Dialog
----------------------------------------------
The Catalog Widget allows you to visualize a local source catalog in "VOTable" or "FITS" format or retrieve a catalog from remote services `SIMBAD <https://simbad.u-strasbg.fr>`_ and `VizieR  <https://vizier.cds.unistra.fr>`_. Apart from table visualization, catalog data can also be visualized as:

* image overlay
* 2D scatter plot
* histogram

Please refer to the section :ref:`catalog_widget` for details.


Log Widget
----------
The Log Widget is a tool which provides important diagnostic information when something has gone wrong. It offers multiple log levels for reporting different levels of detail:
        
* Debug: intended for in-depth analysis and troubleshooting.
* Info (default): presents general information and updates.
* Warning: highlights potential issues or concerns.
* Error: indicates encountered errors that require attention.
* Critical: identifies critical errors demanding immediate intervention.

.. raw:: html

   <img src="_static/carta_fn_log.png" 
        style="width:50%;height:auto;">


If you encounter an error, we encourage you to reach out for assistance. You can contact our `HelpDesk <mailto:support@carta.freshdesk.com>`_ or visit our `GitHub <https://github.com/CARTAvis/carta/issues>`_ to file an issue.