.. _layout_management:

Layout
======

CARTA has a set of preset layouts designed for different kinds of image analysis. These layouts are accessible via the menu "**View**" -> "**Layouts**" -> "**Existing Layouts**". 

You may customize a preset layout for a different purpose and save it for the future. To save a custom layout, use the menu "**View**" -> "**Layouts**" -> "**Save Layout**". A name is required when saving a layout. 

A saved layout can be restored via the menu "**View**" -> "**Layouts**" -> "**Existing Layouts**". The active layout is highlighted in blue ("my layout 01" in the following example). Saved layouts can be removed via the menu "**View**" -> "**Layouts**" -> "**Delete Layout**" or renamed via the menu "**View**" -> "**Layouts**" -> "**Rename Layout**".


.. raw:: html

   <a href="_static/carta_gui_custom_layout.png" target="_blank">
       <img src="_static/carta_gui_custom_layout.png" 
           style="width:100%;height:auto;">   
   </a>


By default, CARTA will load the preset layout named “Default” when initialized. Which layout, including user-customized layouts, should be loaded can be further defined via the Preferences Dialog ("**File**" -> "**Preferences**"). The initial layout can be set via the "**Initial layout**" dropdown menu of the "**Global**" tab.


.. raw:: html

   <a href="_static/carta_gui_layout_preference.png" target="_blank">
       <img src="_static/carta_gui_layout_preference.png" 
           style="width:90%;height:auto;">   
   </a>


.. note::
  
  The layout files are kept in :code:`<your home>/.carta/config/layouts` folder in the JSON format. When you install CARTA on a new computer, you may copy the layout files from the old computer to migrate the custom layouts.

