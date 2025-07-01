.. _profile_fitting:

Profile fitting
===============

As of v4.1.0, the profile fitting function can be applied to the Spectral Profiler Widget to estimate of the spectral line properties, such as amplitude, FWHM, center, and integrated area. The profile fitting function is available via the "**Fitting**" button in the top-right corner of the Spectral Profiler Widget. 


.. raw:: html

   <a href="_static/carta_fn_profile_fitting.png" target="_blank">
       <img src="_static/carta_fn_profile_fitting.png" 
           style="width:100%;height:auto;">
   </a>

.. note::
   In a future release, the profile fitting function will be added to the Spatial Profiler Widget and the Histogram Widget.

CARTA supports two model profile functions in v4.1.0 (more will be added in a future release):

* Gaussian: thermal or random motion broadening
* Lorentzian: pressure broadening

In addition, the profile fitting process can include a continuum emission as a constant distribution (0th-order polynomial) or a linear distribution (1st-order polynomial).

In order to work correctly, a set of reasonable initial solutions needs to be provided to the fitting engine. CARTA provides flexible ways of setting up the initial solutions. They can be set manually with the text fields or cursor by drawing a box (for the profile function) or a line (for the continuum function) on the spectral profile plot. An amplitude, a FWHM, and a center must be configured for each component. Up to 20 components are supported in one single fit. When more than one component is required in the fit, the "**components**" slider can be used to switch to different components. The "**delete**" button can be used to delete a selected component.


.. raw:: html

   <a href="_static/carta_fn_profile_fitting_manual.png" target="_blank">
       <img src="_static/carta_fn_profile_fitting_manual.png" 
           style="width:100%;height:auto;">
   </a>

Alternatively, the "**auto detect**" function (experimental) tries to analyze your spectral profile data and sets up the initial solutions *automatically*. If there is a prominent continuum emission or offset, please enable the "**w/ cont.**" toggle before clicking the "**auto detect**" button. If the "**auto fit**" toggle is enabled, the fitting engine will be triggered if the "**auto detect**" function finds a set of initial solutions. When the "**auto detect**" function is applied, you may edit the initial solutions manually afterward, such as adding a new component, deleting an existing component, refining a parameter, etc.


.. raw:: html

   <a href="_static/carta_fn_profile_fitting_auto.png" target="_blank">
       <img src="_static/carta_fn_profile_fitting_auto.png" 
           style="width:100%;height:auto;">
   </a>


The fitting results are visualized in the spectral profile plot, including the individual model profiles, the synthetic model profile, and the residual profile. The numeric values of the fitting results are displayed in the "**Fitting result**" box. The fitting log is available by clicking the "**View log**" button. When the "**Reset**" button is clicked, the profile fitting function will be reset.


.. raw:: html

   <a href="_static/carta_fn_profile_fitting_log.png" target="_blank">
       <img src="_static/carta_fn_profile_fitting_log.png" 
           style="width:100%;height:auto;">
   </a>

In some cases, a given free parameter, such as the center of a Gaussian component, may need to be fixed to obtain a *sensible* fit. A parameter can be fixed by clicking its "**lock**" button. Note that there needs to be at least one free parameter to request a fit. 

.. raw:: html

   <a href="_static/carta_fn_profile_fitting_lock.png" target="_blank">
       <img src="_static/carta_fn_profile_fitting_lock.png" 
           style="width:100%;height:auto;">
   </a>



.. note::
   The profile fitting function is unavailable when multiple profiles are plotted in the Spectral Profiler Widget. Please ensure that there is only one profile in the plot to use the profile fitting function.

.. note::
   In a future release, the spectral profile fitting function will be enhanced by referencing the spectral line catalog so that the relative positions of the model components can be locked. Line width and relative amplitude can be constrained, too. 
