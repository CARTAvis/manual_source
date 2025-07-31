.. _pv_generator:

Position-velocity image generator
=================================

The PV Generator has two operation modes:

* Production mode: A full-resolution PV image is computed from the full-resolution image cube, suitable for detailed analysis.
* Preview mode: A downsampled preview PV image is computed from the downsampled image cube on the fly when the PV cut moves, suitable for real-time interactive feature exploration.

Production mode
---------------

When studying source kinematics, it is common to utilize a position-velocity (PV) image. You can generate a PV image with the PV Generator Widget from the widget bar. Line region and polyline region are supported as the PV cut. When a line region is selected, the resulting "position" axis is "offset", while when a polyline region is selected, the resulting "position" axis is "distance".

.. raw:: html

   <a href="_static/carta_fn_pvGenerator.png" target="_blank">
       <img src="_static/carta_fn_pvGenerator.png" 
           style="width:100%;height:auto;">
   </a>

A line region or a polyline region must be selected from the "**PV cut**" dropdown menu to generate a PV image. A spectral range (flexible in spectral convention) can be defined with the "**Range**" input fields to focus on the features in interest to save computation time. The axes order (position vs. velocity or velocity vs. position) of the PV image can be configured as well. You can click the "**Generate**" button to start the PV image generation process. A progress bar will be displayed with a "**Cancel**" button during the PV image generation process. The process can be canceled at any time. 

Once a PV image is generated, it will be loaded and displayed in the Image Viewer. It is named with an additional :code:`_pv` string in the original input file name.  The generated PV image is kept in RAM per session, and if there is a new request for PV image generation, the old PV image will be deleted first. If you want to regenerate a PV image but keep the old one, you can enable the "**Keep previous PV image(s)**" toggle. Optionally, a calculated PV image can be exported in CASA or FITS format via "**File**" -> "**Save Image**".

.. note::
   Viewing a position-velocity image

   CARTA switches to using *rectangular* pixels for rendering when a position-velocity image is loaded as a raster image. The pixel aspect ratio is dynamic based on the aspect ratio of the Image Viewer Widget. By default, the "spectral" axis is displayed in velocity, if possible, based on the image header. You may use the Image Viewer Settings Dialog to apply a conversion to other spectral conventions, such as frequency or wavelength. The frequency-to-velocity conversion requires a reference rest frequency. This reference rest frequency is derived from the image header. You may use the settings dialog of the Image List Widget to set a new reference rest frequency to recompute the velocity axis.

   .. raw:: html

      <a href="_static/carta_fn_imageviewer_pv_rendering.png" target="_blank">
          <img src="_static/carta_fn_imageviewer_pv_rendering.png" 
               style="width:100%;height:auto;">
      </a>

.. warning::
   In a resumed session after a broken connection to the backend, all in-memory images, such as those generated with the PV generator, are lost. Those images will not be accessible in the resumed session.


Sampling process
^^^^^^^^^^^^^^^^

When a PV image is derived from a line region or a polyline region, a set of boxes with a “height” (parallel to the trajectory) of three unit steps and a custom “width” (perpendicular to the trajectory; set with the "**Averaging width**" input and spinbox) in the number of unit steps are created along the trajectory. These hidden boxes are created on the reference image first. Then, similar to the polygon approximation of closed regions, these "boxes" are transformed into the spatially matched secondary image to derive a PV image. The unit step refers to an image pixel if the image is “flat” without noticeable distortion. However, if the image is considered "wide" with noticeable distortion, the unit step refers to the angular size of an image pixel as defined in the image header. In this case, the boxes retain approximately a fixed solid angle. With all these approximations, PV images of the same trajectory can be compared directly among different spatially matched images. See also :ref:`spatial_profile_computation` for more details on the sampling process.

.. raw:: html

   <a href="_static/carta_fn_pvGenerator2.png" target="_blank">
       <img src="_static/carta_fn_pvGenerator2.png" 
           style="width:100%;height:auto;">
   </a>

As a scalable approach for large image cubes, CARTA constructs a PV image from a series of *region spectral profiles* along the PV cut, instead of re-gridding the input image cube first so that the PV cut becomes a horizontal one for the temporary cube. The final PV image is an ensemble of region spectral profiles at different sampled offset locations. 

.. note::

   When the sampling process is made along a line region in a "non-flat" image, the solid angle of the sampling boxes is approximately conserved. In some cases, especially when the image is highly distorted, some computed boxes may cover zero image pixels for spectral profile calculations. Therefore, you may see NaN stripes in the final PV image. When this happens, you can consider increasing the averaging "width" with the "**Averaging width**"  input and spinbox.

   In a future release, the averaging "height" (parallel to the trajectory) can be customized too. With the v5.0 release, the "height" is fixed to *three* (three pixels for flat image or three unit angular size for non-flat image). 



Preview mode
------------
The PV Generator supports a preview mode to explore the PV image interactively in real time. Only a line region is supported as the PV cut in the preview mode. 

As a scalable implementation, CARTA creates a downsampled image cube in RAM first, based on the configurations in the "**Preview region**" dropdown menu and the "**Preview rebin (px)**" inputs and spinboxes. The estimated memory usage of the downsampled cube is displayed in "**Preview cube size (MB)**". The upper limit is set to 1 GB as an experimental default (configurable up to 2 GB in the "**Performance**" tab of the Preferences Dialog). If the value exceeds the limit (displayed in red), you must reconfigure how the downsampled cube is constructed to use the preview mode. 

.. raw:: html

   <a href="_static/carta_fn_pvGenerator_preview.png" target="_blank">
       <img src="_static/carta_fn_pvGenerator_preview.png" 
           style="width:100%;height:auto;">
   </a>

By clicking the "**Start preview**" button, the PV Generator will enter the preview mode and launch a PV Preview Viewer Widget with a preview PV image derived from the downsampled cube along a line region as the PV cut. If you reconfigure the PV cut in the Image Viewer with the mouse, such as move, rotate, and resize, new preview PV images will be streamed in real-time. You can utilize this feature to explore your image cube and identify a PV cut configuration to generate a full-resolution PV image with the "**Generate**" button.

