.. _catalog_widget:

Catalog visualization
=====================
Catalog widget provides an interface to visualize the context of source catalogs in CARTA. It also provides a way to visualize the source catalog data as a catalog image overlay in the Image Viewer Widget, a 2D scatter plot, and a histogram plot.   


Supported catalog formats
-------------------------

CARTA supports local source catalog files ("**File**" -> "**Import Catalog**") in

* VOTable format
* FITS format

and online catalog files from

* `SIMBAD <https://simbad.u-strasbg.fr>`_
* `VizieR <https://vizier.cds.unistra.fr>`_

by querying the catalog data via the Online Data Query Dialog (see :ref:`online_data_query` for details). 


Basic user interface
--------------------
Once a source catalog file is loaded, it is displayed as two tables in the Catalog Widget. The upper table shows the column information in the catalog. The actual source catalog is displayed in the lower table. You can use the "Display" toggles in the upper table to show or hide specific columns in the source catalog table. 

By default, only the first ten columns of an offline catalog file are enabled and displayed (use "**File**" -> "**Preferences**" -> "**Catalog**" to change the default number). The upper table may be minimized by clicking the "Show header" toggle or by double-clicking the splitter bar between the two tables. 


.. raw:: html

   <img src="_static/carta_fn_catalogue_widget.png" 
        style="width:100%;height:auto;">


Multiple catalog files can be loaded, and you may use the "**File**" dropdown menu at the top of the widget to switch catalog files. Multiple Catalog Widgets may be launched to display different catalog files. The "**Close catalog**" button at the bottom of the widget will close the selected catalog file in the "**File**" dropdown menu. 



Catalog filtering and sorting
-----------------------------
The source catalog table accepts sub-filters such as partial string match or value range. For numeric columns, supported operators are:

* :code:`>` : greater than
* :code:`>=` : greater than or equal to
* :code:`<` : less than
* :code:`<=` : less than or equal to
* :code:`==` : equal to
* :code:`!=` : not equal to
* :code:`..` : between (exclusive)
* :code:`...` : between (inclusive)
                    
For examples:

* To filter everything less than 10, use :code:`< 10`
* To filter entries equal to 1.23, use :code:`== 1.23`
* To filter everything between 10 and 50 (exclusive), use :code:`10..50`
* To filter everything between 10 and 50 (inclusive), use :code:`10...50`

For string columns, a partial match is adopted. For example, :code:`gal` (no quotation) will return entries containing the "gal" string.

The filters will be applied by clicking the "**Apply filter**" button or pressing the "enter" or "return" key. The filtered source catalog will be displayed up to the number of entries defined in the "**Max Rows** input field. Clicking the "**Reset filter**" button removes all filters. If a catalog image overlay has been created in the Image Viewer, it will be removed. If a histogram plot or a 2D scatter plot has been created, they will be reset and only up to the first 50 entries will be rendered.

By clicking on the column header, you can sort the table by that column. The sorting order is indicated by an icon next to the column name. You can click on the column header again to reverse the sorting order or click once again to switch back to the default sorting order. The sorting order is applied to the filtered source catalog. If no filter is applied, the sorting order is applied to the full source catalog.


Catalog image overlay
---------------------
CARTA supports flexible catalog image overlay rendering with variable marker size, color, and orientation. A catalog image overlay can be generated using the dropdown menus at the bottom of the Catalog Widget. When the rendering type is "image overlay", two data columns need to be identified as the world coordinates. Once they are configured correctly, you can click the "**Plot**" button to generate a catalog overlay on the image.


As an example, a catalog is loaded and displayed in the Catalog Widget in the screenshot below. The rendering type is "Image Overlay", and the "RA_d" and the "DEC_d" columns are identified as source world coordinates in the ICRS system. A filter is applied to the "ANG_DIST" column, resulting in 638 filtered sources. These sources are rendered on the image as cyan circles with a fixed size on screen. 

.. raw:: html

   <img src="_static/carta_fn_catalogue_widget_filter.png" 
        style="width:100%;height:auto;">


Custom mode
^^^^^^^^^^^
By default, a catalog overlay is rendered with a fixed size in screen pixels and a fixed color on screen. This is a special case of the default "Custom" mode. In this mode, the marker size, color, and orientation can be further customized via the Catalog Settings Dialog. By assigning a data column each, you can have a variable marker size, color, and orientation, respectively. 

.. raw:: html

   <img src="_static/carta_fn_catalogue_widget_custom_mode.png" 
        style="width:100%;height:auto;">


The marker size, referring to the marker diameter or area, can be mapped to a data column with a scaling function and clip bounds so that the marker size becomes variable. If the selected marker has a major and a minor axis such as an ellipse, the major size and the minor size can be configured separately. 

The marker color can be mapped to a data column with a scaling function and clip bounds so that the marker color becomes variable. The marker orientation can be mapped to a data column with a scaling function and clip bounds so that the marker orientation becomes variable.

The following example uses an ellipse marker to generate a catalog overlay. Its color, size, and orientation are mapped to data columns. 

.. raw:: html

   <img src="_static/carta_fn_catalogue_widget_marker_mapping.png" 
        style="width:100%;height:auto;">


Angular size mode
^^^^^^^^^^^^^^^^^
If it is intended to interpret the data value of a data column as an angular size or an orientation in degrees, you can select the "Angular Size" mode. In this mode, the marker size is interpreted as an angular size with a custom unit (arcsecond, arcminute, degree), and the marker orientation is interpreted as an angle in degrees. The marker color can still be mapped to a data column if it is necessary.

.. raw:: html

   <img src="_static/carta_fn_catalogue_widget_angular_size_mode.png" 
        style="width:100%;height:auto;">



Linked catalog overlay and catalog table
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The catalog overlay in the Image Viewer Widget and the catalog table in the Catalog Widget are interlinked. For example, when you select a source on the image, the selected source will be highlighted in the image *and* the catalog table, and vice versa. 

.. raw:: html

   <img src="_static/carta_fn_catalogue_widget_image_overlay_selection.png" 
        style="width:100%;height:auto;">


Catalog overlay on spatially matched images   
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If there are spatially matched images, a catalog overlay on the reference image will be shared with other images with proper coordinate transformations. A prerequisite is that a coordinate system of the source catalog needs to be defined via the "**System**" dropdown menu. CARTA tries to obtain the coordinate system information from the header of the catalog file. If this process is unsuccessful, you must set it manually to interpret the world coordinates correctly. The source catalog defined in the image coordinate (0-based or 1-based) is also supported.


.. raw:: html

   <img src="_static/carta_fn_catalogue_matching.png" 
        style="width:100%;height:auto;">


Catalog 2D scatter plot
-------------------------
By selecting "2D Scatter" mode and identifying two numeric columns as the x-axis and y-axis, you can generate a 2D scatter plot of the source catalog in the Catalog 2D Scatter Plot Widget. 

The Catalog 2D Scatter Plot Widget shows a 2D scatter plot of two numeric columns of a catalog file. The available numeric columns are determined by the “Display” column of the upper table in the Catalog Widget. The lower table in the Catalog Widget determines the data used for plotting the 2D scatter. The table may not show all entries due to the dynamic loading feature. Thus, the 2D scatter plot may not include all entries (after filtering). The "**Plot**" button in the Catalog 2D Scatter Plot Widget will request a full download of all entries, and the scatter plot will then include all entries (after filtering).


By clicking on a point or using the selection tools from the top-right corner of the scatter plot, selected sources will be highlighted in the source catalog table, in the histogram plot (if it exists), and in the Image Viewer (if the catalog overlay is enabled). Points on the plot will be highlighted if sources are selected in the source catalog table, in the histogram plot (if it exists), and in the Image Viewer (if the catalog overlay is enabled). With the "**Selected only**" toggle, you can update the source catalog table to show only the selected sources. You can use the "**Statistic source**" dropdown menu to select a data column to show its basic statistics at the bottom of the scatter plot.


.. raw:: html

   <img src="_static/carta_fn_catalogue_widget_scatter.png" 
        style="width:100%;height:auto;">


Linear fitting
^^^^^^^^^^^^^^

The "**Linear Fit**" button allow you to fit a straight line to the data points in the current view. Data points outside the current view are not included in the linear fit process. The fitting results are summarized at the top-left corner of the scatter plot.


Catalog histogram plot
------------------------
By selecting "Histogram" mode and identifying one numeric column as the input data, you can generate a histogram plot of the source catalog in the Catalog Histogram Plot Widget.

The Catalog Histogram Plot Widget shows a histogram of one numeric column of a catalog file. The available numeric columns are determined by the “Display” column of the upper table in the Catalog Widget. The lower table in the Catalog Widget determines the data used for plotting a histogram. The table may not show all entries due to the dynamic loading feature. Thus, the histogram plot may not include all entries (after filtering). The "**Plot**" button will request a full download of all entries, and the histogram plot will include all entries (after filtering). The number of bins and the y-axis scale can be customized with the "**Bins**" field and the "**Log scale**" toggle, respectively.


By clicking on a specific histogram bin, source entries of that bin will be highlighted in the source catalog table, in the 2D scatter plot (if it exists), and in the Image Viewer (if the catalog overlay is enabled). A specific histogram bin will be highlighted if source entries of that bin are selected in the source catalog table, in the 2D scatter plot (if it exists), and in the Image Viewer (if the catalog overlay is enabled). With the "**Selected only**" toggle, you can update the source catalog table to show only the selected sources. You can use the "**Statistic source**" dropdown menu to select a data column to show its basic statistics at the bottom of the histogram plot.


.. raw:: html

   <img src="_static/carta_fn_catalogue_widget_histogram.png" 
        style="width:100%;height:auto;">


Linked catalog visualization
------------------------------
The source catalog table, the image overlay, the 2D scatter plot, and the histogram plot are interlinked or cross-referenced. For example, selecting a source or a set of sources in the catalog table will trigger source highlights elsewhere. Alternatively, selecting a source or a set of sources in the 2D scatter plot will trigger source highlights in other plots and the catalog table. 


.. raw:: html

   <img src="_static/carta_fn_catalogLinkedVisualization.png" 
        style="width:100%;height:auto;">

