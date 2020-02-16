How to attach/access/modify a dictionary to a cell
======================================================================================

Each cell, by default, has a Python dictionary ``dict`` attached to it as a cell attribute.

.. code-block:: python

    for cell in self.cell_list:
        # get custom cell attributes 'custom_cell_val1' and 'custom_cell_val2'
        # with keys 'custom_cell_keyA' and 'custom_cell_keyB'
        custom_cell_val1 = cell.dict['custom_cell_keyA']
        custom_cell_val2 = cell.dict['custom_cell_keyB']
        # do calculations for custom cell attributes here
        # <calculations -> custom_cell_val1, custom_cell_val2>
        # store custom cell attributes
        cell.dict['custom_cell_keyA'] = custom_cell_val1
        cell.dict['custom_cell_keyB'] = custom_cell_val2


