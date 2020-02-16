How to loop over a cells' neighbors
======================================================================================

.. code-block:: python

    for cell in self.cell_list:
        for neighborTuple in self.get_cell_neighbor_data_list(cell):
            neighborCell = neighborTuple[0]
            # commands for all neighbors go here
            if neighborCell:
                # commands for all neighbors, excluding medium, go here

*Note*: Make sure to call ``NeighborTracker`` plugin from either the *.xml* or the *.py* file.
Neighbor cells have the same properties as those listed before for cells. To access them, substitute ``cell``
with ``neighborTuple[0]``.

