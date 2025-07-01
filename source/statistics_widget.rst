Statistics widget
=================

The Statistics Widget allows you to view statistics from a selected region and a selected image with a polarization component (if it exists). The following statistic quantities are supported:

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

The "**Region**" dropdown menu and the "**Image**" dropdown menu can be used to select which region statistics from which image to be displayed. When the selected image has the polarization axis, you can use the "**Polarization**" dropdown menu to select a target polarization component to compute statistics. The default is "Active", which means the active (selected) region and the active image in the Image Viewer. The “Active” option refers to the entire image if no region is active. Multiple Statistics Widgets can be created to display statistics computed with a combination of "**Image**", "**Region**", and "**Polarization**" (if it is available). 


.. raw:: html

   <a href="_static/carta_fn_statistics_widget.png" target="_blank">
       <img src="_static/carta_fn_statistics_widget.png" 
           style="width:100%;height:auto;">
   </a>

The statistics table can be exported as a text file with the "**export data**" button at the bottom-right corner when you hover over the widget. 