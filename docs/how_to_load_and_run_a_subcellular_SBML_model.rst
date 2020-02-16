How to load and run a subcellular SBML model
======================================================================================

.. code-block:: python

    class SBMLSolverSteppable(SteppableBasePy):
        def __init__(self, frequency=1):
            SteppableBasePy.__init__(self, frequency)

        def start(self):
            # Add options that setup SBML solver integrator
            # These are optional but useful when encountering integration instabilities
            options = {'relative': 1e-10, 'absolute': 1e-12}
            self.set_sbml_global_options(options)
            # Specify location of SBML model file for a model of a species "S"
            model_file = 'Simulation/test_1.xml'
            # Specify initial conditions
            initial_conditions = {}
            initial_conditions['S'] = 0.00020
            # Add SBML model with name "dp" to some cells by id
            self.add_sbml_to_cell_ids(model_file=model_file, model_name='dp',
                                      cell_ids=list(range(1, 11)), step_size=0.5,
                                      initial_conditions=initial_conditions)
            # Add free-floating SBML model with name "Medium_dp" to the medium
            self.add_free_floating_sbml(model_file=model_file, model_name='Medium_dp',
                                        step_size=0.5,
                                        initial_conditions=initial_conditions)
            # Add SBML model to cell with id 20
            cell_20 = self.fetch_cell_by_id(20)
            self.add_sbml_to_cell(model_file=model_file, model_name='dp', cell=cell_20)

        def step(self, mcs):
            self.timestep_sbml() # Perform integration for this step in SBML solver
            # Get SBML model current values by model name for cell with id 20
            cell_20 = self.fetch_cell_by_id(20)
            vals_20 = cell_20.sbml.dp.values()
            # Get free-floating SBML model current values by model name for the medium
            vals_ff = self.sbml.Medium_dp.values()
            # Set value for species S1 in free-floating SBML model
            Medium_dp = self.sbml.Medium_dp
            Medium_dp['S'] = 10
            # Delete SBML model from some cells by id
            self.delete_sbml_from_cell_ids(model_name='dp', cell_ids=list(range(1, 11)))
            # Copy SBML solver from cell 20 to cell 25
            cell_25 = self.fetch_cell_by_id(25)
            self.copy_sbml_simulators(from_cell=cell_20, to_cell=cell_25)


