Spectral line query
===================

CARTA supports an *initial* implementation of spectral line ID overlay on a Spectral Profiler Widget based on the data from the Splatalogue service (https://splatalogue.online). The query is made by defining a spectral range in frequency or wavelength and, optionally, a lower limit of CDMS/JPL line intensity (logarithmic). The spectral range can be defined as "from-to" or "center-width". Other filters, such as filtering by species name, energy range, etc., can be applied *after* the data are retrieved from the Splatalogue. By clicking the "**Query**" button, molecular data will be retrieved from the Splatalogue service. 

.. note::
   The current implementation has some limitations when making a query to the Splatalogue service:

   * The allowed maximum query range, equivalent in frequency, is 20 GHz.
   * The actual query is made with a frequency range in MHz rounded to integer.
   * Only the lines from CDMS and JPL catalogs will be returned when an intensity limit is applied.
   * Up to 100,000 lines are displayed. 

   Improvements to the above limitations will be made in future releases.


.. raw:: html

   <a href="_static/carta_fn_linequery_widget.png" target="_blank">
       <img src="_static/carta_fn_linequery_widget.png" 
           style="width:100%;height:auto;">
   </a>

Once a query is successfully made, the line catalog will be displayed in the tables. The upper table shows the column information in the catalog with options to show or hide a specific column. The actual line catalog is displayed in the lower table. The line catalog table accepts sub-filters such as partial string match or value range. For numeric columns, supported operators are:

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

For string columns, a partial match is adopted. For example, :code:`CH3` (no quotation) will return entries containing the "CH3" string.

The "Shifted Frequency" column is computed based on the user input of a velocity or a redshift. This "Shifted Frequency" is adopted for line ID overlay on a Spectral Profiler Widget. You can use the checkbox to select a set of lines to be overplotted on a Spectral Profiler Widget. The maximum number of line ID overlays is 1000.


The text labels of the line ID overlay are shown dynamically based on the zoom level of a profile. Different line ID overlays (with different velocity shifts) can be created on different Spectral Profiler Widgets via the "**Spectral Profiler**" dropdown menu. By clicking the "**Clear plot**" button, the line ID overlay on the selected Spectral Profiler will be removed.

.. note::
   The sorting function in the line table will be available in a future release.

.. note::
   When there are multiple profiles from different image cubes in the plot, and the x-axis is in velocity, the line ID overlay function is disabled.