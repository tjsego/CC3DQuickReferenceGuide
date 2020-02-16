How to loop over a cell's boundary sites
======================================================================================

.. code-block:: python

    pixel_list = self.get_cell_boundary_pixel_list(cell)
    for boundary_pixel_tracker_data in pixel_list:
        pt = boundary_pixel_tracker_data.pixel
        # commands for each cell boundary pixel (pt) go here


*Note*: Make sure to call the ``BoundaryPixelTracker`` plugin from either the *.xml* or the *.py* file.

