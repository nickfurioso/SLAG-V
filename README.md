# SLAG-V
SLAG-V is a semi-Lagrangian guiding-center-Lorentz hybrid approach to resolving particle fluxes at GEO. SLAG-V models Earth's magnetosphere macroscopically using proton distributions that propagate kinetically according to BATSRUS MHD fields.

List of what the files are and what they do:
- mmap_data: adjustments to the interpolated MHD file that allow it to be read better into SLAG-V

Make sure to adjust the datetime (sim_start_unix) across all files to match your date of interest. Everything is currently set up to begin on December 31st, 2025 at 00:00 and end at 02:00 UTC (STORM_DURATION). All the associated parameters are taken from that time as well.

This includes the ephemeris of the GOES-18 satellite, the Kp index (KP_INDEX), and solar parameters (N_sw_input, V_sw_input, Vz_input). Each of these parameters is hardcoded and needs to be adjusted to match any new date other than December 31st, 2025, 00:00 to 02:00.

The bins across the 5-D phase space (spatial, energy, pitch angle) can be adjusted to your desired resolution. (sim_x, sim_y, sim_z, sim_Ek, sim_alpha)

If initializing your own MHD run, make sure to use the proper values to initialize that simulation according to the date and time you want to measure.

All files that are needed are included in the repository here. You will need to update the paths for yourself locally to match where you have the data stored in the code
