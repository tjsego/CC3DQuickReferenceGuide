How to share data between steppables
======================================================================================

All steppables, by default, can share data with each other by accessing a global Python dictionary as an
attribute ``shared_steppable_vars``:

.. code-block:: Python

    class InitiatorSteppable(SteppableBasePy):
        def __init__(self, frequency=1):
            SteppableBasePy.__init__(self, frequency)

        def start(self):
            self.shared_steppable_vars['x_shared'] = 0

    class PrinterSteppable(SteppableBasePy):
        def __init__(self, frequency=1):
            SteppableBasePy.__init__(self, frequency)

        def step(self, mcs):
            print('x_shared=', self.shared_steppable_vars['x_shared'])

