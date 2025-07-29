Statistics widget
=================

The Statistics Widget allows you to view statistics from a selected region and a selected image with a polarization component (if it exists). The following statistic quantities are supported:

* NumPixels: number of pixels included in the statistics computation
* Sum: summation
* Mean: average
* FluxDensity: flux density
* StdDev: standard deviation
* Min: minimum
* Max: maximum
* Extrema: extrema
* RMS: root mean square
* SumSq: summation of squared pixel values

.. raw:: html

   <a href="_static/carta_fn_statistics_widget.png" target="_blank">
       <img src="_static/carta_fn_statistics_widget.png" 
           style="width:100%;height:auto;">
   </a>


The "**Region**" dropdown menu and the "**Image**" dropdown menu can be used to select which region statistics from which image to be displayed. When the selected image has the polarization axis, you can use the "**Polarization**" dropdown menu to select a target polarization component to compute statistics. The default is "Active", which means the active (selected) region and the active image in the Image Viewer. The “Active” option refers to the entire image if no region is active. Multiple Statistics Widgets can be created to display statistics computed with a combination of "**Image**", "**Region**", and "**Polarization**" (if it is available). 




Flux density formulae
---------------------
The "**FluxDensity**" statistic is computed depending on the pixel unit and as the following:

- **Jy/beam** -> **Jy**

  :math:`\sum_{\rm pixel}^{}{I \div d\Omega_{\rm beam} \times d\Omega_{\rm pixel}}`

  where :math:`I` is the intesnity in Jy/beam, :math:`d\Omega_{\rm beam}` is the beam solid angle in steradians (the beam solid angle = :math:`\pi \times {\rm BMAJ} \times {\rm BMIN} \div 4 \ln(2)`, where BMAJ and BMIN are the beam major and minor axes in radians, respectively), and :math:`d\Omega_{\rm pixel}` is the pixel solid angle in steradians (the pixel solid angle = :math:`{\rm PIXEL\_X} \times {\rm PIXEL\_Y}`, where PIXEL_X and PIXEL_Y are the pixel size in X axis and Y axis in radians, respectively).

- **Jy/arcsec^2** -> **Jy**

  :math:`\sum_{\rm pixel}^{}{I \times A}`

  where :math:`I` is the intensity in Jy/arcsec^2, and :math:`A` is the pixel area in square arcseconds.

- **Jy/pixel** -> **Jy**

  :math:`\sum_{\rm pixel}^{}{I}`

  where :math:`I` is the intensity in Jy/pixel.

- **MJy/sr** -> **MJy**

  :math:`\sum_{\rm pixel}^{}{I \times d\Omega_{\rm pixel}}`

  where :math:`I` is the intensity in MJy/sr, and :math:`d\Omega_{\rm pixel}` is the pixel solid angle in steradians.

- **K** -> **K arcsec^2**

  :math:`\sum_{\rm pixel}^{}{I \times A}`

  where :math:`I` is the brightness temperature in K, and :math:`A` is the pixel area in square arcseconds.

For units other than the above, the flux density is displayed as NaN (not a number).

Export as a text file
---------------------

The statistics table can be exported as a text file with the "**export data**" button at the bottom-right corner when you hover over the widget. 