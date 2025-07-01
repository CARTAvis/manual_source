.. _animator_intro:

Animator
========

The Animator Widget provides controls for image frames, channels, and polarization. When multiple images are loaded via "**File**" -> "**Append image**", the "**Image**" slider will show up and allow you to switch to a different image. You can also use the Image List Widget for image switching. If an image file has multiple channels and/or polarization components, the "**Channel**" and/or the "**Polarization**" slider will appear. The double slider right below the "**Channel**" slider allows you to specify a range of channels for animation playback. On the top is a set of animation control buttons such as "**Play**", "**Next**", etc. Playback modes, including "forward", "backward", "Bouncing", and "Blink", are supported. Playback action will be applied to the slider with the activated radio button. 


.. raw:: html

   <img src="_static/carta_fn_animator_widget.png" 
        style="width:80%;height:auto;">


The polarization slider shows all the polarization components (Stokes I/Q/U/V, XX/YY/XY/YX, or RR/LL/RL/LR) as defined in the image header. If the Stokes parameters are defined in the image header, additional *computed* components, including:

* Ptotal: total polarization intensity (computed from Stokes QU or QUV)
* Plinear: linear polarization intensity (computed from Stokes QU)
* PFtotal: fractional total polarization intensity (computed from Stokes IQU or IQUV)
* PFlinear: fractional linear polarization intensity (computed from Stokes IQU)
* Pangle: linear polarization angle (computed from Stokes QU)

are appended as well. You may save a computed component as a new image file via "**File**" -> "**Save image**".

The "**Frame Rate**" spin box controls the *desired* frame per second (fps). The *actual* frame rate depends on image size and internet condition. Optionally, you can set a step for the animation playback (default as unity). By clicking the "**Frame Rate**" dropdown, the "**Step**" option will show up. 


