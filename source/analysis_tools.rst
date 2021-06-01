Image cube analysis tools
=========================
With version 2.0, CARTA provides the following widgets and tools for image cube analysis:

* Widget
  
  * Region list: to view and configure region properties
  * Spatial profiler: to view x or y spatial profile at the cursor position
  * Spectral profiler: to view one or multiple spectral profiles
  * Histogram: to view histogram from a region of interest
  * Statistics: to view basic statistics from a region of interest
  * Stokes analysis: to view basic polarization quantities (e.g., polarized intensity and angle)
  * Spectral line query: to make a query to the Splatalogue service and create labels on a spectral profile plot
  * Catalogue widget: to visualize a catalogue as an image overlay, a 2D scatter plot, or a histogram

* Tool

  * Profile smoothing: to smooth a spectral or spatial profile for a better S/N
  * Moment map generator: to collapse an image cube with various moments and statistics
  * Spectral profile fitting: to fit an observed spectrum with a model profile


Region of interest
------------------
As of v2.0, CARTA supports the following region types:

* rectangle (rotatable)
* ellipse (rotatable)
* square (rotatable; as a special case of rectangle; "**shift**" key + drag)
* circle (as a special case of ellipse; "**shift**" key + drag)
* point
* polygon


The creation and modification of regions are demonstrated in the section :ref:`mouse_interaction_with_regions`. To create a region, use the region button at the bottom-right corner of the image viewer or use the region buttons at the top of the GUI, then use the cursor to draw a region. CARTA allows regions to be created even if the region is outside the image. Keyboard shortcuts associated with regions are listed below.

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

  If using CARTA remote mode in Firefox on macOS, you may find the "**backspace**" key navigates back a page instead of removing a region. This behaviour can be prevented by modifying your Firefox web browser settings:

  1. Enter about:config in the address bar.
  2. Click "I accept the risk!"
  3. A search bar appears at the top of a long list of preferences. Search for "browser.backspace_action"
  4. It will likely have a value of 0. Double click it, and then modify it to a value of "2".
  5. Close the about:config tab and now backspace will no longer navigate back a page.

All created regions are listed in the region list widget with basic region properties. To select a region (region state changes to "selected"), simply click on the region in the image viewer, or click on the region in the region list widget. To modify the properties of a selected region, double-click on a region in the image viewer or a region in the region list widget. The color, line style, name, location, and shape, of a region are all configurable with the region configuration dialogue. The location and shape properties can be edited in the image coordinate, or in the world coordinate with angular scales (default). To de-select a region or cancel a region creation process, press "**esc**" key. To delete a selected region, press "**delete**" or "**backspace**" key. An activated region can be locked by pressing "**L**" key or by clicking the "lock" icon in the region list widget or region property dialogue. When a region is locked, it cannot be modified (resize, move, or delete) with mouse actions and the "**delete**" or "**backspace**" key. A locked region, however, can still be modified or deleted via the region configuration dialogue. Locking a region could help the situation when users want to modify overlapping regions, or could prevent modifying a region accidentally. The "center" icon is to show the corresponding region at the center of image view. 

.. raw:: html

   <img src="_static/carta_fn_roi.png" 
        style="width:100%;height:auto;">


CARTA checks if a polygon is simple or complex. If a polygon is detected as complex, its color will be in pink as a warning. Spectral profile, statistics, or histogram of a complex polygon can still be requested. However, the outcome may be beyond users' expectations. The enclosed pixels depend on *how* a complex polygon is constructed. Please use complex polygons with caution. 

When editing region properties in the world coordinate, the coordinate reference system can be changed with the dropdown menu. The default reference system is as defined in the image header and is the same as the one defining the grid line overlay in the image viewer. When users switch to different reference frames, the grid line overlay in the image viewer is changed too. If the reference system is ICRS, FK5 or FK4, the coordinate is in sexagesmial format. If the reference system is Galactic or Ecliptic, the coordinate is in decimal degrees. The region size property can be defined in arcsecond with **"**, in arcminute with **'**, or in degrees with **deg**.


Shared region with conserved solid angle
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When a region is created on one of the spatially matched images, effectively the region is created on the image served as the spatial reference, regardless which image is being viewed. Then, the region is *shared* and rendered to other spatially matched images with the considerations of projection effects and difference in coordinate reference systems. Regions (except the point region) are approximated by polygons and each control point is transformed from the spatial reference image to the spatially-matched secondary image. In this way, the solid angles of the regions before and after polygonal approximation are nearly identical thus analytics of the *same* region among different spatially matched images can be compared directly. 

In the following exaggerated example, two images with different coordinate systems and projection schemes are spatially matched. Regions on the spatial reference image retain their shapes. Polygon approximated regions on the spatially-matched secondary image may have visible distortions, depending on the projection schemes. In most use cases, the region distortion effect should be much less noticable if the field of view of the image is small.

.. raw:: html

  <img src="_static/carta_fn_roi_sharedRegion.png" 
      style="width:100%;height:auto;">

Shared region management
^^^^^^^^^^^^^^^^^^^^^^^^
When regions are created on one of the spatially matched images, they are *all* registered to the spatial reference image for matching. The regions are shared to all the matched images, thus analytics can be derived and compared directly. When an image is unmatched with respect to the spatial reference image, the image will get a copy of all regions. This set of regions is now independent to the region set belonging to the matched images. If there are modifications of the regions and users re-match the image to the matched images, only those modified regions will be copied to the region set of the matched images. The following diagram illustrates the idea.

.. raw:: html

  <img src="_static/carta_fn_roi_sharedRegion_management.png" 
      style="width:100%;height:auto;">

Analytics with shared regions
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Shared region of interest enables practical image cube analysis through statistics, histogram, spectral profiler, and Stokes analysis widgets. These widgets contains an image dropdown menu and a region dropdown menu. The former allows users to select which loaded image cube to show its analytics. The latter allows users to select which region to show the region analytics. With the combination of the two menus, CARTA provides a flexible user interface to explore image data. 

As an example below, two image cubes representing 12CO 2-1 and 13CO 2-1 are matched spatially and spectrally. Three shared regions are created to highlight different features. Three spectral profiler widgets are placed to show different profiles. The top one shows the square region profile from 12CO 2-1. The middle one shows the polygon region profile of 13CO 2-1. The bottom one shows both 12CO 2-1 and 13CO 2-1 profiles from the square region. Please refer to the section :ref:`spectral_profiler` to learn how to plot *multiple* profiles in one spectral profler widget. In addition, one statistics widget is configured to show the statistics of 13CO 2-1 from the circle region.

.. raw:: html

  <img src="_static/carta_fn_roi_sharedRegion_analytics.png" 
      style="width:100%;height:auto;">



Region import and export
^^^^^^^^^^^^^^^^^^^^^^^^
As of v2.0, CARTA supports basic region import and export capability. Regions, in world coordinate or in image coordinate, can be exported to a text file or imported from a text file. To import a region file, use the menu **File** -> **Import regions**. 

.. raw:: html

   <img src="_static/carta_fn_regionImport.png" 
        style="width:100%;height:auto;">

To export regions to a region file, use the menu **File** -> **Export regions**. All regions, except cursor, will be exported. 

.. raw:: html

   <img src="_static/carta_fn_regionExport.png" 
        style="width:100%;height:auto;">

As of v2.0, CASA region text format (.crtf) and ds9 region text format (.reg) are supported with some limitations. Currently only the 2D region definition is supported. Other properties, such as spectral range or reference frame will be supported in future releases.  

The currently supported CRTF region syntax is summarized below:

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

Please refer to https://casa.nrao.edu/casadocs/casa-5.7.0/imaging/image-analysis/region-file-format for more detailed descriptions about the CRTF syntax. 


The currently supported ds9 region syntax is summarized below:

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

When displaying a spatial profile with the number of pixels more than the number of screen pixels of the spatial profiler widget, a *decimated* profile will be derived and displayed to users as an enhancement of performance. Min/max decimation of a profile is adopted to ensure profile features are preserved. In other words, positive and negative peaks should stay at the same screen pixels just like displaying the full resolution profile. When users keep zooming in the profile, decimation with narrower and narrower intervals is applied dynamically. Full resolution profile is displayed when the number of screen pixels is more than the number of pixels of the profile to be displayed.  

The interactions of the spatial profiler widget are demonstrated in the section :ref:`mouse_interaction_with_charts`. The red vertical bar indicates the pixel where the profile is taken. The bottom axis shows the image coordinate, while optional world coordinate is displayed on the top axis. Extra options to configure the profile plot are available in the spatial profiler settings dialogue which is launched by clicking the "cog" icon at the top-right corner. The option "Show Mean/RMS" in the Styling tab will adopt the data in the current view to derive a mean value and an rms value, and visualize the results on the plot. Numerical values are also displayed at the bottom-left corner. Optionally, the profile can be smoothed with different methods provided in the Smoothing tab (see section :ref:`profile_smoothing`). The profile can be exported as a png image or a text file in tsv format via the buttons at the bottom-right corner when hovering over the plot.

When the cursor is on the image in the image viewer, the pointed pixel value (pixel index and pixel value) will be displayed at the bottom-left corner of the spatial profiler. When the cursor is on the spatial profiler graph, the pointed profile data will be displayed instead. 



.. raw:: html

   <img src="_static/carta_fn_spatialProfiler_widget.png" 
        style="width:100%;height:auto;">

.. note::
   In future releases, the following features will be supported:
   
   * More flexibilities on how mean and rms values are derived in the plot
   * Profile fitting capability 
   * Profile along a line segment, polyline, or an arbitrary curve  



.. _spectral_profiler:

Spectral profiler
-----------------
Spectral profiler widget allows users to view region spectra from image cubes. There are two modes:

* single-profile mode (when none of the Image/Region/Statistic/Stokes checkboxes is selected)
* multiple-profile mode (when one of the Image/Region/Statistic/Stokes checkboxes is selected)

The single-profile mode allows users to create multiple spectral profiler widgets and compare spectra side by side. The multiple-profile mode, however, shows multiple spectra in one plot with same x and y ranges so that spectra can be compared directly.

**Single-profile mode**

The configuration of how spectral profiles are extracted from image cubes and displayed is determined by the four dropdown menus and their selection states. When there is no checkbox selected, the spectral profiler widget displays one spectrum only depending on the selection of each dropdown menu (Image, Region, Statistic, and Stokes). When regions are created, the spectral profiler widget can be configured to display a profile from a specific region with the "*Region*" dropdown menu. The default of the "*Region*" dropdown is "Active" which points to the current active (selected) region. If no region is active, it defaults to cursor region. Additional statistic types to compute the region spectral profile are available with the "*Statistic*" dropdown menu (default to mean). If the image cube has multiple Stokes, the "*Stokes*" dropdown menu will be activated and defaulted to "Current" which is synchronized with the selection in the animator. To view a specific Stokes, select with the "*Stokes*" dropdown menu.

Multiple spectral profile widgets can be configured to display different region ("*Region*" dropdown menu) spectral profiles from different image cubes ("*Image*" dropdown menu) and Stokes ("*Stokes*" dropdown menu, if applicable) with different statistics ("*Statistic*" dropdown menu), allowing a side-by-side comparsion of spectra.

.. raw:: html

   <img src="_static/carta_fn_spectralProfiler_multiwidget.png" 
        style="width:100%;height:auto;">



**Multiple-profile mode**

When one of the Image, Region, Statistic, and Stokes checkboxes is selected, the spectral profiler widget switches to the multiple-profile mode. CARTA support four different use cases as the following:

* **Comparing spectra from different image cubes**: When the Image checkbox is selected, spectral profiles from different *spatially and spectrally matched* cubes can be displayed. The image dropdown menu shows the matching state of each image as configured via the image list widget. The dropdown menu allows single-selection only. The selected image *and* its matched images are used for spectral profile computations based on the selected region (single selection), statistic (single selection), and Stokes (if applicable, single selection). In the following example, CO 2-1, 13CO 2-1, and C18O 2-1 lines from the source HD163296 are plotted for comparsion. The profiles are dervied from the rectangle region with mean statistic. 

   .. raw:: html

      <img src="_static/carta_fn_spectralProfiler_multiple_image.png" 
        style="width:100%;height:auto;">

* **Comparing spectra from different regions**: When the Region checkbox is selected, spectral profiles from different regions of an image cube can be displayed. The region dropdown menu allows multiple-selection of different regions. The region spectral profiles will be computed based on the selected image (single selection), statistic (single selection), and Stokes (if applicable, single selection). In the following example, CO 2-1 mean spectra from different parts of the protoplanetary disk HD163296 are compared.

   .. raw:: html

      <img src="_static/carta_fn_spectralProfiler_multiple_region.png" 
         style="width:100%;height:auto;">

* **Comparing spectra with different statistic quantities**: When the Statistic checkbox is selected, region spectral profiles with different statistic quantities can be displayed. The statistic dropdown menu allows multiple-selection of different statistic quantities. The region spectral profiles will be computed based on the selected image (single selection), region (single selection), and Stokes (if applicable, single selection). In the following example, CO 2-1 mean, standard deviation, and max spectra are compared. The profiles are derived from the ellipse region.

   .. raw:: html

      <img src="_static/carta_fn_spectralProfiler_multiple_statistic.png" 
         style="width:100%;height:auto;">


* **Comparing spectra with different Stokes parameters**: When the Stokes checkbox is selected, region spectral profiles with different Stokes parameters can be displayed. The Stokes dropdown menu allows multiple-selection of different Stokes. The region spectral profiles will be computed based on the selected image (single selection), region (single selection), and statistic (single selection). In the following exmaple, Stokes Q, U and V single-pixel spectra from IRC+10216 are compared. 

   .. raw:: html

      <img src="_static/carta_fn_spectralProfiler_multiple_stokes.png" 
         style="width:100%;height:auto;">


.. note::
   Only one of the Image, Region, Statistic, and Stokes checkboxes can be selected at one time. Plotting spectral profiles from different images *and* from multiple regions, for example, is not allowed. 



The default region is set to "Cursor". The "**F**" key will disable or enable cursor profile update. When cursor update is disabled, a marker "+" will be placed on the image to indicate the position of the profile taken. 

When requesting a spectral profile, a common disappointing user experience is that users may have to wait for an unknown amount of time to see the final result if the image cube is large. As an improvement on this aspect, CARTA supports *progressive update* of spectral profile. Partial profiles will be periodically delivered to users while the full profile calculations are still ongoing. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_spectralProfiler_partialUpdate.mp4" type="video/mp4">
   </video>


When the property of a region (cursor or a regular region) is modified while the profile of the original region is being updated, the partial profile will disappear and a new partial profile corresponding to the new region will start updating. If users modify the request of a spectral profile via the spectral profile widget before it is fully delivered, the original profile calculations will be cancelled and new profile calculations will start. In short, CARTA should just focus on calculating and showing the profiles that users pay attention to. If a profile is no longer needed to be shown on the screen, the profile calculation will be cancelled immediately, instead of blocking and queueing up new profile requests. 


.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_spectralProfiler_profileCancellation.mp4" type="video/mp4">
   </video>

When displaying a spectral profile with the number of channels more than the number of screen pixels of the spectral profiler widget, a *decimated* profile will be derived and displayed to users as an enhancement of performance. Min/max decimation of a profile is adopted to ensure profile features are preserved. In other words, positive and negative peaks should stay at the same screen pixels just like displaying the full resolution profile. When users keep zooming in the profile, decimation with narrower and narrower intervals is applied dynamically. Full resolution profile is displayed when the number of screen pixels is more than the number of pixels of the profile to be displayed. 

The interactions of the spectral profiler widget are demonstrated in the section :ref:`mouse_interaction_with_charts`. The red vertical bar indicates the channel of the image displayed in the image viewer. Clicking directly on the spectral profiler graph will change the displayed image to the clicked channel. Alternatively, the red vertical bar is draggable and acts just like the channel slider of the animator widget. 

The bottom axis shows the spectral coordinate. Additional options to configure the profile plot are available in the spectral profile settings dialogue which can be launched by clicking the "cog" icon in the top-right corner. In the dialogue, users may select a different spectral convention (e.g., optical velocity) and a different reference system (e.g., TOPO) with the Conversion tab. The option "Show Mean/RMS" in the Styling tab will adopt the data in the current view to derive a mean value and an rms value, and visualize the results on the plot. Numerical values are also displayed at the bottom-left corner. When the cursor is on the image in the image viewer, the pointed pixel value (frequency or velocity or channel index, and pixel value) will be displayed at the bottom-left corner of the spectral profiler. When the cursor is on the spectral profiler graph, the pointed profile data will be displayed instead. Optionally, the displayed profile can be smoothed via the options in the Smoothing tab (see section :ref:`profile_smoothing`). Image collapsing is available in the Moments tab. Various image moments and statistics are supported (see section :ref:`moment_generator`). Profile fitting is available in the Fitting tab (see section :ref:`profile_fitting`). The profile can be exported as a png image or a text file in tsv format via the buttons at the bottom-right corner.

.. raw:: html

   <img src="_static/carta_fn_spectralProfiler_widget.png" 
        style="width:100%;height:auto;">


.. note::
   In future releases, the follow features will be supported:
   
   * More flexibilities on how mean and rms values are derived
   * Intensity unit conversion
   * Dynamic velocity reference transformation



   

.. _moment_generator:

Moment map generator
--------------------
Moment images (i.e., collapsed cube along the spectral axis) can be generated and viewed with CARTA. A shortcut button, linking to the Moments tab of the spectral profilers settings dialogue, can be found at the top-right corner of the spectral profiler widget.

**[TODO]** update the following figure again due to UI change...

.. raw:: html

   <img src="_static/carta_fn_momentGenerator_tool.png" 
        style="width:100%;height:auto;">

The Moments tab provides several control parameters to define how moment images are calculated, including:
                
* Image: the input image file for moment calculations. "Active" refers to the image displayed in the image viewer.
* Region: a region can be selected so that moment calculations are limited inside the region. "Active" refers to the selected region in the image viewer. If no region is selected, the full image is included in the moment calculations.
* Coordinate, System, and Range: the spectral range (e.g., velocity range) used for moment calculations is defined with these options. The range can be defined either via the text input fields, or via the cursor by dragging horizontally in the spectral profiler widget.
* Mask and Range: these options define a pixel value range used for moment calculations. If the mask is "None", all pixels are included. If the mask is "Include" or "Exclude", the pixel value range defined in the text input fields is included or excluded, respectively. Alternatively, the pixel value range can be defined via the cursor by dragging vertically in the spectral profiler widget.
* Moments: which moment images to be calculated are defined here. Supported options are:
                        
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


When all the parameters are defined, by clicking the "Generate" button, moment calculations will begin. Depending on the file size, moment calculations may take a while. If that happens, users may optionally  cancel the calculations and re-define a proper region and/or spectral range.

.. note::
   As of v2.0, the moment images are computed along the spectral axis only. In future release, calculations along other axes will be provided (e.g., R.A.). 



Once moment images are generated, they will be loaded and displayed in the image viewer. They are named as $image_filename.moment.$keyword. For example, if moment 0, 1 and 2 images are generated from the image M51.fits, they will be named as *M51.fits.moment.integrated*, *M51.fits.moment.weighted_coord*, and *M51.fits.moment.weighted_dispersion_coord*, respectively. These images are kept in RAM per session and if there is a new request of moment calculations, these images will be deleted first. Optionally, calculated moment images can be exported in CASA or FITS format via **File** -> **Save image**.

.. raw:: html

   <img src="_static/carta_fn_momentGenerator_tool2.png" 
        style="width:100%;height:auto;">

                
.. note::
   Due to a CASA issue, image of "Median coordinate" cannot be generated. The request of "Median coordinate" is ignored automatically.

.. warning::
   In a resumed session after a broken connetion to the backend, all in-memory images, such as the images generated with the moment generator, are lost. Those images will not be accessible in the resumed session.


.. _profile_fitting:

Profile fitting
---------------
As of v2.0, the profile fitting function can be applied to the spectral profiler widget as an estimate of the spectral line properties, such as amplitude, FWHM, center, and intergrated area. The profile fitting function is available via the "Fitting" button at the top-right corner of the spectral profiler widget. 

.. raw:: html

   <img src="_static/carta_fn_profile_fitting.png" 
        style="width:100%;height:auto;">

.. note::
   In a future release, the profile fitting function will be added to the spatial profiler widget and the histogram widget.

CARTA supports two model profile functions in v2.0 (more will be added in a future release):

* Gaussian: thermal or random motion broadening
* Lorentzian: pressure broadening

In addition, a continuum emission as a constant distribution (0th-order polynomial) or a linear distribution (1st-order polynomial) can be included in the profile fitting process.

In order to work properly, a set resonable initial solutions needs to be provided to the fitting engine. CARTA provides flexible ways of setting up the initial solutions. They can be set manually with the text fields or with the cursor by drawing a box (for the profile function) or a line (for the continuum function) on the spectral profile plot. For each component, an amplitude, a FWHM, and a center need to be configured. Up to 20 components are supported in one single fit. When there are more than one component required in the fit, the "slider" can be used to switch to different components. The "delete" button can be used to delect a selected component.

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_profile_fitting_manual.mp4" type="video/mp4">
   </video>


Alternatively, the "auto detect" function (experimental) tries to analyze your spectral profile data and sets up the initial solutions *automatically*. If there is a prominent continumm emission or offset, please enable the "w/ cont." toggle before clicking the "auto detect" button. If the "auto fit" toggle is enabled, the fitting engine will be triggered if the "auto detect" function found a set of initial solutions. When the "auto detect" function is applied, you may edit the initial solutions manually afterward, such as adding a new component, deleting an existing component, refining a parameter, etc.. 

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_profile_fitting_auto.mp4" type="video/mp4">
   </video>

The fitting results are visualized in the spectral profile plot, including the individual model profiles, the synthetic model profile, and the residual profile. The numeric values of the fitting results are displayed in the "Fitting result" box. The fitting log is available by clicking the "View log" button. When the "Reset" button is clicked, the profile fitting function will be reset.

.. raw:: html

   <img src="_static/carta_fn_profile_fitting_log.png" 
        style="width:100%;height:auto;">


In some cases, a given free parameter, such as the center of a Gaussian component, may need to be fixed in order to obtain a sensible fit. This is supported with the "lock" button. Note that there needs to be at least one parameter unlocked in order to request a fit. 

.. raw:: html

   <img src="_static/carta_fn_profile_fitting_lock.png" 
        style="width:60%;height:auto;">


.. note::
   The profile fitting function is not available when there are multiple profiles plotted in the spectral profiler widget. Please ensure that there is only one profile in the plot in order to use the profile fitting function.

.. note::
   In future releases, the spectral profile fitting function will be enhanced by referencing line catalog so that the relative positions of the model components can be locked. Line width and relative amplitude can be constrained too. 



.. _profile_smoothing:

Profile smoothing
-----------------
Profile Smoothing may be applied to profiles in the spatial profiler widget, the spectral profiler widget, and the Stokes analysis widget to enhance the signal-to-noise ratio. 

CARTA provides the following smoothing methods:

* Boxcar: convolution with a boxcar function
* Gaussian: convolution with a Gaussian function
* Hanning: convolution with a Hanning function
* Binning: averaging channels with a given width
* Savitzky-Golay: fitting successive sub-sets of adjacent data points with a low-degree polynomial by the method of linear least squares
* Decimation: min-max decimation with a given width    


Optionally, the original profile can be overplotted with the smoothed profile. The appearance of the smoothed profile, including color, style, width, and size, can be customized.


.. raw:: html

   <img src="_static/carta_fn_profileSmoothing_examples.png" 
        style="width:100%;height:auto;">




Spectral line query
-------------------
CARTA supports an *initial* implementation of spectral line ID overlay on a spectral profiler widget based on the data from the Splatalogue service (https://splatalogue.online). The query is made by defining a spectral range in frequency or wavelength and optionally a lower limit of CDMS/JPL line intensity (log). The spectral range can be defined as from-to or center-width. Other filters, such as filtering by species name, or enery range, etc., can be applied *after* the data are retrived from the  Splatalogue.

.. note::
   The current implementation has some limitations when making a query to the Splatalogue service:

   * The allowed maximum query range, equivalent in frequency, is 20 GHz.
   * The actual query is made with a frequency range in MHz rounded to integer.
   * When an intensity limit is applied, only the lines from CDMS and JPL catalogues will be returned.
   * Up to 100000 lines are displayed. 

   Improvements of the above limitations will be made in future releases.

   Currently, the Splatalogue query service is under active development. Unexpected query results might happen. When users believe there is something wrong, please contact `the CARTA helpdesk <mailto:carta@asiaa.sinica.edu.tw>`_, or file an issue on `Github <https://github.com/CARTAvis/carta/issues>`_ (recommended).  


Once a query is successfully made, the line catalogue will be displayed in the tables. The upper table shows the column information in the catalogue with options to show or hide a specific column. The actual line catalogue is displayed in the lower table. The line catalogue table accepts sub-filters such as partial string match or value range. For numeric columns, supported operators are:

* :code:`>` : greater than
* :code:`>=` : greater than or equal to
* :code:`<` : less than
* :code:`<=` : less than or equal to
* :code:`==` : equal to
* :code:`!=` : not equal to
* :code:`..` : between (exclusive)
* :code:`...` : between (inclusive)
                    
For examples:

* to filter everything less than 10, use :code:`< 10`
* to filter entries equal to 1.23, use :code:`== 1.23`
* to filter everything between 10 and 50 (exclusive), use :code:`10..50`
* to filter everything between 10 and 50 (inclusive), use :code:`10...50`

For string columns, partial match is adopted. For example, :code:`CH3` (no quotation) will return entries containing the "CH3" string.

The "Shifted Frequency" column is computed based on the user input of a velocity or a redshift. This "Shifted Frequency" is adopted for line ID overlay on a spectral profiler widget. Users can use the checkbox to select a set of lines to be overplotted on a spectral profiler widget. The maximum number of line ID overlay is 1000.


.. raw:: html

   <img src="_static/carta_fn_linequery_widget.png" 
        style="width:100%;height:auto;">


The text labels of the line ID overlay are shown dynamically based on the zoom level of a profile. Different line ID overlays (with different velocity shifts) can be created on different spectral profilers widgets via the "Spectral Profiler" dropdown. By clicking the "Clear" button, the line ID overlay on the selected "Spectral Profiler" will be removed.

.. note::
   The sorting function in the line table will be available in a future release.

.. note::
   When there are multiple profiles from different image cubes in the plot and the x-axis is in velocity, the line ID overlay function is disabled. This limitation will be removed in a future release.



Stokes analysis widget
----------------------
Stokes analysis widget allows users to view basic polarization quantities of a multi-channel (number of channel > 1) cube with multi-Stokes (IQU, QU, or IQUV) efficiently. If different Stokes images are stored as individual files (i.e., image_I.fits, image_Q.fits, image_U.fits, and image_V.fits), users can use the file browser dialogue to create a Stokes hypercube by selecting multiple Stokes images and clicking the "Load as hypercube" button. Effectively, users will see that there is only one image loaded with multiple Stokes in CARTA. 


The widget includes the following plots:

* Stokes Q intensity and Stokes U intensity over the spectral axis
* Linearly polarized intensity over the spectral axis
* Linear polarization angle over the spectral axis
* Stokes Q intensity versus Stokes U intensity as a scatter plot

The profiles can be zoomed and panned with a mouse similar to the spatial profile widget or the spectral profile widget (:ref:`mouse_interaction_with_charts`). The Stokes Q versus Stokes U scatter plot is color-encoded from red to blue with increasing frequencies. The profiles can be requested at the cursor position (single pixel) or over a region of interest. Fractional polarization quantities are also supported if Stokes I is available. Examples are given in the following figures. The first one is from real ALMA data, while the second one is from an artificial Stokes cube. 

.. raw:: html

   <img src="_static/carta_fn_Stokes_widget.png" 
        style="width:100%;height:auto;">


.. raw:: html

   <img src="_static/carta_fn_Stokes_widget2.png" 
        style="width:100%;height:auto;">

When profiles are zoomed, the scatter plot will highlight those channels remaining in the profile view. Similarly, when the scatter plot is zoomed, the profile plot will highlight those channels remaining in the scatter plot view.

.. raw:: html

   <video controls style="width:100%;height:auto;">
     <source src="_static/carta_fn_stokesLinkedPlot.mp4" type="video/mp4">
   </video>

Additional options to customize the plots in the Stokes analysis widget are provided in the settings dialogue which can be launched by clicking the "cog" icon at the top-right corner. With the options in the dialogue, users can configure the appearance of the profile plots and the scatter plot. Optionally, profile smoothing can be applied with the Smoothing tab (see section :ref:`profile_smoothing`). A shortcut button to the Smoothing tab can be found at the top-right corner of the Stokes analysis widget.

.. raw:: html

   <img src="_static/carta_fn_Stokes_settings.png" 
        style="width:100%;height:auto;">


Statistics widget
-----------------
Statistics widget allows users to view statistics with respect to a selected region and a selected image. The following statistic quantities are currently supported:

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

The "Region" dropdown menu and the "Image" dropdown menu can be used to select which region statistics from which image to be displayed. The default is "Active" which means the current active (selected) region and the current image in the image viewer. If no region is active, it defaults to the entire image of the displayed channel to compute statistics. Multiple statistics widgets can be created to display statistics of different regions as demonstrated below.

.. raw:: html

   <img src="_static/carta_fn_statistics_widget.png" 
        style="width:100%;height:auto;">

The statstics table can be exported as a text file with the "export data" button at the bottom-right corner when hovering over the widget. 

.. note::
   A Stokes dropdown menu, allowing users to set a Stokes value without using the Stokes slider of the animator widget, will be added in a future release.


Histogram widget
----------------
Histogram widget allows users to visualize image data as a histogram with respect to a selected region and a selected image. The "Image" dropdown menu and the "Region" dropdown menu can be used to select which region histogram from which image to be displayed. The default is "Active" which means the current active (selected) region and the current image in the image viewer. If no region is active, it defaults to the entire image of the displayed channel to construct a histogram. Multiple histogram widgets can be created to display histograms of different regions as demonstrated below. 

.. raw:: html

   <img src="_static/carta_fn_histogram_widget.png" 
        style="width:100%;height:auto;">

Additional options to customize the histogram in the histogram widget are provided in the settings dialogue which can be launched by clicking the "cog" icon at the top-right corner. 

.. raw:: html

   <img src="_static/carta_fn_histogram_settings.png" 
        style="width:100%;height:auto;">


.. note::
   With v2.0, histogram bin width and bin count are automatically decided. Enhancement of the histogram widget, including histogram fitting, will be available in a future release. 

   A Stokes dropdown menu, allowing users to set a Stokes value without using the Stokes slider of the animator widget, will be added in the a future release.


Catalog widget
--------------
The catalog widget allows users to visualize a source catalog in VOTable or FITS format as

* image overlay
* 2D scatter plot
* histogram

Please refer to the section :ref:`catalog_widget` for details.