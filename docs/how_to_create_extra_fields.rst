How to create extra fields:
======================================================================================

.. code-block:: Python

    class ExtraFieldsSteppable(SteppableBasePy):
        def __init__(self, frequency=10):
            SteppableBasePy.__init__(self, frequency)
            # Create extra fields
            self.create_scalar_field_py("sFieldP") # pixel-based scalar field
            self.create_vector_field_py("vFieldP") # pixel-based vector field
            self.create_scalar_field_cell_level_py("sFieldC") # cell-based scalar field
            self.create_vector_field_cell_level_py("vFieldC") # cell-based vector field

        def step(self, mcs):
            # access extra fields by names passed to instantiation methods in __init__
            scalar_field_pixel = self.field.sFieldP
            vector_field_pixel = self.field.vFieldP
            scalar_field_cell = self.field.sFieldC
            vector_field_cell = self.field.vFieldC
            # modify some pixel-based values; sites are accessed just like the cell field
            scalar_field_pixel[0, 1, 2] = 3.0
            vector_field_pixel[1, 2, 3, 0] = 1.0 # vector components are in dim. 4
            # modify some cell-based values
            cell = self.cell_field[0, 1, 2]
            scalar_field_cell[cell] = cell.id * 2
            vector_field_cell[cell] = [0.0, 1.0, 2.0]

*Note*: Extra fields do not necessarily have to be created inside ``__init__``, though full functionality
associated with fields requires it.

*Note*: Extra fields do not directly participate in any core calculations. Rather, they can be used to store
data associated with core calculations at each lattice site that can, like other data, be passed to the
CC3D computational core or visualized in Player.

