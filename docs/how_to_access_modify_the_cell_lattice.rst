How to access/modify the cell lattice
======================================================================================

.. code-block:: Python

    pt = CompuCell.Point3D() # define a lattice vector
    pt.x = 3; pt.y = 2; pt.z = 0 # specify its coordinates
    cell = self.cell_field[pt.x, pt.y, pt.z] # access the cell or Medium at (3, 2, 0)
    # create an extension of that cell in another location (3, 1, 0)
    pt.x = 3; pt.y = 1; pt.z = 0
    self.cell_field[pt.x, pt.y, pt.z] = cell
    # place a brand new cell over a subdomain with type "Condensing" defined in .xml file
    self.cell_field[10:14, 10:14, 0] = self.new_cell(self.CONDENSING)



