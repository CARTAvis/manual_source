Appendix A: version history
===========================

Version 3.0
-----------
Released 23rd August 2022

* Vector overlay rendering
* Loading images with the Lattice Expression Language (LEL)
* Loading CASA images with pixel values as complex numbers
* Initial implementation of image 2D Gaussian fitting
* Generating computed polarization quantities (eg. linear polarization intensity) of a Stokes cube on the fly
* Setting a new rest frequency when saving a subimage
* Logging moment map generation information in header history
* Line and polyline region spectral profiler
* Initial implementation of PV image generator
* Image file list filter
* High-resolution PNG export
* Enhanced spectral matching mode
* Custom rest frequency for velocity conversion
* Performance boost when loading a region file with massive amount of regions
* Telemetry
* Online catalog query from SIMBAD and VizieR
* Region export and import enhancement
* Initial implementation of intensity unit conversion
* Multiple panel view
* Pixel grid border rendering at high zoom levels
* Interactive raster rendering with a cutoff via the interactive colorbar
* Distance measuring tool
* Spatial profiler widget enhancement
* Histogram and statistics widget enhancement
* Cursor info widget
* Code snippets (experimental feature)
* Support gzipped FITS images (fits.gz and fz)
* HDF5 mip map support
* Remember last used directory

Performance enhancement and bug fixes are included as well.


Version 2.0
-----------
Released 7th June 2021

* Multi-profile plot with the spectral profiler
* Progress report and cancellation when requesting a long file list
* Forming a Stokes hypercube at image loading stage
* Colorbar display in the image viewer and enhanced raster image config widget
* Support rectangular pixel rendering for PV image
* Filtering function in the spectral line query widget
* Enhanced FITS and CASA image support
* Saving subimage
* Searching a keyword from image header
* Profile fitting in the spectral profiler 
* Marker-based catalog rendering and performance enhancement
* New deployment modes

Performance enhancement and bug fixes are included as well.


Version 1.4
-----------
Released 17th September 2020

* Catalogue support
* Shared region analytics
* Animation playback improvement of raster and contour images
* Profile smoothing
* Moment map generator
* Spectral line query
* Server authentication and deployment improvements
* File browser improvements

Performance enhancement and bug fixes are included as well.


Version 1.3.1
-------------
Released 5th May 2020

Bug fixes

* Truncated header values in HDF5 images.
* Crashes when creating a region on a single channel image while the spectral profiler is launched.
* Hanging when requesting statistics.
* Correct axes labeling in region widget.
* Swapped major/minor axes of ellipse when exporting as region file.
* Incorrect or inaccurate angular size of rectangle and ellipse regions in the region dialog.
* Server version database fix.


Version 1.3
-----------
Released 31th March 2020

* Contour rendering
* Matching images in world coordinates
* Support "Active" region type in analytics widgets
* Enhanced remote mode for desktop version
* Spectral conversion in the spectral profiler
* Tiled animation
* In-app help manual 

Performance enhancement and bug fixes are included as well.


Version 1.2.2
-------------
Released 3rd January 2020

* Critical bug fix


Version 1.2.1
-------------
Released 30th October 2019

* Support region import/export in ds9 syntax
* Critical bug fix

Version 1.2
-----------
Released 28th August 2019

This release includes the following new features:

* New server authentication method
* User preferences and layouts
* Tiled rendering and animator enhancement
* support point and polygon regions
* support region import/export in crtf syntax
* introducing enhanced profile delivery strategies 
* new Stokes analysis widget
* support HDF5 images under IDIA schema

Performance enhancement and bug fixes are included as well.


Version 1.1
-----------
Released 2nd May 2019.


Initial support of region of interest and the HDF5-IDIA image format.

This version enables the initial support of region of interest and relevant analysis tools (statistics, histogram, region spectral profiler). Initial support of the HDF5-IDIA image format is implemented, which takes the advantage of pre-calculated data and rotated cube to speed up some time-consuming tasks. A basic server-side authentication model and command line startup options are provided. Performance enhancement and bug fixes are included as well.



Version 1.0.1
-------------
Released 6th March 2019.

Patch release of version 1.0. 

With version 1.0.1 patch release, CARTA futher provides enhanced file browser navigation capability, remote server (backend) status icon, improvements of file information and header, and displaying data values in the spatial and the spectral profilers. 


Version 1.0
-----------
Released 29th December 2018.

Initial release. 

This version provides basic image viewing capabilities, basic profile viewing capabilities in both spatial and spectral domains, and basic per-frame or per-cube histogram viewing capabilities. Exporting images or charts in png format and charts in plain text format are supported. 


