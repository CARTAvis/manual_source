.. _channel_map_view:

Channel map control
===================

A channel map view is a powerful visualization tool used in radio astronomy to explore spectral data within an image cube. An image cube contains a sequence of 2D images at different frequency or velocity channels, effectively representing the third dimension of spectral information. The channel map view displays these individual slices sequentially or side-by-side, allowing astronomers to trace the spatial distribution and motion of emitting gas across different velocities. This technique is especially useful for identifying kinematic structures, such as rotating disks (see the following screenshot), expanding shells, or outflows, and for studying the dynamics of molecular clouds and galaxies.

.. raw:: html

    <a href="_static/carta_fn_channel_map_view.png" target="_blank">
        <img src="_static/carta_fn_channel_map_view.png" 
            style="width:100%;height:auto;">
    </a>
   
.. note::
    In v5.1, the channel map view only supports raster rendering of an image cube. Contour rendering, vector field rendering, and catalog overlay are not supported. In a future release, we will support the other rendering modes including the matching feature.

To enable the channel map view mode, click the "Channel Map" button at the top-right corner of the Image Viewer Widget, or use the "Enable channel map mode" toggle in the Channel Map Control Widget which is accessible in the widget bar at the top of the GUI.

To exit the channel map view mode, click the "Channel Map" button again or toggle off the "Enable channel map mode" in the Channel Map Control Widget. Alternatively, you can click the single-panel/multi-panel view button at the top-right corner of the Image Viewer Widget to switch back to the other view modes.



Channel map configuration
-------------------------

Once the channel map view mode is enabled, the channel maps of the active image as specified in the Image dropdown menu will be displayed in the Image Viewer Widget. You can use this menu to switch to other image cubes to show their channel maps. 

.. note::
    To switch to a different Stokes, you can use the Polarization slider in the Animator Widget. The channel map view will be updated to show the channel maps of the selected Stokes parameter.

By default a 2x2 grid of panels will be displayed in the Image Viewer Widget to display the first four channels of the image cube. The number of rows and columns can be configured with the "Number of columns" and "Number of rows" input fields in the Channel map control widget. The upper limit of each is 10. Therfore in total, the Image Viewer Widget can display up to 100 channels at once. The active channel in the current channel map view is highlighted with a red box.

.. raw:: html

   <a href="_static/carta_fn_channel_map_view_control.png" target="_blank">
       <img src="_static/carta_fn_channel_map_view_control.png" 
            style="width:60%;height:auto;">
   </a>

To switch to the next set of channels filling the configured channel map grid, you can click the "Next page" button. Likewise, to switch to the previous set of channels, you can click the "Previous page" button. 

To set a specific channel as the start channel (the upper-left corner of the grid) of the channel map view, you can enter the channel number in the "Start channel" input field or use the "Start channel" slider. The slider provides a handy way to search for features in the cube. To fine tune the start channel, you can use the spinbox of the Start channel input field or use the "Next channel" or the "Previous channel" buttons.

The spectral information such as the channel index, frequency, or velocity of each channel can be displayed in the channel map view. You can use the toggles "Show channel string", "Show frequency string" and "Show velocity string" to enable or disable the display of these labels. The styling of the frequency label can be customized including the font type, size, and color.



Switching active channel
------------------------
The active channel in the channel map view is the one that is highlighted with a red box. You can switch the active channel by clicking on a channel panel in the channel map grid. The active channel, as an implicity property of an image will be used for image analytics, such as statistics, spatial profiler, and spectral profiler, etc. 

.. raw:: html

    <a href="_static/carta_fn_channel_map_view_active_channel.png" target="_blank">
        <img src="_static/carta_fn_channel_map_view_active_channel.png" 
            style="width:100%;height:auto;">
    </a>

Alternatively, you can use the Channel slider in the Animator Widget for switching active channels. If the selected channel is in the current channel map view, the corresponding channel panel will be highlighted with a red box and no re-rendering is required. However, if the selected channel is not in the current channel map view, the channel map view will be updated to have the selected channel as the new start channel in the grid and the subsequent channels will be rendered to fill up the grid.

Similarly, you can use the Spectral Profiler Widget to switch the active channel (as highlighted with a red vertical line) by clicking on the channel in the spectral profiler plot. The channel map view will behave the same as when using the Channel slider in the Animator Widget.


Raster rendering configuration
------------------------------
By default, the raster rendering configuration of the channel map view behaves similar to the single-panel and the multi-panel view modes. As now we are able to view multiple channels at once, the raster rendering configuration for the active channel is applied to *all* channels in the channel map view. To fix the raster rendering configuration for the channel map view, you can click the "Custom" clip button in the Render Configuration Widget. This will set the raster rendering configuration fixed regardless the active channel allowing cross-channel and cross-page comparison. 

Region of interest and annotations
----------------------------------
In the channel map view mode, you can still create regions of interest for image analytics or annotation objects for decoration. Note that a region or annotation object created in the channel map view mode is rendered on all channels as the limitation of the current implementation of region of interest and annotation objects. 

.. note::
    In v5.1, the region of interest and annotation objects are implicitly applied to the entire spectral axis of an image cube. Having the ability to specify a range of the spectral axis and a set of Stokes will be available in a future release of CARTA. This is also know as 3D or 4D region of interest.

Export channel maps
-------------------

The channel map view can be exported as a PNG image by clicking the "**Export image**" button at the bottom-right corner of the Image Viewer or by "**File**" -> "**Export image**". High-resolution PNG images can be requested with the additional "200%" and "400%" options. With the "100%" option, the resolution is the same as the screen resolution. With these options, you can set the resolution as 1X, 2X, or 4X the screen resolution. Note that if you use a high-resolution screen to export a PNG image and the request resolution exceeds the limitation of WebGL2, the final resolution of the PNG image will be reduced automatically. 

.. raw:: html

   <a href="_static/carta_fn_channel_map_view_export.png" target="_blank">
       <img src="_static/carta_fn_channel_map_view_export.png" 
            style="width:100%;height:auto;">
   </a>