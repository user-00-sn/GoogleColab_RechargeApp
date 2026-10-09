## Cloud computing and global satellite products for potential groundwater recharge estimation: Application to the Basin of Mexico
Elizabeth Guzmán-Hidalgo, Saúl Arciniega-Esparza & Antonio Hernández-Espriú 

**Format:** Jupyter Notebook compatible with Google Colab
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/user-00-sn/GoogleColab_RechargeApp/blob/main/GEE_Recharge.ipynb)
[(https://colab.research.google.com/github/user-00-sn/GoogleColab_RechargeApp/blob/main/GEE_Recharge.ipynb)]

## i. Project description

This code implements a Thornthwaite-Mather (T-M) water balance model to estimate groundwater potential recharge (GWpr) using global satellite products and cloud computing capabilities through Google Earth Engine (GEE). The model integrates precipitation data (CHIRPS), potential evapotranspiration (MODIS), and soil properties (OpenLandMap) to generate spatially mean annual GWpr estimates and monthly time series for the Basin of Mexico and at the global scale.

## ii. Repository structure

The code is organized in a single Jupyter Notebook file containing the following sections:

| Cell | Description |
|------|-------------|
| **Markdown initial** | General instructions, credits, and model context. |
| **Cell 1** | User authentication in Google Earth Engine using a Google Cloud project. |
| **Cell 2** | Installation of dependencies (PyCRS, hvplot), library loading, and function definitions based on the implementation developed by Attard (2022) and available in Google Earth Engine (GEE) community tutorials. The code consists of soil property processing, implementation of the Saxton–Rawls pedotransfer functions, climate data processing, temporal resampling, and the core Thornthwaite–Mather model. |
| **Cell 3** | Interactive interface with ipywidgets to define simulation parameters (analysis period, root depth, PET bias correction factor, visualization parameters, and analysis region), model execution, interactive map visualization, and CSV time series download. |

## iii. Requirements and dependencies

The code requires the following Python libraries:

| Library | Purpose |
|---------|---------|
| `ee` (Earth Engine API) | Access to geospatial data and cloud processing |
| `geemap` | Interactive map visualization |
| `ipywidgets` | Interactive user interface |
| `hvplot` / `pandas` | Time series generation and handling |
| `folium` | Base maps for visualization |
| `numpy` | Numerical operations |
| `requests` | Loading geometries from remote JSON file |

## iv. Usage instructions

The cells can be executed using the play button.

## 1. Authenticate Google Earth Engine project
You need a Google Cloud account and a project linked to Google Earth Engine for non-commercial use. You can follow [this tutorial](https://www.youtube.com/watch?v=-kUuQF_D4Jw) if you don't have an active project.

You can find the Project ID for your Google Earth Engine account (https://code.earthengine.google.com/) in the “Project info” section under your profile. Copy and paste the Project ID into the Google Earth Engine User authentication field.
## 2. Install requirements and load libraries

This section installs the required libraries and loads the visualization packages needed to run the potential recharge model in Google Earth Engine. Functions are defined for the acquisition and preprocessing of input variables, including soil texture properties and climatological data on precipitation and potential evapotranspiration. The functions implementing the Thornthwaite-Mather water balance model are then defined to generate a new dataset at a monthly temporal scale, with bands corresponding to potential recharge (rech), precipitation (pr), potential evapotranspiration (pet), accumulated potential water loss (apwl), and soil water storage at field capacity (st).

## 3. Run application
This section implements an interactive panel in which users can define the following parameters:

**Start and End year:**
Allows the simulation period to be defined with a maximum duration of five years. The sliders are dynamically linked to prevent exceeding this range, thereby restricting the selection of longer simulation periods.

**Root depth:**
Allows the definition of an average rooting depth, in meters, representative of the study area.

**PET bias factor:**
Allows the definition of a correction factor applied to the MODIS potential evapotranspiration dataset, enabling the adjustment (increase or decrease) of PET values in cases where systematic overestimation or underestimation relative to reference data or field observations has been identified within the study area.

**Visualization parameters:**
Allows the definition of the color scale ranges, in millimeters, for the output maps (recharge, precipitation, and PET).

**Select analysis zone:**
Allows the spatial domain of the estimation to be defined, which may correspond to the entire Basin of Mexico, a specific aquifer within the basin, or, if left blank, a global estimation is produced.

**Run model:**
Generates spatial maps of Precipitation, PET (potential evapotranspiration), and Recharge for the previously selected area. If a simulation area is specified in the "Select analysis zone" field, the model also produces monthly time series for that area; otherwise, only global maps are generated.

**Download Series:**
Enables the export of the simulated time series in CSV format for the selected simulation area.

## References
Attard, G. G. (2022). Implementation of the Thornthwaite-Mather procedure to map groundwater recharge [Código fuente]. Google Earth Engine Tutorials. https://developers.google.com/earth-engine/tutorials/community/groundwater-recharge-estimation

## Cite this work:
Guzmán-Hidalgo, E., Arciniega-Esparza, S. & Hernández-Espriú, A. Cloud computing and global satellite products for potential groundwater recharge estimation: application to the Basin of Mexico. Model. Earth Syst. Environ. 12, 268 (2026). https://doi.org/10.1007/s40808-026-02930-5
