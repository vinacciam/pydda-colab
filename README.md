# PyDDA-Chicago-DualDoppler

This project uses **PyDDA** and **Py-ART** to perform dual-Doppler wind retrievals over the Chicagoland area using radar data from the **KLOT** (NEXRAD) and **TORD** (TDWR) radars. The primary goal is to study the kinematics of a storm on **May 16, 2025**, including inflow, outflow, shear, and rotation, using a variational retrieval approach implemented in PyDDA.

## Overview

- **Date:** May 16, 2025 (00–01 UTC)
- **Radars used:**  
  - KLOT (Romeoville, IL – S-band NEXRAD)  
  - TORD (Countryside, IL – C-band TDWR)
- **Sounding:** 1 Hz resolution from Morris, IL (UIUC/Nesbitt group)
- **Tools:**  
  - [PyDDA](https://github.com/openradar/PyDDA) for wind retrieval  
  - [Py-ART](https://github.com/ARM-DOE/pyart) for radar data processing

## Workflow Summary

1. **Data Loading & Preprocessing**  
   - Load and inspect radar volumes with Py-ART  
   - Apply velocity dealiasing  
   - Grid volumes to common Cartesian space

2. **Sounding Integration**  
   - Convert .GPS sounding file to .CSV  
   - Use as background field for PyDDA retrievals

3. **Wind Retrieval**  
   - Customize PyDDA script for variational dual-Doppler analysis  
   - Cost function includes terms for:
     - Mass continuity
     - Radar radial wind agreement
     - Background constraint from sounding
     - Smoothness

4. **Visualization**  
   - Plot reflectivity, radial velocity, and 3D wind vectors  
   - Identify inflow, outflow, and shear regions

## Directory Structure

/notebooks/ → Jupyter Notebooks for end-to-end workflow
/data/ → Processed radar and sounding data (not included)
/figures/ → Output visualizations of reflectivity and wind fields
/scripts/ → Core PyDDA wind retrieval and plotting scripts

## Results

- Captured inflow and storm-scale rotation features not visible with single-radar scans
- First known dual-Doppler wind retrieval over Chicagoland using open-source tools
- Supports future work with CROCUS and higher-resolution radars

## Citation

If using this workflow, please cite:

- Jackson, B., et al. (2023). PyDDA: The Pythonic Doppler Radar Analysis Toolkit. [https://github.com/openradar/PyDDA](https://github.com/openradar/PyDDA)  
- Helmus, J. J., & Collis, S. M. (2016). The Python ARM Radar Toolkit (Py-ART). *JORS*, 4(1), e25. [https://doi.org/10.5334/jors.119](https://doi.org/10.5334/jors.119)

## Author

**Malachi Vinaccia**  
CCI Intern, Argonne National Laboratory  
University of Illinois Urbana-Champaign  
*Summer 2025*
