How to write output files to the simulation output directory
======================================================================================

.. code-block:: Python

    def step(self, mcs):
        output_dir = self.output_dir
        if output_dir is not None:
            # Write output file with unique name by appending MCS to template
            output_path = Path(output_dir).joinpath('step_' + str(mcs).zfill(3) + '.dat')
            with open(output_path, 'w') as f_out:
                f_out.write('{} {} {}\n'.format(1, 2, 3))

*Note*: ``self.output_dir`` is a special variable in each steppable that stores the directory where
the output of the current simulation will be written. Other files can be specified by substituting
``output_dir`` and ``output_path`` with a different directory and file name, respectively.


