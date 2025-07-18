File header
===========

The File header dialog provides a way to view and export the header information of an image file. It is useful for checking the metadata of the image, such as WCS information, data type, and other relevant parameters.

Using the File Header Dialog, you can view a summary using the "File information" tab or full header of an image file using the "Header" tab. To search for a keyword, click the "**search**" button in the header tab. If you want to save the file header as a text file, use the "**export**" button.

.. raw:: html
 
   <a href="_static/carta_fn_fileHeader.png" target="_blank">
       <img src="_static/carta_fn_fileHeader.png" 
           style="width:80%;height:auto;">
   </a>

.. warning::
    The displayed header information adopts 1-based indexing same as the FITS standard. For example, the first pixel in a 2D image is at (1, 1) instead of (0, 0) at the center of the bottom-left corner pixel. This is different from the 0-based indexing used in elsewhere in CARTA. The 1-based indexing is used to be consistent with the FITS standard and to avoid confusion when users are familiar with FITS headers.