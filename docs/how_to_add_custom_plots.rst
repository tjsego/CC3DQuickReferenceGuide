How to add custom plots
======================================================================================

.. code-block:: python

    class VisualizationSteppable(SteppableBasePy):
        def __init__(self, frequency=1):
            SteppableBasePy.__init__(self, frequency)

        def start(self):
            # Create plot window for Cell 1 volume and surface
            self.plot_win1 = self.add_new_plot_window(
                title='Volume and surface area of Cell 1',
                x_axis_title='Monte Carlo Step (MCS)',
                y_axis_title='Variables',
                x_scale_type='linear',
                y_scale_type='log',
                grid=True)
            self.plot_win1.add_plot("Volu1", style='Dots', color='red', size=5)
            self.plot_win1.add_plot('Surf1', style='Steps', color='black', size=5)
            # Create plot window for histogram of cell volumes ans surfaces
            self.plot_win2 = self.add_new_plot_window(
                title='Cell volume/surface histogram',
                x_axis_title='Number of cells',
                y_axis_title='Volume/surface (pixels^n)')
            # alpha is transparency: = 0 -> transparent, = 255 -> opaque
            self.plot_win2.add_histogram_plot(plot_name='voluH', color='green', alpha=100)
            self.plot_win2.add_histogram_plot(plot_name='surfH', color='red', alpha=100)

        def step(self, mcs):
            # Collect cell data
            cell1_volu = 0
            cell1_surf = 0
            volu_list = []
            surf_list = []
            for cell in self.cell_list:
                volu_list.append(cell.volume)
                surf_list.append(cell.surface)
                if cell.id == 1:
                    cell1_volu = cell.volume
                    cell1_surf = cell.surface
            # Update plots
            self.plot_win1.add_data_point('Volu1', mcs, cell1_volu)
            self.plot_win1.add_data_point('Surf1', mcs, cell1_surf)
            self.plot_win2.add_histogram(plot_name='VoluH', value_array=volu_list,
                                         number_of_bins=10)
            self.plot_win2.add_histogram(plot_name='SurfH', value_array=surf_list,
                                         number_of_bins=10)
            if self.output_dir is not None: # Export histogram plots
                # Export data in CSV format (needs "from pathlib import Path")
                txt_path = Path(self.output_dir).joinpath("Hist_" + str(mcs) + ".txt")
                self.plot_win.save_plot_as_data(txt_path, CSV_FORMAT)
                # export image with size 1000 x 1000 (default is 400 x 400)
                png_path = Path(self.output_dir).joinpath("Hist_" + str(mcs) + ".png")
                self.plot_win.save_plot_as_png(png_path, 1000, 1000)

