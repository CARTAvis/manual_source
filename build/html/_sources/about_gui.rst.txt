Graphical user interface
========================
The graphical user interface (GUI) of CARTA is flexible and user friendly to support most of use cases, such as continuum image analysis, or spectral line cube analysis, etc. In this section, we introduce the details of the GUI and provide examples to guide users to get familiar with configuring layouts via mouse interactions.


Components
----------
The GUI of CARTA is classified into different components:

* main window
* menu bar
* widget bar
* panel 
* tab
* floating window

.. figure:: ./_figures/carta_gui.png
   :scale: 40 %
   :alt: carta_gui

   Figure: components of the CARTA garphical user interface.

The main window consists of a set of panels and each panel may hold multiple tabs. For example, in the above figure there are six panels in the main window and there are two tabs in the bottom-right panel. A tab may be detached to become a floating window. The menu bar provides control options, such as image input/output, lanuching widgets, getting helps, etc. The widget bar provides tools to view or analyze images.



Layouts: how to configure?
--------------------------
The configuration of the layout is achieved by mouse operations, like single click or drag-and-drop. The drag-and-drop action is guided on the GUI with a semi-transparent rectangle. Below different operations are demostrated.

Resizing a panel
^^^^^^^^^^^^^^^^
By dragging borders, a panel can be resized like the following example. After a panel is resized, nearby panels are resized automatically to fit the new layout. Note that the appearance of the UI elements is adaptive to the size of the panel, like the **render configuration** widget or the **animator** widget in the example. 

.. figure:: ./_figures/carta_gui_resizing_panel.gif
   :scale: 100 %
   :alt: carta_gui_resizing_panel


Relocating a tab as a new panel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A tab can be relocated by dragging its title to a desired new panel. The target location is visualized with a semi-transparent box, like the following example.

.. figure:: ./_figures/carta_gui_relocating_tab_as_panel.gif
   :scale: 100 %
   :alt: carta_gui_relocating_tab_as_panel


Relocating a tab to another panel
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A tab can be moved to other existing panel by dragging its title to the upper boarder of the target panel, like the following example.

.. figure:: ./_figures/carta_gui_relocating_tab_as_tab.gif
   :scale: 100 %
   :alt: carta_gui_relocating_tab_as_tab

Maximixing and minimizing a tab
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
By clicking the **maximize** icon at the top-right corner of a panel, the activated tab will be maximized to the main window. By clicking the **restore** icon, the tab will be restored to its original panel.

.. figure:: ./_figures/carta_gui_max_min_tab.gif
   :scale: 100 %
   :alt: carta_gui_max_min_tab


Detaching and attaching a tab
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
By clicking the **detach** icon (like a pin) at the top-right corner of a panel, the activated tab will be detached to become a floating window. By dragging the **attach** icon (like a pin), a floating winodw will be attached to an existing panel or as a new paenl.

.. figure:: ./_figures/carta_gui_detach_attach_tab.gif
   :scale: 100 %
   :alt: carta_gui_detach_attach_tab


Activating a widget as a floating window or as a tab
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
A widget is activated as a floating window by clicking the icon in the widget bar. A widget can be activated as a tab by dragging the icon in the widget bar to a desired location.

.. figure:: ./_figures/carta_gui_activating_widget.gif
   :scale: 100 %
   :alt: carta_gui_activating_widget



Light and dark theme
^^^^^^^^^^^^^^^^^^^^
CARTA supports two themes: one is the light theme as default and the other is the dark theme which is accessible by the menu **View** -> **Interface**, or the shortcut **shift** + **D**. 

.. figure:: ./_figures/carta_gui_theme.gif
   :scale: 100 %
   :alt: carta_gui_theme


Keyboard shortcuts
------------------
CARTA supports keyboard shortcuts to enable certain controls without using a mouse. A summary is accessible via the menu **Help** -> **Controls and Shortcuts**, or the shortcut **shift** + **?**. The shortcuts are slightly different depending on operating systems, which are summerized in the following table.


+------------------------------+-----------------------+-----------------------+
| Control                      | macOS                 | Linux                 |
+==============================+=======================+=======================+
| **Help**                     |                       |                       |
+------------------------------+-----------------------+-----------------------+
| Controls and shortcuts       | shift + ?             | shift + ?             |
+------------------------------+-----------------------+-----------------------+
| **Appearance**               |                       |                       |
+------------------------------+-----------------------+-----------------------+
| Toggle dark/light theme      | cmd + D               | ctrl + D              |
+------------------------------+-----------------------+-----------------------+
| **Cursor**                   |                       |                       |
+------------------------------+-----------------------+-----------------------+
| Toggle frozen cursor         | F                     | F                     |
+------------------------------+-----------------------+-----------------------+
| **File**                     |                       |                       |
+------------------------------+-----------------------+-----------------------+
| Open image                   | cmd + O               | ctrl + O              |
+------------------------------+-----------------------+-----------------------+
| Append image                 | cmd + L               | ctrl + L              |
+------------------------------+-----------------------+-----------------------+
| Export image                 | cmd + E               | ctrl + E              |
+------------------------------+-----------------------+-----------------------+
| **Frame**                    |                       |                       |
+------------------------------+-----------------------+-----------------------+
| Next frame                   | cmd + ]               | ctrl + ]              |
+------------------------------+-----------------------+-----------------------+
| Previous frame               | cmd + [               | ctrl + [              |
+------------------------------+-----------------------+-----------------------+
| Next channel                 | cmd + up              | ctrl + up             |
+------------------------------+-----------------------+-----------------------+
| Previous channel             | cmd + down            | ctrl + down           |
+------------------------------+-----------------------+-----------------------+
| Next Stokes                  | cmd + shift + up      | ctrl + shift + up     |
+------------------------------+-----------------------+-----------------------+
| Previous Stokes              | cmd + shift + down    | ctrl + shift + down   |
+------------------------------+-----------------------+-----------------------+

