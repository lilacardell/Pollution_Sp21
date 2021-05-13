This repository is for a project for ACE 592: Data Science. The title is "Using Air Pollution to Predict Economic Activity" and a draft is listed above.

Contributors: Lila Cardell, Manny Kim, Frederick Nyanzu, Pablo Ordoñez, Gowthami Venkateswaran

Project Summary:
The use of different measures of economic activity is important for both policy makers and researchers. However, the availability of these data at a subnational level in developing countries is uncommon, and when available, they come with significant problems in terms of quality (Johnson et al 2009). To address this, Henderson et al. (2012) use night lights to predict income growth, and show that it is a useful proxy. In this paper, we aim to build upon this work, by using air pollution, in addition to night lights, to predict economic activity at a subnational level.

Data Sources:
We use data for the years 2009 and 2014 in this project. All datasets used are publicly available at the following links

1) Air Pollution (Particulate Matter PM 2.5):

https://sedac.ciesin.columbia.edu/data/set/sdei-global-annual-gwr-pm2-5-modis-misr-seawifs-aod/data-download
_________________

2) Night lights (Harmonized)

https://figshare.com/articles/dataset/Harmonization_of_DMSP_and_VIIRS_nighttime_light_data_from_1992-2018_at_the_global_scale/9828827/2
__________________

3) Monthly Maximum Temperature

http://data.chc.ucsb.edu/products/CHIRTSdaily/v1.0/global_tifs_p05/Tmax/
__________________

4) Monthly Precipitation

http://data.chc.ucsb.edu/products/CHIRP/monthly/
__________________

5) Mexico Population Census

https://www.inegi.org.mx/temas/pibti/

__________________


We use Python to conduct our analysis along with geo-spatial packages such as rasterio, rasterstats and geopandas to clean and analyze remotely sensed data. 

There are two python notebooks.
1) Data_Cleaning.ipynb

This program performs the following tasks:
* Loads necessary packages
* Reads in shapefiles of Mexico
* Reads in Nightlight, Air Pollution, Temperature and Precipitation GeoTIFF files as raster objects
* Calculates zonal statistics such as minimum, maximum, mean and standard deviation of all above mentioned raster objects at the municipality level. 
* Combines all data into a long format panel to be used for analysis


2) Data_Analysis.ipynb

This program takes as inputs the panel dataset created from the first notebook and the Mexico shapefiles. The tasks conducted in this notebook includes:
* Loads sklearn toolkits to conduct machine learning analysis
* Imports clean data (created in Data_Cleaning.ipynb)
* Normalizes the data to prepare for analysis
* Splits sample into training and testing sets
* Runs OLS, Lasso and Random Forest prediction exercises
* Produces results - Root Mean Square Error(RMSE) and r-squared for all models
* Produces results - maps of ground truth vs predicted per capita income for the best model