How to do a loop over cell and medium sites
======================================================================================

.. code-block:: python

    # Loop over all pixels of cell with id = 1
    cell_1 = self.fetch_cell_by_id(1)
    for ptd in self.get_cell_pixel_list(cell_1)
        this_pixel = ptd.pixel

    # Loop over all current medium pixels
    for ptd in self.pixel_tracker_plugin.getMediumPixelSet():
        this_pixel = ptd.pixel


*Note*: Make sure to load the ``PixelTracker`` plugin from either the *.xml* or the *.py* file.
For tracking medium sites, make sure to first enable the medium tracking option for ``PixelTracker``.

