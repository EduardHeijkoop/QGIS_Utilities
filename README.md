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

Make sure QGIS is installed. You will need to edit the installation path in the `qgis_config.ini` file to point to your installation location. 

## Scripts

### Auto QGIS

This script will automate the generation of maps of inundation scenarios using a list of input files.

#### Configuration

As a Jupyter Notebook, individual cells can be run, or the whole script can be run sequentially. The major changes can be made in the `qgis_config.ini` configuration file, which is read by the notebook. Make sure the conda environment is active before running the notebook.

The main entries to change to generate new maps per location are the input csv (under `GENERAL_PATHS/input_csv`)