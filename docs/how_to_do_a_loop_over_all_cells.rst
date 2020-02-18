How to loop over all cells
======================================================================================

.. code-block:: python

    for cell in self.cell_list:
        # commands for all cells go here

    for cell in self.cell_list_by_type(self.TYPENAME1, self.TYPENAME2):
        # commands for all cells of cell type "Typename1" or "Typename2" go here

