How to loop over all cells
======================================================================================

.. code-block:: python

    for cell in self.cell_list:
        # commands for all cells go here

    for cell in self.cell_list_by_type(self.TYPENAME1, self.TYPENAME2):
        # commands for all cells of cell type "Typename1" or "Typename2" go here


*Note*: Integers specified for all cell types ``Type`` defined in the *.xml* file are assigned to
all steppables as attributes ``TYPE`` (*e.g.*, for a type with name ``Condensing`` and integer = 2,
``self.CONDENSING = 2`` for all steppables).
