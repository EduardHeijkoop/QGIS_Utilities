# QGIS_Utilities

Contents
- [Funding & Support](#funding---support)
- [Installation](#installation)
- [Scripts](#scripts)
  * [Auto QGIS](#auto-qgis)
- [Citation](#citation)
- [Acknowledgments](#acknowledgments)
- [To Do](#to-do)

## Funding & Support

This work was funded by the NASA Sea Level Change Team (N-SLCT) and performed at the Colorado Center for Astrodynamics Research (CCAR), part of the Ann & H.J. Smead Department of Aerospace Engineering at the University of Colorado Boulder.

<p float "middle">
    <a href="https://www.colorado.edu/aerospace">
        <img src="https://raw.githubusercontent.com/EduardHeijkoop/EduardHeijkoop.github.io/refs/heads/main/Assets/Images/CU_Smead_Logo.png" height=200 alt="CU Aerospace Engineering"/>
    </a>
    <a href="https://www.colorado.edu/ccar">
        <img src="https://raw.githubusercontent.com/EduardHeijkoop/EduardHeijkoop.github.io/refs/heads/main/Assets/Images/CCAR_Logo.jpg" height=200 alt="Colorado Center for Astrodynamics Research"/>
    </a>
</p>


<p float "middle">
    <a href="https://sealevel.nasa.gov">
        <img src="https://raw.githubusercontent.com/EduardHeijkoop/EduardHeijkoop.github.io/refs/heads/main/Assets/Images/NSLCT_Logo.png" height=200 alt="NASA Sea Level Change Team" />
    </a>
</p>



## Installation

Note: this software has only been tested on a Unix-based operating system (Mac OS X and Ubuntu Linux). No guarantees for Windows can be made.

Clone the repository:

    git clone https://github.com/EduardHeijkoop/QGIS_Utilities.git

Create a new conda environment with the right packages:

    conda env create -f pyqgis.yml

Make sure QGIS is installed. You will need to edit the installation path in the `qgis_config.ini` file (under `CONFIG/install_dir`) to point to your installation location. The default install location on Mac OS X is `~/Library/Application Support/QGIS/QGIS3` and on Ubuntu Linux is `/usr/bin/qgis`.

## Scripts

### Auto QGIS

This script will automate the generation of maps of inundation scenarios using a list of input files. The `Defaults` directory contains all the necessary default files to run a scenario. 

#### Configuration & Customization

As a Jupyter Notebook, individual cells can be run, or the whole script can be run sequentially. The major changes can be made in the `qgis_config.ini` configuration file, which is read by the notebook. Make sure the conda environment is active before running the notebook.

The main entries to change to generate new maps per location are:
- The input csv (under `GENERAL_PATHS/input_csv`). This input file requires a header line with the column names ("filename" and "legend entry") and the two columns with the associated entries. The first column needs to contain the full paths to the `.shp` inundation files of inundation, e.g. 
`/Users/myname/Documents/Projects/PEERS/Philippines/LapuLapuCity/Inundation/Philippines_LapuLapu_Inundation_SLR_0p00m_FES2014_MHHW.shp`. This file should have a similarly named `_connectivity.shp` and `_disconnected.shp` file in the same directory as the main file. The second column should have the name of the desired legend entry in the map, e.g. "Inundation Risk baseline (= 0.00 m)\nabove MHHW" where `\n` is used to denote a new line. 
- A tilde (~) may be used to replace the name of a user's home directory for privacy reasons, and for ease of sharing among users.
- Individual zoom boxes can be added to the `qgis_config.ini` file to customize zooms. These bounding boxes must be listed under `BBOX` in the following order: minx, miny, maxx, maxy. The software will render the boxes in the desired color (as defined under `OPTIONS/color_bbox`) for the map showing the entire study region, after which a new render will be created showing only the extents defined by the zoom box. 
- Set the testing flag to `True` if you want to perform a test run for speed purposes. This will run the user-defined configuration on the first two entries only, so the user can check to see if the output is as desired. If satisfactory, set the flag to `False` and the software will rerun on all entries.
- When running multiple scenarios it is prudent to restart the kernel every time a user wants to run a new scenario. 
- Extra layers can be added and rendered with one of the default styles. Each extra layer must have `filename`, `legend_name`, `legend_visible` and `style` appended with `_i` (where `i` starts at 0 and goes up depending on how many extra layers are added, so `_0`,`_1`,`_2` etc). The full path to the filename must be specified, a legend name must be entered and `True`/`False` must be entered as to whether or not the entry is added to the legend. Finally, a style (nodata.qml, outline.qml or coast.qml) must be selected.




## Citation

Please cite this repository and my name if you use this software to create maps.

## To Do

- Add dynamic x/y offset & resize based on map size, lon/lat extents, etc. Currently only a select few locations are supported, and the user much manually adjust it themselves for other locations.
- Publish work to Zenodo and add DOI to citation.