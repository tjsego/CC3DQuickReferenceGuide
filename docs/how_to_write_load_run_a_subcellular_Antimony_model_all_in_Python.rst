How to write/load/run a subcellular Antimony model all in Python
======================================================================================

.. code-block:: python

    class AntimonySolverSteppable(SteppableBasePy):

        def __init__(self,frequency=1):
            SteppableBasePy.__init__(self,frequency)

        def start(self):
            # Define Antimony model with a Python multi-line string
            antimony_model_string = """model rkModel()
            <Antimony model specification goes here>
            end"""

            options = {'relative': 1e-10, 'absolute': 1e-12}
            self.set_sbml_global_options(options)
            step_size = 1e-2

            for cell in self.cell_list:
                self.add_antimony_to_cell(model_string=antimony_model_string,
                                          model_name='dp',
                                          cell=cell,
                                          step_size=step_size)

        def step(self):
            self.timestep_sbml()

*Note*: All SBML model instantiations methods have corresponding Antimony methods. Antimony models
are translated into SBML models, which are then passed to the corresponding SBML instantiation methods.
As such, after instantiation they can be accessed and manipulated in the same ways as models specified
using SBML model specification.

*Note*: Antimony models can also be specified in separate text files and loaded by instead passing the
location of the file to an instantiation methods using the keyword argument ``model_file`` (as
in SBML methods).