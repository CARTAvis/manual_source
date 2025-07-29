.. _multicolor_blending:

Multi-color image blending
==========================

The multi-color image blending feature in CARTA allows users to visualize multiple images simultaneously by blending them together in the color space. This is particularly useful for comparing different datasets or visualizing multi-wavelength observations. The blending is done by assigning different colors to each image and then combining them to create a composite image. 

Unlike the conventional RGB blending, which uses red, green, and blue channels, CARTA allows for more color channels (>= 2) and more flexible color assignments (monocolor maps or usual colormaps). In addition, the blending is done at the *screen pixel* level instead of the *image pixel* level. This approach removes the limitations of the conventional RGB blending, such as the requirement for images to have the same pixel size and image size. The only requirement is that the images need to be matchable to each others in world coordinates.

The following is an example of blending three X-ray images with different energies each assigned to a different color channel to emulate an optical image. 


.. raw:: html

   <a href="_static/carta_fn_multicolor_blending_example.png" target="_blank">
       <img src="_static/carta_fn_multicolor_blending_example.png" 
            style="width:100%;height:auto;">
   </a>


.. note::
    If images are matchable in world coordinates but they have different projection schemes with noticeable spatial distortions, the blending may not produce the expected results. In such cases, it is recommended to reproject the images to a common projection scheme before blending.


Enabling multi-color blending
-----------------------------
There are two ways to enable multi-color blending in CARTA:

- Via the File Browser Dialog:

  This is the use case that you already know which images you want to blend together. You can select multiple images in the File Browser Dialog and then click the "Load with RGB blending" (2 or 3 images) or "Load with multi-color blending" (>3 images) button to load the selected images into the Image Viewer as well as an extra one as the blended image. In this mode, colors will be assigned automatically. You can further customize the colors using the Render Configuration Widget.

- Via the File menu: 
  
  This is the use case that you want to blend images that are already loaded in the Image Viewer. You can use "**File**" -> "**Multi-Color Blending**" to blend *matched* images. The color assignment for each image will be as it is before the blending. You can further customize the colors using the Render Configuration Widget for each image or use the "Apply color set" dropdown menu in the Render Configuration Widget when the blended image is active.


.. note::
    To close the multi-color blending image, you can use "**File**" -> "**Close Image**" or use the context menu (right-click) on the blended image in the Image List Widget and select "Close image". This will remove the blended image from the Image Viewer but will not affect the original images used for blending.


Layer customization
-------------------
When a multi-color blending image is created, it is recommended to use the multi-panel view mode to visualize the blended image and the original images side by side. The number of panels can be configured in the settings dialog of the Image Viewer Widget (see :ref:`single_panel_view_multi_panel_view`). If a given layer is active, the Render Configuration Widget will display the usual raster rendering options for configuring the rendering of that layer. You will see the layer *and* the blended image in the Image Viewer Widget being updated accordingly. This allows you to optimize the blended image rendering in an efficient way. 

When the blended image is active, the Render Configuration Widget will display a list of layers that are used for blending. Each layer can be re-configured with its own data source (other matched images that are not used for blending), color assignment, and opacity. You can use the remove button to remove a layer from the blending (but the image is still loaded in CARTA). You can also add a new layer by clicking the "Add layer" button and selecting an image (note that only spatially matched images will appear on the list). 


.. raw:: html

   <a href="_static/carta_fn_multicolor_blending_config.png" target="_blank">
       <img src="_static/carta_fn_multicolor_blending_config.png" 
            style="width:100%;height:auto;">
   </a>


The "Apply color set" dropdown menu allows you to apply a predefined color set to the blended image. If the "rainbow" colormap is selected, the exact color assignment is calculated by interpolating the colormap based on the number of layers. The "RGB" and "CMY" color sets are primarily used for blending three images. 


Region of interest and annotations
----------------------------------
As the multi-color blending image is also a spatially matched image to the spatial reference image, you can still create regions of interest or annotation objects on the blended image. However, the region of interest takes no effect for image analytics, such as statistics, spatial profiler, and spectral profiler. When the blended image is active, the actual active image used for analytics is the spatial reference image. The region of interest on the blended image is used only for visualization purposes. It is recommended to use annotation objects for decoration purposes instead.


.. raw:: html

   <a href="_static/carta_fn_multicolor_blending_region_analytics.png" target="_blank">
       <img src="_static/carta_fn_multicolor_blending_region_analytics.png" 
            style="width:100%;height:auto;">
   </a>

Exporting color-blended images
------------------------------
The multi-color blending image can be exported as a PNG file. To do this, you can use the "Export image" button in the toolbar of the Image Viewer Widget. You may switch to the single-panel view mode to export the blended image only.  

.. raw:: html

   <a href="_static/carta_fn_multicolor_blending_export.png" target="_blank">
       <img src="_static/carta_fn_multicolor_blending_export.png" 
            style="width:100%;height:auto;">
   </a>

Save the recipe
---------------
The multi-color blending image cannot be save as an image file, Instead, you can save the recipe of the multi-color blending image by using the "**Save Workspace**" option in the "**File**" menu. The workspace will contain the original images used for blending, the raster configuration for each layer, and the color-blending configuration. You can load the workspace later with "**File**" -> "**Open Workspace**" to restore the multi-color blending image and continue working with it.

.. note::
    With v5.0, the workspace does not save the layout of the entire application. As a result, the restored multi-color blending image may not have exactly the same displayed field of view as before. You will need to adjust the view for your needs. The layout saving feature in a workspace will be available in a future release of CARTA.