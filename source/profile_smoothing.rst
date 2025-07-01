.. _profile_smoothing:

Profile smoothing
=================

Profile smoothing may be applied to profiles in the Spatial Profiler Widget, the Spectral Profiler Widget, and the Stokes Analysis Widget to enhance the signal-to-noise ratio. You can access the settings from the "**Smoothing**" tab of the settings dialogs of these widgets. 

.. raw:: html

   <a href="_static/carta_fn_profileSmoothing.png" target="_blank">
       <img src="_static/carta_fn_profileSmoothing.png" 
           style="width:100%;height:auto;">
   </a>

Optionally, the original profile can be overplotted with the smoothed profile. The appearance of the smoothed profile, including color, style, width, and size, can be customized.

CARTA provides the following smoothing methods:

* Boxcar: convolution with a boxcar function
* Gaussian: convolution with a Gaussian function
* Hanning: convolution with a Hanning function
* Binning: averaging channels with a given width
* Savitzky-Golay: fitting successive sub-sets of adjacent data points with a low-degree polynomial by the method of linear least squares
* Decimation: min-max decimation with a given width    

.. raw:: html

   <a href="_static/carta_fn_profileSmoothing_examples.png" target="_blank">
       <img src="_static/carta_fn_profileSmoothing_examples.png" 
           style="width:100%;height:auto;">
   </a>

