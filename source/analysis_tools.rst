Image cube analysis tools
=========================
With version 1.4, CARTA provides the following widgets and tools for image cube analysis:

* Widget
  
  * Region list: to view and configure region properties
  * Spatial profiler: to view x and y spatial profiles at the cursor position
  * Spectral profiler: to view spectral profile from a region of interest
  * Histogram: to view histogram from a region of interest
  * Statistics: to view basic statistics from a region of interest
  * Stokes analysis: to view basic polarization quantities
  * Spectral line query: to make a query to the Splatalogue service and create labels on a spectral profile plot
  * Catalogue widget: to visualize a catalogue as an image overlay, a 2D scatter plot, or a histogram

* Tool

  * Profile smoothing: to smooth a profile for a better S/N
  * Moment map generator: to collapse an image cube with various moments and statistics



Region of interest
------------------
As of v1.4, CARTA supports the following region types:

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

  If using CARTA remote mode in Firefox on MacOS, you may find the "**backspace**" key navigates back a page instead of removing a region. This behaviour can be prevented by modifying your Firefox web browser settings:

  1. Enter about:config in the address bar.
  2. Click "I accept the risk!"
  3. A search bar appears at the top of a long list of preferences. Search for "browser.backspace_action"
  4. It will likely have a value of 0. Double click it, and then modify it to a value of "2".
  5. Close the about:config tab and now backspace will no longer navigate back a page.

All created regions are listed in the region list widget with basic region properties. To select a region (region state changes to "selected"), simply click on the region in the image viewer, or click on the region in the region list widget. To modify the properties of a selected region, double-click on a region in the image viewer or a region in the region list widget. The color, line style, name, location, and shape, of a region are all configurable with the region configuration dialogue. The location and shape properties can be edited in the image coordinate, or in the world coordinate with angular scales (default). To de-select a region or cancel a region creation process, press "**esc**" key. To delete a selected region, press "**delete**" or "**backspace**" key. The activated region can be locked by pressing "**L**" key or by clicking the "lock" icon in the region list widget or region property dialogue. When a region is locked, it cannot be modified (resize, move, or delete) with mouse actions and the "**delete**" or "**backspace**" key. A locked region, however, can still be modified or deleted via the region configuration dialogue. Locking a region could help the situation when users want to modify overlapping regions, or could prevent modifying a region accidentally. The "center" icon is to show the corresponding region at the center of image view. 

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
Shared region of interest enables practical image cube analysis through statistics, histogram, spectral profiler, and Stokes analysis widgets. These widgets contains an image dropdown menu and a region dropdown menu. The former allows users to select which loaded image cube to show its analytics. The latter allows users to select which region to show the region analytics. With the combination of the two menus, CARTA provides a flexible user interface to explore image data. As an example below, three image cubes representing 12CO 2-1, 13CO 2-1, and C18O 2-1 are matched spatially and spectrally. Three shared regions are created to highlight different features. Three spectral profiler widgets are placed to show different profiles. The top one shows the square region profile from 12CO 2-1. The middle one shows the ellipse region profile of 13CO 2-1. The bottom one shows the circle region profile from C18O 2-1. 


.. raw:: html

  <img src="_static/carta_fn_roi_sharedRegion_analytics.png" 
      style="width:100%;height:auto;">

Alternatively, users may use multiple widgets to show analytics from different regions of the same image, or show analytics of a shared region from different matched images, or the mix of the two scenarios as the example above.

The image dropdown menu will be highlighted with a blue box if the selected image is currently displayed in the image viewer. The region dropdown menu will be highlighted with a blue box too if the selected region is currently selected (with control points displayed) in the image viewer. 


Region import and export
^^^^^^^^^^^^^^^^^^^^^^^^
As of v1.4, CARTA supports basic region import and export capability. Regions, in world coordinate or in image coordinate, can be exported to a text file or imported from a text file. To import a region file, use the menu **File** -> **Import regions**. 

.. raw:: html

   <img src="_static/carta_fn_regionImport.png" 
        style="width:100%;height:auto;">

To export regions to a region file, use the menu **File** -> **Export regions**. All regions, except cursor, will be exported. 

.. raw:: html

   <img src="_static/carta_fn_regionExport.png" 
        style="width:100%;height:auto;">

As of v1.4, CASA region text format (.crtf) and ds9 region text format (.reg) are supported with some limitations. Currently only the 2D region definition is supported. Other properties, such as spectral range or reference frame will be supported in future releases.  

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

When displaying a spatial profile with the number of pixels more than the number of screen pixels of the spatial profiler widget, a *decimated* profile will be derived and displayed to users as an enhancement of performance. Min/max decimation of a profile is adopted to ensure profile features are preserved. In other words, positive and negative peaks should stay at the same screen pixels just like displaying the full resolution profile. When users keep zooming in the profile, decimation with narrower and narrower interval is applied dynamically. Full resolution profile is displayed when the number of screen pixels is more than the number of pixels of the profile to be displayed.  

The interactions of the spatial profiler widget are demonstrated in the section :ref:`mouse_interaction_with_charts`. The red vertical bar indicates the pixel where the profile is taken. The bottom axis shows the image coordinate, while optional world coordinate is displayed on the top axis. Extra options to configure the profile plot are available in the spatial profiler settings dialogue which is launched by clicking the "cog" icon at the top-right corner. The option "Show Mean/RMS" in the Styling tab will adopt the data in the current view to derive a mean value and an rms value, and visualize the results on the plot. Numerical values are also displayed at the bottom-left corner. Optionally, the profile can be smoothed with different methods provided in the Smoothing tab (see section :ref:`profile_smoothing`). The profile can be exported as a png image or a text file in tsv format via the buttons at the bottom-right corner when hovering over the plot.

When the cursor is on the image in the image viewer, the pointed pixel value (pixel index and pixel value) will be displayed at the bottom-left corner of the spatial profiler. When the cursor is on the spatial profiler graph, the pointed profile data will be displayed instead. 



.. raw:: html

   <img src="_static/carta_fn_spatialProfiler_widget.png" 
        style="width:100%;height:auto;">

.. note::
   In future release, the following features will be supported:
   
   * More flexibilities on how mean and rms values are derived in the plot
   * Profile fitting capability 
   * Profile along a line segment, polyline, or an arbitary curve  


Spectral profiler
-----------------
Spectral profiler provides the spectral profile of the current image cube at the selected region. The default region is set to "Cursor". The "**F**" key will disable or enable cursor profile update. When cursor update is disabled, a marker "+" will be placed on the image to indicate the position of the profile taken. 

When requesting a spectral profile, a common disappointing user experience is that users may have to wait for an unknown amount of time to see the final result if the image cube is large. As an improvement on this aspect, CARTA supports *progressive update* of spectral profile. Partial profiles will be periodically delivered to users while the full profile calculations are still ongoing. 

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_spectralProfiler_partialUpdate.mp4" type="video/mp4">
   </video>


When the property of a region (cursor or a regular region) is modified while the profile of the original region is being updated, the partial profile will disappear and a new partial profile cooresponding to the new region will start updating. If users modify the request of a spectral profile via the spectral profile widget before it is fully delivered, the original profile calculations will be cancelled and new profile calculations will start. In short, CARTA should just focus on calculating and showing the profiles that users pay attention to. If a profile is no longer needed to be shown on the screen, the profile calculation will be cancelled immediately, instead of blocking and queueing up new profile requests. 


.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_spectralProfiler_profileCancellation.mp4" type="video/mp4">
   </video>

When displaying a spectral profile with the number of channels more than the number of screen pixels of the spectral profiler widget, a *decimated* profile will be derived and displayed to users as an enhancement of performance. Min/max decimation of a profile is adopted to ensure profile features are preserved. In other words, positive and negative peaks should stay at the same screen pixels just like displaying the full resolution profile. When users keep zooming in the profile, decimation with narrower and narrower interval is applied dynamically. Full resolution profile is displayed when the number of screen pixels is more than the number of pixels of the profile to be displayed. 

When regions are created, the spectral profiler widget can be configured to display a profile from a specific region with the "*Region*" dropdown menu. The default of the "*Region*" dropdown is "Active" which points to the current active (selected) region. If no region is active, it defaults to cursor region. Additional statistic types to compute the region spectral profile are available with the "*Statistic*" dropdown menu (default to mean). If the image cube has multiple Stokes, the "*Stokes*" dropdown menu will be activated and defaulted to "Current" which is synchronized with the selection in the animator. To view a specific Stokes, select with the "*Stokes*" dropdown menu.

Multiple spectral profile widgets can be configured to display different region ("*Region*" dropdown menu) spectral profiles from different image cubes ("*Image*" dropdown menu) and Stokes ("*Stokes*" dropdown menu, if applicable) with different statistics ("*Statistic*" dropdown menu).

.. raw:: html

   <img src="_static/carta_fn_spectralProfiler_multiwidget.png" 
        style="width:100%;height:auto;">

The interactions of the spectral profiler widget are demonstrated in the section :ref:`mouse_interaction_with_charts`. The red vertical bar indicates the channel of the image displayed in the image viewer. Clicking directly on the spectral profiler graph will change the displayed image to the clicked channel. Alternatively, the red vertical bar is draggable and acts just like the channel slider of the animator widget. 

The bottom axis shows the spectral coordinate. Additional options to configure the profile plot are available in the spectral profile settings dialogue which can be launched by clicking the "cog" icon in the top-right corner. In the dialogue, users may select a different spectral convention (e.g., optical velocity) and a different reference system (e.g., TOPO) with the Conversion tab. The option "Show Mean/RMS" in the Styling tab will adopt the data in the current view to derive a mean value and an rms value, and visualize the results on the plot. Numerical values are also displayed at the bottom-left corner. When the cursor is on the image in the image viewer, the pointed pixel value (frequency or velocity or channel index, and pixel value) will be displayed at the bottom-left corner of the spectral profiler. When the cursor is on the spectral profiler graph, the pointed profile data will be displayed instead. Optionally, the displayed profile can be smoothed via the options in the Smoothing tab (see section :ref:`profile_smoothing`). Image collapsing is available in the Moments tab. Various image moments and statistics are supported (see section :ref:`moment_generator`). The profile can be exported as a png image or a text file in tsv format via the buttons at the bottom-right corner.

.. raw:: html

   <img src="_static/carta_fn_spectralProfiler_widget.png" 
        style="width:100%;height:auto;">


.. note::
   In future releases, the follow features will be supported:
   
   * More flexibilities on how mean and rms values are derived
   * Profile fitting
   * Intensity unit conversion


.. _moment_generator:

Moment map generator
--------------------
Moment images can be generated and viewed with CARTA. A shortcut button, linking to the Moments tab of the settings dialogue, can be found at the top-right corner of the spectral profiler widget.

.. raw:: html

   <img src="_static/carta_fn_momentGenerator_tool.png" 
        style="width:100%;height:auto;">

The Moments tab provides several control parameters to define how moment images are calculated, including:
                
* Image: the image file for moment calculations. "Active" refers to the image displayed in the image viewer.
* Region: a region can be selected so that moment calculations are limited inside the region. "Active" refers to the selected region in the image viewer. If no region is selected, full image is included in the moment calculations.
* Coordinate, System, and Range: the spectral range (e.g., velocity range) used for moment calculations is defined with these options. The range can be defined either via the text input fields, or via the cursor by dragging horizontally in the spectral profiler widget.
* Mask and Range: these options define a pixel value range used for moment calculations. If mask is "None", all pixels are included. If mask is "Include" or "Exclude", the pixel value range defined in the text input fields is included or excluded, respectively. Alternatively, the pixel value range can be defined via the cursor by dragging vertically in the spectral profiler widget.
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


When all the parameters are defined, by clicking the "Generate" button moment calculations will begin. Depending on the file size, moment calculations may take a while. If that happens, users may consider to cancel the calculations and re-define a proper region and/or spectral range.

Once moment images are generated, they will be loaded and displayed in the image viewer. They are named as $image_filename.moment.$keyword. For example, if moment 0, 1 and 2 images are generated from the image M51.fits, they will be named as *M51.fits.moment.integrated*, *M51.fits.moment.weighted_coord*, and *M51.fits.moment.weighted_dispersion_coord*, respectively. These images are kept in RAM per session and if there is a new request of moment calculations, these images will be deleted first. Optionally, calculated moment images can be exported in CASA or FITS format via **File** -> **Save image**.

.. raw:: html

   <img src="_static/carta_fn_momentGenerator_tool2.png" 
        style="width:100%;height:auto;">

                
.. note::
   Due to a CASA issue, image of "Median coordinate" cannot be generated. The request of "Median coordinate" is ignored automatically.



Spectral line query
-------------------
CARTA supports an *initial* implementation of spectral line ID overlay on a spectral profiler widget with a query to the Splatalogue service (https://splatalogue.online). The query is made by defining a spectral range in frequency or wavelength and optionally a lower limit of CDMS/JPL line intensity (log). The spectral range can be defined as from-to or a center with a width.

.. note::
   The current implementation has some limitations when making a query to the Splatalogue service:

   * The allowed maximum query range, equivalent in frequency, is 20 GHz.
   * The actual query is made with a frequency range in MHz rounded to integer.
   * When an intensity limit is applied, only the lines from CDMS and JPL catalogues will be returned.
   * Up to 100000 lines are displayed. 

   Improvements of the above limiations will be made in future releases.

   Currently, the Splatalogue query service is under active development. Unexpected query results might happen. When users believe there is something wrong, please contact `the CARTA helpdesk <mailto:carta@asiaa.sinica.edu.tw>`_, or file an issue on `Github <https://github.com/CARTAvis/carta/issues>`_ (recommended).  


Once a query is successfully made, the line catalogue will be displayed in the tables. The upper table shows the column information in the catalogue with options to show or hide a specific column. The actual line catalogue is displayed in the lower table.

The "Shifted Frequency" column is computed based on the user input of a velocity or a redshift. This "Shifted Frequency" is adopted for line ID overlay on a spectral profiler widget. Users can use the checkbox to select a set of lines to be overplotted on a spectral profiler widget. The maximum number of line ID overlay is 1000.


.. raw:: html

   <img src="_static/carta_fn_linequery_widget.png" 
        style="width:100%;height:auto;">


The text labels of the line ID overlay are shown dynamically based on the zoom level of a profile. Different line ID overlays (with different velocity shifts) can be created on different spectral profilers widgets via the "Spectral Profiler" dropdown. By clicking the "Clear" button, the line ID overlay on the selected "Spectral Profiler" will be removed.

.. note::
   The sorting and filtering functions in the line table will be available in the next release (v1.5).





Stokes analysis widget
----------------------
Stokes analysis widget allows users to view basic polarization quantities of a multi-channel (number of channel > 1), multi-Stokes (IQU or IQUV) cube efficiently. The widget includes the following plots:

* Stokes Q intensity and Stokes U intensity over the spectral axis
* Linearly polarized intensity over the spectral axis
* Linear polarization angle over the spectral axis
* Stokes Q intensity versus Stokes U intensity

The profiles can be zoomed and panned with mouse similar to the spatial profile widget or the spectral profile widget (:ref:`mouse_interaction_with_charts`). The Stokes Q versus Stokes U scatter plot is color-encoded from red to blue with increasing frequencies. The profiles can be requested at the cursor position (single pixel) or over a region of interest. Fractional polarization quantities are also supported. Examples are given in the following figures. The first one is from real ALMA data, while the second one is from an artifical Stokes cube. 

.. raw:: html

   <img src="_static/carta_fn_Stokes_widget.png" 
        style="width:100%;height:auto;">


.. raw:: html

   <img src="_static/carta_fn_Stokes_widget2.png" 
        style="width:100%;height:auto;">

When profiles are zoomed, the scatter plot will highlight those channels remaining in the profile view. Similarly, when scatter plot is zoomed, the profile plot will highlight those channels remaining in the scatter plot view.

.. raw:: html

   <video controls loop style="width:100%;height:auto;">
     <source src="_static/carta_fn_stokesLinkedPlot.mp4" type="video/mp4">
   </video>

Additional options to customize the plots in the Stokes analysis widget are provided in the settings dialogue which can be launched by clicking the "cog" icon at the top-right corner. 

.. raw:: html

   <img src="_static/carta_fn_Stokes_settings.png" 
        style="width:100%;height:auto;">





.. _profile_smoothing:

Profile smoothing
-----------------
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX




Statistics widget
-----------------
Statistics widget allows users to see statistics with respect to a selected region. The "Region" dropdown menu can be used to select which region statistics to be displayed. The default is "Active" which means the current active (selected) region. If no region is active, it defaults to the entire image of the displayed channel to compute statistics. Multiple statistics widgets can be created to display statistics of different regions as demonstrated below. The widget with the selected region will be highlighted with a persistent blue box. 

.. raw:: html

   <img src="_static/carta_fn_statistics_widget.png" 
        style="width:100%;height:auto;">



Histogram widget
----------------
Histogram widget allows users to visualize data in a histogram with respect to a selected region. The "Region" dropdown menu can be used to select which region histogram to be displayed. The default is "Active" which means the current active (selected) region. If no region is active, it defaults to the entire image of the displayed channel to construct a histogram. Multiple histogram widgets can be created to display histograms of different regions as demonstrated below. The widget with the selected region will be highlighted with a persistent blue box.

.. raw:: html

   <img src="_static/carta_fn_histogram_widget.png" 
        style="width:100%;height:auto;">

Additional options to customize the histogram in the histogram widget are provided in the settings dialogue which can be launched by clicking the "cog" icon at the top-right corner. 

.. raw:: html

   <img src="_static/carta_fn_histogram_settings.png" 
        style="width:100%;height:auto;">


.. note::
   With v1.3, histogram bin width and bin count are automatically decided. Enhancement of the histogram widget, including histogram fitting, will be available in future releases. 



Catalogue widget
----------------
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX