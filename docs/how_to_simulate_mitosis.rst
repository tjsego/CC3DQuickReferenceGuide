How to simulate mitosis
======================================================================================

A special steppable class ``MitosisSteppableBase`` implements convenient mitosis-related methods.
Mitosis events are triggered in ``step`` and handled in ``update_attributes``:

.. code-block:: python

    class MitosisSteppable(MitosisSteppableBase):
        def __init__(self, frequency=1):
            MitosisSteppableBase.__init__(self, frequency)
            # Select relative position of parent and child after mitosis
            #   0  - parent and child positions will be randomized between mitosis event
            #   -1 - parent appears on the 'left' of the child
            #   1  - parent appears on the 'right' of the child
            self.set_parent_child_position_flag(-1)

        def step(self, mcs):
            # Make a Python list of cells to divide
            cells_to_divide = []
            for cell in self.cell_list:
                if <mitosis_condition_here>:
                    cells_to_divide.append(cell)
            # Implement oriented mitosis by applying an available cell division method
            for cell in cells_to_divide:
                self.divide_cell_random_orientation(cell)
                # self.divide_cell_orientation_vector_based(cell, 1, 1, 0)
                # self.divide_cell_along_major_axis(cell)
                # self.divide_cell_along_minor_axis(cell)

        def update_attributes(self):
            # Updates to parent cell attributes before cloning them go here
            self.parent_cell.targetVolume /= 2.0 # Example: reduce parent target volume
            # Clone all parent attributes to child
            self.clone_parent_2_child()
            # Changes to child cell attributes after clone go here
            self.child_cell.type = self.parent_cell.ANOTHERTYPE # Example: change type

*Note*: ``update_attributes`` is called for every call to a cell division method (*e.g.*,
``divide_cell_random_orientation``), where ``self.parent_cell`` is the cell object passed to
the cell division method, and ``self.child_cell`` is the cell object added to simulation by mitosis.
