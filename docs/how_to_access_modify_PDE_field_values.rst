How to access/modify PDE field values
======================================================================================

.. code-block:: Python

    # Get PDE field defined in .xml with name "MyFieldName"
    my_field = CompuCell.getConcentrationField("MyFieldName")
    # Blend at (0, 0, 0) with a neighbor
    my_field[0, 0, 0] = (my_field[0, 0, 0] + my_field[1, 0, 0]) / 2.0
    minVal = my_field.min() # Get current field minimum
    maxVal = my_field.max() # Get current field maximum


