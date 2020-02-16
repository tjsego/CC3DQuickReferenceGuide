How to loop over all lattice sites
======================================================================================

.. code-block:: python

    for x, y, z in self.every_pixel():
        # commands for each lattice site go here


*Note*: Make sure to call the ``PixelTracker`` plugin from either the *.xml* or the *.py* file.

