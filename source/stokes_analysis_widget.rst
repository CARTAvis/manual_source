Stokes analysis widget
======================

The Stokes Analysis Widget helps you efficiently view fundamental polarization quantities of a multi-channel cube with multi-Stokes (IQU, QU, or IQUV). Suppose different Stokes images are stored as individual files (i.e., image_I.fits, image_Q.fits, image_U.fits, and image_V.fits). In that case, you can use the File Browser Dialog to create a Stokes hypercube by selecting multiple Stokes images and clicking the “Load as hypercube” button (see :ref:`forming_hypercube`). Effectively, you will see only one image loaded with multiple Stokes in CARTA. 


The widget includes the following plots:

* Stokes Q intensity and Stokes U intensity over the spectral axis
* Linear polarization intensity over the spectral axis
* Linear polarization angle over the spectral axis
* Stokes Q intensity versus Stokes U intensity as a scatter plot

The profiles can be zoomed and panned with a mouse, similar to the Spatial Profiler Widget or the Spectral Profiler Widget (:ref:`mouse_interaction_with_charts`). The Stokes Q versus Stokes U scatter plot is color-encoded from red to blue with increasing frequencies. The profiles can be requested at the cursor position (single pixel) or over a region of interest. Fractional polarization quantities are also supported when the Stokes I component is available. 

.. raw:: html

   <a href="_static/carta_fn_Stokes_widget.png" target="_blank">
       <img src="_static/carta_fn_Stokes_widget.png" 
           style="width:100%;height:auto;">
   </a>



When profiles are zoomed in, the scatter plot will highlight those channels in the profile view. Similarly, when the scatter plot is zoomed, the profile plot will highlight those channels just in the scatter plot view. The profile plots and the scatter plot are interlinked.

.. raw:: html

   <a href="_static/carta_fn_Stokes_widget_linkView1.png" target="_blank">
       <img src="_static/carta_fn_Stokes_widget_linkView1.png" 
           style="width:100%;height:auto;">
   </a>

.. raw:: html

   <a href="_static/carta_fn_Stokes_widget_linkView2.png" target="_blank">
       <img src="_static/carta_fn_Stokes_widget_linkView2.png" 
           style="width:100%;height:auto;">
   </a>

Additional options to customize the plots in the Stokes Analysis Widget are provided in the settings dialog, which can be launched by clicking the "**cog**" button at the top-right corner. With the options in the dialog, you can configure the appearance of the profile plots and the scatter plot. Optionally, profile smoothing can be applied with the "**Smoothing**" tab (see section :ref:`profile_smoothing`). A shortcut button to the "**Smoothing**" tab can be found in the top-right corner of the Stokes Analysis Widget.


Settings
--------

