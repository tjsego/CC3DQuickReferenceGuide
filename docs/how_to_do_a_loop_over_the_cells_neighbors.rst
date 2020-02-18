How to loop over a cell's neighbors
======================================================================================

.. code-block:: python

    for cell in self.cell_list:
        for neighbor, common_surface_area in self.get_cell_neighbor_data_list(cell):
            # commands for all neighbors go here
            if neighbor:
                # commands for all neighbors, excluding medium, go here

*Note*: Make sure to load ``NeighborTracker`` plugin from either the *.xml* or the *.py* file.
Neighbor cells have the same properties as those listed before for cells. To access them, substitute ``cell``
with ``neighbor``.

