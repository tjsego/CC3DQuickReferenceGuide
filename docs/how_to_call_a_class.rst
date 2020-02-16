How to call a CC3D steppable class
======================================================================================
In the main Python file ``<mainFile.py>``, register custom steppables by following the procedure
shown between the first and last lines:

.. code-block:: python

    from cc3d import CompuCellSetup # First line: import CompuCellSetup

    from <SteppablesFile> import <NameOfClass> # Import steppable from steppables file
    CompuCellSetup.register_steppable(steppable=<NameOfClass>(frequency=1)) # Register
    # <Additional steppables registered here...>

    CompuCellSetup.run() # Last line: run CC3D


*Note*: ``<NameOfClass>`` refers to the name of the steppable class defined in the Python script
``<SteppablesFile>`` (*e.g.*, ``class MySteppable(SteppableBasePy)`` in ``MySteppables.py``).


