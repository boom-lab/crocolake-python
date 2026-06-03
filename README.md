## CrocoLake-Python

CrocoLake-Python is a collection of Jupyter notebooks that shows how to interface with [CrocoLake](https://crocolakedocs.readthedocs.io/en/latest/) and Argo's parquet databases with Python.

### Table of Contents
1. [Usage](#usage)
2. [Examples](#examples)
3. [Databases](#databases)
4. [Contact](#contact)

### Usage

CrocoLake itself is a dataset made of a collection of parquet files and as such is language-agnostic. The following instructions are to install the python packages recommended to run the notebook examples (e.g. pandas to read the data, matplotlib to visualize plots, etc.).

#### python

Create your local environment (creates a folder in your current directory)
`virtualenv crocolake`

Activate the new python environment
`source crocolake/bin/activate`

Install the required packages
`pip install .`

Launch jupyter lab to access the notebooks:
`jupyter lab`

If you don't have virtualenv in your machine, you can install it with
`pip install virtualenv`

#### conda

Create the local environment
`conda env create -f environment.yml`

Activate the environment:
`conda activate crocolake`

Launch jupyter lab to access the notebooks:
`jupyter lab`

#### Notebooks
You can then launch any notebook from the `notebooks` folder and execute it. Each example needs a specific dataset, and it contains code to download it to your local machine.

Note that there are a couple of ways to load parquet datasets in a dataframe in Python: using [pyarrow](https://arrow.apache.org/docs/python/index.html) and using [dask](https://www.dask.org/). [Example 1](notebooks/Example_1_ArgoBGC_Map_Oxygen.ipynb) and [Example 2](notebooks/Example_2_CrocoLakePHY_Map_Temperature.ipynb) show both, while the other examples use the one that in my experience is most efficient (i.e. dask).

### Examples

The [notebooks](notebooks/) folder contains four examples/tutorials:

1. [Example 1](notebooks/Example_1_ArgoBGC_Map_Oxygen.ipynb) shows how to make a map of dissolved oxygen content in the North West Atlantic;
2. [Example 2](notebooks/Example_2_CrocoLakePHY_Map_Temperature.ipynb) shows how to make a map of temperature measurements in the North West Atlantic, including information about the source (Argo, GLODAP, or Spray Gliders);
3. [Example 3](notebooks/Example_3_ArgoPHY_QC_Temperature-Salinity_Profiles.ipynb) shows how to make temperature-salinity plots from Argo QC-ed measurements;
4. [Example 4](notebooks/Example_4_Animation_Oxygen.ipynb) shows how to make an animation of Argo's fleet growth over time on a world map;
4. [Example 5](notebooks/Example_5_CrocoLakeBGC_Map_Oxygen.ipynb) shows how to make a map of dissolved oxygen measurements in the Pacific off the coast of California.

### Databases

The following databases are currently available:

* CrocoLake: contains the best available data from Argo, GLODAP, and Spray Gliders. [More details here](https://crocolakedocs.readthedocs.io/en/latest/crocolake.html). [This example uses CrocoLake](notebooks/Example_2_CrocoLakePHY_Map_Temperature.ipynb).
* Argo 'QC': contains the best available data, that is real time values are reported only when delayed values are not available. This version is the same used in CrocoLake, and [here](https://crocolakedocs.readthedocs.io/en/latest/available_datasets.html#argo) you can find more details on how it is generated. [This example uses Argo 'QC'](notebooks/Example_3_ArgoPHY_QC_Temperature-Salinity_Profiles.ipynb).
* Argo 'ALL': contains all real time and adjusted variables as reported in the core ('<PLATFORM_NUMBER>_prof.nc') and synthetic ('<PLATFORM_NUMBER>_Sprof.nc') profile files, for the physical and biogeochemical versions respectively. [Both this](notebooks/Example_1_ArgoBGC_Map_Oxygen.ipynb) and [this examples](notebooks/Example_4_Animation_Oxygen.ipynb) use Argo 'ALL'.

Each database comes in 'PHY' and 'BGC' versions.

### Contact

For any questions, bugs, missing information, etc, open an issue or [get in touch](enrico.milanese@whoi.edu)!
