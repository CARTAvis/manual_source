.. _raster_rendering:

Raster rendering
================
Raster rendering is the default rendering mode in CARTA when an image is loaded and displayed in the Image Viewer Widget. As a paired widget, the Render Configuration Widget provides options to control how a raster image is rendered in the Image Viewer Widget, including the scaling function, colormap, clip values, bias/contrast adjustment and NaN color.

.. raw:: html

      <img src="_static/carta_fn_renderConfig_widget.png" 
           style="width:100%;height:auto;">

.. note::
   The Render Configuration Widget will display a different set of options when a multi-color blending image is set as the active image. See :ref:`multicolor_blending` for details.

.. note::
   The raster rendering layer in the Image Viewer Widget may be hidden by clicking the "R" button in the Layers column of the Image List widget.

Histogram
---------
The Render Configuration Widget provides a histogram plot to visualize the pixel value distribution of the active image. The histogram is displayed in a logarithmic scale for the y-axis and the x-axis represents the pixel values. The mean value is displayed as a green dashed line, and the range from mean minus one standard deviation to mean plus one standard deviation is shown as a green box. The two vertical red bars indicate the clip values of the colormap, which can be adjusted by dragging them or entering values in the Clip min and Clip max input fields. The grey curve between the two red vertical bars shows the applied scaling function, including bias and contrast parameters. 

By default, the histogram is calculated per channel of the image, but it can also be calculated per cube if requested using the Histogram dropdown menu. When a per-cube histogram is requested, a warning message and a progress dialog will appear. Calculating a per-cube histogram can be time-consuming for large image cubes. You may cancel the request anytime by pressing the "**cancel**" button in the progress dialog. If the image is in the HDF5 format (IDIA schema), the pre-calculated per-cube histogram will be loaded and displayed instantly. 

The mouse interaction with the histogram plot is summarized in the section :ref:`mouse_interaction_with_charts`.


Clip Values
-----------
The Render Configuration Widget allows you to set clip values for the image rendering. By default, a "99.9%" clip level is applied to the per-channel histogram to determine the two clip values. You can apply a preset clip value using the clip buttons (e.g., "90%", "95%", "100%", etc.) or set custom clip Values by dragging the two vertical red bars in the histogram plot or by entering values in the Clip min and Clip max input fields. 

When you set custom clip values, the "custom" button is enabled, and all channels will be rendered with these fixed boundary values. This is useful for comparing images channel by channel or when you want to ensure consistent rendering across multiple images. If you want to revert to the default per-channel per render configuration rendering mode, you can click one of the predefined clip buttons to do so.

Scaling functions
-----------------
The Render Configuration Widget provides several scaling functions to adjust how pixel values within the two clip values are mapped to colors in the colormap. The available scaling functions in the Scaling dropdown menu include:

* linear: :math:`y = x`
* log: :math:`y = {\log}_{{\alpha}x+1}({\alpha}x+1)`
* square root: :math:`y = {\sqrt{x}}`
* squared: :math:`y = x^2`
* gamma: :math:`y = x^{\gamma}`
* power: :math:`y = ({\alpha}^x-1)/({{\alpha}-1})`

, where :math:`\alpha` or :math:`\gamma` can be adjusted.

The selected scaling function (default linear) is rendered in the histogram plot as a grey curve between the two red vertical bars. 

Bias and contrast adjustment
----------------------------
In addition to the scaling function, the Render Configuration Widget allows you to adjust the bias and contrast of the image rendering. The bias and contrast adjustment is represented as a 2D box in the Render Configuration Widget, where the x-axis represents bias (-1 ~ +1, default 0) and the y-axis represents contrast (0 ~ 2, default 1). Input fields for bias and contrast are also provided. Bias and contrast parameters are coupled with the scaling function to adjust how pixel values are mapped to colors in the colormap. By default, the resulting scaling function rendered as a grey curve in the histogram plot is "smooth" without abrupt changes, which can help produce a more visually appealing image. This option can be switched off by toggling the "Smoothed bias/contrast" toggle in the Render Configuration tab in the Preferences dialog.


Colormaps
---------
CARTA provides a set of colormaps adopted from `matplotlib <https://matplotlib.org/tutorials/colors/colormaps.html?highlight=colormap>`_ and a set of monocolor colormaps (e.g., Red, Green, Blue, etc.). You can select a colormap from the Colormap dropdown menu in the Render Configuration Widget. You can also invert the colormap by toggling the "Invert colormap" toggle. 

.. raw:: html

   <img src="_static/carta_fn_renderConfig_colormaps.png" 
        style="width:100%;height:auto;">

The "custom" colormap can be set by clicking the Color panel button to select any color and generate a custom monocolor colormap.


NaN color
---------
If your image contains NaN (not a number) values such as bad pixels or an ALMA image after primary beam correction where primary beam response less then 20% is masked out, the NaN pixels will be rendered in a specific color. You can change the NaN color in the Render Configuration Widget or change the default NaN color using the Render configuratio tab in the Preferences dialog.

.. note::
   When you generate a multi-color blending image, try to set the NaN color to transparent so that the NaN pixels will not be rendered in the multi-color blending image.


Customization
-------------
The default scaling function, colormap, percentile rank (clip level), and color for NaN pixels can be customized via the menu "**File**" -> "**Preferences**" -> "**Render Configuration**". When the "**Smoothed bias/contrast**" toggle is disabled, bias and contrast are applied so the resulting scaling function is piecewise smooth. 


Settings
--------

The settings dialog of the Render Configuration Widget can be accessed via the "**Settings**" button at the top-right corner of the Render Configuration Widget. This dialog allows you to customize the styling of the histogram plot.

.. raw:: html

   <img src="_static/carta_fn_renderConfig_settings.png" 
        style="width:50%;height:auto;">



