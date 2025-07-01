.. _vectorrendering:

Vector field rendering
======================

A vector overlay can be added to the Image Viewer from a vector field derived from an image, such as a linear polarization field or a magnetic field, or from a scalar field derived from an image, such as a temperature field or a column density field via the Vector Overlay Configuration Dialog.  

.. raw:: html

   <img src="_static/carta_fn_vectorOverlay.png" 
        style="width:100%;height:auto;">

There are different ways to configure how a vector element is derived from the "**Data source**" via the "**Angular source**" and the "**Intensity source**" dropdown menus:

1. For visualization of linear polarization from a Stokes IQU or QU cube with *variable* vector length and angle, set the "**Angular source**" to "Computed PA" and set the "**Intensity source**" to "Computed PI".
2. For visualization of linear polarization from a Stokes IQU or QU cube with *fixed* vector length and variable angle, set the "**Angular source**" to "Computed PA" and set the **"Intensity source**" to "None".
3. For visualization of linear polarization from a pre-computed position angle image in degrees, set the "Angular Source" to "Current image" and set the "**Intensity source**" to "None". 
4. For visualization of a scalar field by interpreting pixel value as the strength or intensity, set the "**Angular source**" to "None" and set the "**Intensity source**" to "Current image". This mode renders a filled square marker instead of a line segment.

See the figure below for examples of the four vector overlay rendering modes.

.. raw:: html

   <img src="_static/carta_fn_vectorOverlay_examples.png" 
        style="width:100%;height:auto;">



Usually, block smoothing is applied to the "**Data source**" image to enhance the signal-to-noise ratio before computing vector elements. You can enable the "**Pixel averaging**" toggle (enabled by default) and set the "**Averaging width (px)**" (default 4 pixels by 4 pixels) to apply pixel averaging. 

When the "**Intensity source**" is "Computed PI", you can select "Absolute" or "Fractional" polarization intensity with the "**Polarization intensity**" radio buttons. A threshold for Stokes I may be applied to mask out noisy parts of the image with the "**Threshold**" field when the "**Threshold enabled**" toggle is switched on. If Stokes I is unavailable (i.e., the input image has Stokes Q and U only), the threshold is applied to Stokes Q and U to construct a mask. Optionally, you may apply "debiasing" to the polarization intensity and angle calculations by enabling the "**Debiasing**" toggle and set errors for Stokes Q and U in the "**Stokes Q error**" and the "**Stokes U error**" fields, respectively.

.. raw:: html

   <img src="_static/carta_fn_vectorOverlay_threshold.png" 
        style="width:100%;height:auto;">


Once the control parameters of how a vector overlay is computed are set, you can click the "**Apply**" button to trigger the computation and rendering process. The vector overlay data will be streamed incrementally similarly to the raster rendering with image tiles. Click the "**Clear**" button to remove the vector overlay.

On spatially matched images, vector elements are reprojected precisely based on the projection schemes. This behaves the same as the contour overlay and catalog image overlay. You can use the Image List Widget to trigger image matching. 

.. raw:: html

   <img src="_static/carta_fn_vectorOverlayMatching.png" 
        style="width:100%;height:auto;">


With the "**Styling**" tab, you can configure how vector elements are rendered, including:

* line thickness
* intensity to vector length mapping
* additional rotation offset to vector angle
* color modes of vector elements


For example, you may use the options to plot a vector overlay like below. Vector elements are rendered in different colors to represent the relative strength of the linear polarization intensity. An angle offset of 90 degrees is applied to the vector elements to *infer* the magnetic field morphology. 

.. raw:: html

   <img src="_static/carta_fn_vectorOverlayStyling.png" 
        style="width:100%;height:auto;">
