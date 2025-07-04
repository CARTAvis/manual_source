.. _raster_rendering:

Raster rendering
================

The Render Configuration Widget controls how a raster image is rendered in the Image Viewer. On the top is a row of buttons with different clip levels, plus a custom button. Below the clip buttons is a plot showing the per-channel histogram (with a logarithmic scale in y) with a bin count equal to the geometric mean of the image size (x and y). The two vertical red bars indicate the two clip values of a color map. The green dashed line marks the mean value, and the green box marks the range from mean minus one standard deviation to mean plus one standard deviation. The gray curve between the two red vertical bars shows the applied scaling function, including bias and contrast parameters. The mouse interaction with the histogram plot is summarized in the section :ref:`mouse_interaction_with_charts`.

.. raw:: html

      <img src="_static/carta_fn_renderConfig_widget.png" 
           style="width:100%;height:auto;">


On the right-hand side of the Render Configuration Widget, there is a column of options, such as histogram type, scaling function, colormap, invert colormap, clip values, control parameter of a scaling function (if applicable), bias/contrast adjustment (i.e., a 2D box with x as bias and y as contrast), and NaN (not a number) color. Extra options to configure the histogram plot are placed in the settings dialog of the Render Configuration Widget, enabled by the "**cog**" button at the top-right corner of the Render Configuration Widget. 

By default, CARTA calculates a per-channel histogram. When a per-cube histogram is requested, a warning message and a progress dialog will appear. Calculating a per-cube histogram can be time-consuming for large image cubes. You may cancel the request anytime by pressing the "**cancel**" button in the progress dialog. If the image is in the HDF5 format (IDIA schema), the pre-calculated per-cube histogram will be loaded and displayed instantly. 

CARTA determines the boundary values of a colormap on a **per-channel** basis by default. A default "99.9%" clip level is applied to the per-channel histogram to look for the two clip values. Then, apply the values in a "linear" scale with zero bias and zero contrast to the default colormap "inferno" to render a raster image. This default procedure usually helps inspect an image in detail without suffering from improper image rendering. 

However, color scales need to be fixed when comparing images channel by channel. You can drag the two vertical red bars or type in the values in the "Clip min" and "Clip max" input fields to do so. When this happens, the "custom" button is enabled automatically, and *all* channels will be rendered with the fixed boundary values. By clicking one of the clip buttons, CARTA switches back to the per-frame rendering mode *if a per-channel histogram is requested*. You may request the per-cube histogram to determine proper clip values.

CARTA provides a set of scaling functions, including:

* linear: :math:`y = x`
* log: :math:`y = {\log}_{{\alpha}x+1}({\alpha}x+1)`
* square root: :math:`y = {\sqrt{x}}`
* squared: :math:`y = x^2`
* gamma: :math:`y = x^{\gamma}`
* power: :math:`y = ({\alpha}^x-1)/({{\alpha}-1})`

A set of color maps adopted from `matplotlib <https://matplotlib.org/tutorials/colors/colormaps.html?highlight=colormap>`_ is provided in CARTA.

.. raw:: html

   <img src="_static/carta_fn_renderConfig_colormaps.png" 
        style="width:100%;height:auto;">

The default scaling function, colormap, percentile rank (clip level), and color for NaN pixels can be customized via the menu "**File**" -> "**Preferences**" -> "**Render Configuration**". When the "**Smoothed bias/contrast**" toggle is disabled, bias and contrast are applied so the resulting scaling function is piecewise smooth. 


.. note::
   Viewing a position-velocity image

   CARTA switches to using *rectangular* pixels for rendering when a position-velocity image is loaded as a raster image. The pixel aspect ratio is flexible based on the aspect ratio of the Image Viewer Widget. By default, the "spectral" axis is displayed in velocity, if possible, based on the image header. You may use the Image Viewer Settings Dialog to apply a conversion to other spectral conventions, such as frequency or wavelength. The frequency-to-velocity conversion requires a reference rest frequency. This reference rest frequency is derived from the image header. You may use the settings dialog of the Image List Widget to set a new reference rest frequency to recompute the velocity axis.

   .. raw:: html

      <img src="_static/carta_fn_imageviewer_pv_rendering.png" 
           style="width:100%;height:auto;">


Settings
--------

work in progress...


