# gridfinder

Algorithm for guessing MV grid network based on NTL. An adaptation of [this work from Facebook](https://github.com/facebookresearch/many-to-many-dijkstra).

gridfinder uses NASA night time lights imagery to as an indicator of settlements/towns with grid electricity access. Then a minimum spanning tree is calculated for these connect points, using the Djikstra algorithm and using existing road networks as a cost function.

The algorithm looks as follows in process, guessing the grid network for Uganda:

[![Animated algorithm](gridfinder-animated.gif)]()

## Input requirements
gridfinder requires the following data sources:
- NASA VIIRS data, monthly and annual composites available [here](https://ngdc.noaa.gov/eog/viirs/download_dnb_composites.html).
- OSM highway data, most easily available using the [HOT Export Tool](https://export.hotosm.org/en/v3/), otherwise [BBBike](https://extract.bbbike.org/) or [geofabrik](https://download.geofabrik.de/), depending on your needs.

## Model usage

To get to grips with the API and steps in the model, open the Jupyter notebook `example.ipynb`. This repository  includes the input data needed to do a test run for Burundi, so it should be a matter of openening the notebook and running all cells.

## Installation

**Requirements**

gridfinder requires Python >= 3.5 with the following packages installed:
 - `numpy` >=1.2.0
 - `scikit-image` >=0.14.1
 - `rasterio` >=1.0.13
 - `geopandas` >=0.4.0

These additional packages may be necessary depending on your configuration:
 - `Rtree` >= 0.8.3
 - `affine` >= 2.2.1
 - `descartes`
 - `Pillow` >= 5.3.0
 - `pyproj` >= 1.9.5.1
 - `pytz` >= 2018.7

 And these for using an interactive notebook:
 - `IPython`
 - `jupyter`
 - `matplotlib`
 - `seaborn`

**Install from GitHub**

Download or clone the repository and install the required packages (preferably in a virtual environment):

```
git clone https://github.com/carderne/gridfinder.git
cd gridfinder
pip install -r requirements.txt
```
You can run ```make test``` in the directory, which will do an entire run through using the test data and confirm whether everything is set up properly.