# ERA5-Land Data Analysis + Model Building PyTorch
<p>
<img src="https://forthebadge.com/images/badges/built-with-love.svg"> <img src="https://forthebadge.com/images/badges/made-with-python.svg"> <img src="https://forthebadge.com/images/badges/open-source.svg"> <img src="https://forthebadge.com/images/badges/made-with-reason.svg">
</p>


### [About the Dataset](https://docs.google.com/document/d/1j7zf1bNZME1LftExzLvPwTqQGqSg4t837e2GF1_dpmo/edit?usp=sharing)
The Copernicus Data Store (CDS) is a one stop shop for a wide range of historical and real time geospatial data from various remote sensing and on-the-ground weather observations. The CDS API allows for programmatic access to this data store. This API is used to obtain the following data from the [ERA5-Land Hourly Reanalysis Dataset](https://cds.climate.copernicus.eu/cdsapp#!/dataset/reanalysis-era5-land?tab=overview). The section in square brackets refers to the specifics of the download - 
1. Temperature of air at 2m above the surface - [2m Temperature - 2019 - December - First 7 days - 12:00 - Whole Available Region - NetCDF]
2. Total precipitation - [Total Precipitation - 2019 - December - First 7 days -12:00 - Whole Available Region - NetCDF]
3. Volumetric soil water layer 1 - [Volumetric soil water layer 1 - 2019 - December - First 7 days - 12:00 - Whole Available Region - NetCDF]

I have taken only a pice of the ERA5-Land Hourly Reanalysis Dataset which includes *Temperature of air at 2m above the surface*, *Total precipitation*, *Volumetric soil water layer 1* features and only 12:00, 7days of December,2019 as the whole dataset is quite huge to work with.
### Exploring and Visualising Geospatial Data:
In this section, I have performed Exploratory Data Analysis and Visualisation of the datasets. Calculated the basic statistics (mean, median, standard dev., variance, range, spatial resolution etc) for each of the datasets and included some comments about the conclusions I drew from these features. Also check for missing data points, NaN values etc and commented on how I would go about handling these. Ploted a randomly chosen day from each of the datasets and use a sequential colormap for the plot. Visualised the distribution of the datasets using `matplotlib hist()` and commented on what I observed.
### NULL Data points of each features:
<pre>
<img src="https://i.ibb.co/T4KZRF3/download-1.png" width="400"> <img src="https://i.ibb.co/qD0wvzW/download-2.png" width="400"> <img src="https://i.ibb.co/Pz104fy/download-3.png" width="400"> 
</pre>
### More visualizations from the notebook:
<pre>
<img src="https://i.ibb.co/ZSGLkKf/download-4.png" width="500"> <img src="https://i.ibb.co/BzxZdYr/download-6.png" width="500"> <img src="https://i.ibb.co/fxmDPYD/download-7.png" width="500"> <img src="https://i.ibb.co/VVNPqTM/download-8.png" width="500"> <img src="https://i.ibb.co/tCFBJyd/download-9.png" width="500"> <img src="https://i.ibb.co/ZR9N0v7/download-10.png" width="500">
</pre>

PS: I have also added comments/conclusions after each visualizations. 
### Deep Learning:
I haved used neural network to predict the [Total Precipitation] from the two input variables [Temperature of air at 2m above the surface, Volumetric soil water layer 1]. The Deep Learning framework of choice is PyTorch.

#### Model Architecture:
```
LinearRegression (
  (linear1): Linear(in_features=4, out_features=40, bias=True), weights=((40, 4), (40,)), parameters=200
  (tanh1): Tanh(), weights=(), parameters=0
  (linear2): Linear(in_features=40, out_features=20, bias=True), weights=((20, 40), (20,)), parameters=820
  (tanh2): Tanh(), weights=(), parameters=0
  (linear3): Linear(in_features=20, out_features=10, bias=True), weights=((10, 20), (10,)), parameters=210
  (tanh3): Tanh(), weights=(), parameters=0
  (linear4): Linear(in_features=10, out_features=1, bias=True), weights=((1, 10), (1,)), parameters=11
)
```
