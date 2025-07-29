Stokes analysis widget
======================

The Stokes Analysis Widget helps you efficiently view fundamental polarization quantities of a multi-channel cube with multi-Stokes (IQU, QU, or IQUV). In the case that different Stokes images are stored as individual files (i.e., image_I.fits, image_Q.fits, image_U.fits, and image_V.fits), you can use the File Browser Dialog to create a Stokes hypercube by selecting multiple Stokes images and clicking the “Load as hypercube” button (see :ref:`forming_hypercube`). Effectively, you will see only one image loaded with multiple Stokes in CARTA.

Diagnostic plots
----------------

The widget includes the following plots:

* Stokes Q intensity and Stokes U intensity over the spectral axis
* Linear polarization intensity over the spectral axis
* Linear polarization angle over the spectral axis
* Stokes Q intensity versus Stokes U intensity as a scatter plot


Interactivity
-------------

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


.. _stokes_analysis_widget_spectral_convention:

Spectral convention
-------------------
The spectral convention of the spectral axis as well as the reference system can be configured via the "Conversion" tab in the settings dialog of the Stokes Analysis Widget. 

The spectral convention with equivalent units includes the following options:

* Frequency
* Radio velocity
* Optical velocity
* Vacuum wavelength
* Air wavelength
* Squared air wavelength
* Squared vacuum wavelength
* Channel

The reference system includes the following options:

* LSRK (Local Standard of Rest, Kinematic)
* LSRD (Local Standard of Rest, Dynamical)
* Barycentric
* Topocentric


Smoothing
---------
The spectral profile data can be smoothed with the methods available in the "Smoothing" tab of the settings dialog. See :ref:`profile_smoothing` for more details. 

The smoothed Q and U profile data will be used to calculate the linear polarization intensity and angle and displayed as profiles in the Stokes Analysis Widget. The smoothed Q and U profile data will also be used to generate the Stokes QU scatter plot. 


.. _stokes_analysis_widget_styling:

Styling of plots
----------------
Additional options to customize the plots in the Stokes Analysis Widget are provided in the settings dialog. The options in the "Line Plot Styling" tab allows to customize the appearance of the QU profile plot, linear polarization intensity profile plot, and the linear polarization angle profile plot. The options in the "Scatter Plot Styling" tab allows to customize the appearance of the Stokes QU scatter plot.

.. raw:: html

   <a href="_static/carta_fn_Stokes_widget_styling.png" target="_blank">
       <img src="_static/carta_fn_Stokes_widget_styling.png" 
           style="width:100%;height:auto;">
   </a>


Export data and plots
---------------------
The profile data and plot, and the Stokes QU scatter data and plot can be exported to a file via the toolbar when you hover the mouse over the plot area. The exported data will be in TSV format, and the exported plot will be in PNG format. 



Settings
--------
The Stokes Analysis Settings dialog provides the following tabs:

* **Conversion**: Configure the spectral convention and reference system (see :ref:`stokes_analysis_widget_spectral_convention`).
* **Smoothing**: Configure the smoothing method and parameters (see :ref:`profile_smoothing`).
* **Line Plot Styling**: Customize the appearance of the QU profile plot, linear polarization intensity profile plot, and the linear polarization angle profile plot (see :ref:`stokes_analysis_widget_styling`).
* **Scatter Plot Styling**: Customize the appearance of the Stokes QU scatter plot (see :ref:`stokes_analysis_widget_styling`).


