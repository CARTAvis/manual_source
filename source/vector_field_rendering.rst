.. _vector_rendering:

Vector field rendering
======================

You can add a vector overlay to the Image Viewer using the Vector Overlay Configuration Dialog. This allows you to visualize vector fields derived from images, such as linear polarization or magnetic fields, as well as scalar fields like temperature or column density.

.. raw:: html

   <img src="_static/carta_fn_vectorOverlay.png" 
        style="width:100%;height:auto;">

The Vector Overlay Configuration Dialog contains a Data source dropdown menu to select the image from which the vector elements are derived. The Configuration tab contains several options to configure how the vector elements are computed. The dialog also has a Styling tab to configure how the vector elements are rendered.

.. note::
   The vector overlay layer in the Image Viewer Widget may be hidden by clicking the "V" button in the Layers column of the Image List widget. When the vector overlay layer of a given image is hidden, the same vector overlay layer on all the other spatially matched images will also be hidden.


Rendering modes
---------------

There are different ways to configure how a vector element is derived from the "**Data source**" via the "**Angular source**" and the "**Intensity source**" dropdown menus:

1. For visualization of linear polarization from a Stokes IQU or QU cube with *variable* vector length and angle, set the "**Angular source**" to "Computed PA" and set the "**Intensity source**" to "Computed PI".
2. For visualization of linear polarization from a Stokes IQU or QU cube with *fixed* vector length and variable angle, set the "**Angular source**" to "Computed PA" and set the **"Intensity source**" to "None".
3. For visualization of linear polarization from a pre-computed position angle image in degrees, set the "Angular Source" to "Current image" and set the "**Intensity source**" to "None". 
4. For visualization of a scalar field by interpreting pixel value as the strength or intensity, set the "**Angular source**" to "None" and set the "**Intensity source**" to "Current image". This mode renders a filled square marker instead of a line segment.

See the figure below for examples of the four vector overlay rendering modes.

.. raw:: html

   <img src="_static/carta_fn_vectorOverlay_examples.png" 
        style="width:100%;height:auto;">

Smoothing
---------

Usually, block smoothing is applied to the "**Data source**" image to enhance the signal-to-noise ratio before computing vector elements. You can enable the "**Pixel averaging**" toggle (enabled by default) and set the "**Averaging width (px)**" (default 4 pixels by 4 pixels) to apply pixel averaging. 


Absolute and fractional polarization intensity
----------------------------------------------

When the "**Intensity source**" is "Computed PI", you can select "Absolute" or "Fractional" polarization intensity with the "**Polarization intensity**" radio buttons. Fractional polarization intensity is computed as the ratio of the polarization intensity to the total intensity (Stokes I) and is expressed in percentage. Absolute linear polarization intensity is computed as the square root of the sum of squares of Stokes Q and U, which is expressed in the same unit as Stokes I. Absolute total polarization intensity is computed as the square root of the sum of squares of Stokes Q, U, and V.


Thresholding and debiasing
--------------------------

A threshold for Stokes I may be applied to mask out noisy parts of the image with the "**Threshold**" field when the "**Threshold enabled**" toggle is switched on. When threshold is enabled, an option is provided to select which component as the target for thresholding. Possible use cases include:

* If Stokes IQU or IQUV is available, you can set Stokes I or Computed PI as the target for thresholding. 
* If Stokes QU or QUV is available, Computed PI is the target for thresholding.
* If no Stokes is available, the current image is used as the target for thresholding.

Optionally, you may apply "debiasing" to the polarization intensity and angle calculations by enabling the "**Debiasing**" toggle and set errors for Stokes Q and U in the "**Stokes Q error**" and the "**Stokes U error**" fields, respectively.

.. raw:: html

   <img src="_static/carta_fn_vectorOverlay_threshold.png" 
        style="width:100%;height:auto;">


Adding and removing vector overlays
-----------------------------------

Once the control parameters of how a vector overlay is computed are set with the Configuration tab, you can click the "**Apply**" button to trigger the computation and rendering process. The vector overlay data will be streamed incrementally similarly to the raster rendering with image tiles. Click the "**Clear**" button to remove the vector overlay.



Matching vector overlay images to raster images
-----------------------------------------------

Suppose you want to plot a vector overlay image on top of another raster image (e.g., linear polarization field as vectors, linear polarized intensity image as raster). In that case, you need to enable WCS matching of the two raster images first (see :ref:`wcs_matching`). Then, you can generate a vector overlay image just like the example below. The vector overlay images will be visible on *all* the images that are matched to the spatial reference image in world coordinates, including the spatial reference image itself. On spatially matched images, vector elements are reprojected precisely based on the projection schemes. This behaves the same as the contour overlay and catalog image overlay.

.. raw:: html

   <img src="_static/carta_fn_vectorOverlayMatching.png" 
        style="width:100%;height:auto;">

If multiple images are loaded in the append mode, you may use the "**Data Source**" dropdown menu to select an image as the input data for vector overlay calculations.



Styling vector overlays
-----------------------

With the "**Styling**" tab, you can configure how vector elements are rendered, including:

* line thickness
* intensity to vector length mapping
* additional rotation offset to vector angle
* color modes of vector elements

For example, you may use the options to plot a vector overlay like below. Vector elements are rendered in different colors to represent the relative strength of the linear polarization intensity. An angle offset of 90 degrees is applied to the vector elements to *infer* the magnetic field morphology. 

.. raw:: html

   <img src="_static/carta_fn_vectorOverlayStyling.png" 
        style="width:100%;height:auto;">
