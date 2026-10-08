# SLAG-V
SLAG-V is a semi-Lagrangian guiding-center-Lorentz hybrid approach to resolving particle fluxes at GEO. SLAG-V models Earth's magnetosphere macroscopically using proton distributions that propagate kinetically according to BATSRUS MHD fields.

List of what the files are and what they do:
- mmap_data: adjustments to the interpolated MHD file that allow it to be read better into SLAG-V
      - Each file represents the gap files (outdated, not used) and the MHD files that are saved individually for each variable (B_x, B_y, B_z magnetic field magnitudes, gradients of those quantities, the grid structure in time, x, y, and z, the kappa curvature vector in each direction, the boltzmann-scaled temperature kT, number density n, and bulk velocity V in each direction)
- 3d__var_1_e20251231-0xx000-000.out: Output MHD fields from BATSRUS. The time xx are replaced with the hour and time, so 1:30 UTC is represented by ...013000-000.out.
- 5D_distribution.ipynb: Main simulation code
- dn_magn-l2-avg1m_g18_d20251231_v2-0-4.nc: magnetic Bz readings from GOES-18 from 00:00 - 02:00 UTC
- Earth.jpg: Earth image for plotting
- goes18_ephemeris_ssc_20250101_v01.cdf: Satellite ephemeris of GOES-18 from 00:00 - 02:00 UTC
- IGRF_Baked_Float.pkl: File containing all the IGRF data required to run the code (not important to the actual calculations, but still needs to be edited out of the code)
- igrf14coeffs.txt: IGRF 14 coefficients given in a text file
- IGRFGridValues.ipynb: file that creates IGRF_Baked_Float.pkl
- Interpolators_4D_float32.pkl: Interpolated MHD fields given in space and time in single-precision
- LICENSE: Apache License
- ops_seis-l1b-mpsl_g18_d20251231_v0-0-0: MPS-LO GOES-18 readings from 00:00-02:00 UTC
- plot_all3.ipynb: plotting file that requires outputs from all three solvers (LAG-GC, LAG-L, and SLAG-V). However, it can be edited to just require output from a single solver. Most up-to-date version of the plots
- plot_SLACMAVS.ipynb: Old version of the plotting code that plots LAG-GC alone
- PrecomputeGridValuesTime.ipynb: File that creates Interpolators_4D_Float32.pkl
- README: READ ME file
- sci_mpsh-l2-avg1m_g18_d20251231_v2-0-2: MPS-HI GOES-18 readings from 00:00-02:00 UTC

Make sure to adjust the datetime (sim_start_unix) across all files to match your date of interest. Everything is currently set up to begin on December 31st, 2025 at 00:00 and end at 02:00 UTC (STORM_DURATION). All the associated parameters are taken from that time as well.

This includes the ephemeris of the GOES-18 satellite, the Kp index (KP_INDEX), and solar parameters (N_sw_input, V_sw_input, Vz_input). Each of these parameters is hardcoded and needs to be adjusted to match any new date other than December 31st, 2025, 00:00 to 02:00.

The bins across the 5-D phase space (spatial, energy, pitch angle) can be adjusted to your desired resolution. (sim_x, sim_y, sim_z, sim_Ek, sim_alpha)

If initializing your own MHD run, make sure to use the proper values to initialize that simulation according to the date and time you want to measure.

All files that are needed are included in the repository here. You will need to update the paths for yourself locally to match where you have the data stored in the code
