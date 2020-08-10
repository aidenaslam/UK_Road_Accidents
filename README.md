# Analysis of UK Road Accidents 2005-2015

The aim of this project is to analyse road accidents that have occurred in the UK in the period between 2005-2015 to help the government improve road safety. The collected data
was obtained from the UK government website [1] which includes incidences that are reported to the police and recorded using the STATS19 accident reporting form. The dataset consists of 32 attributes and 1.78 million rows and the analysis was performed using R. This project utilised recurrent neural networks (RNN) and k-means clustering to predict the number of road accidents and help identify the areas of improvement needed in road safety in the UK.

## Exploratory Data Analysis (EDA)
* The overall number of accidents has reduced from 2005-2015 however, the number of serious or fatal accidents has plateaued  over the last few years. 
<img src="https://github.com/aidenaslam/UK_Road_Accidents/blob/master/Figure2.png" width="500" height="200" />

* A temporal analysis of the number of accidents indicates that the number of accidents is fairly even throughout the year, but slightly higher during November, December and January. Would it be possible to accurately predict the number of road accidents to help the government with accident resource and planning?
<img src="https://github.com/aidenaslam/UK_Road_Accidents/blob/master/Heatmap1.png" width="500" height="200" />

* The age distribution of the number of accidents illustrates that the number of accidents decreases with age. Are younger drivers responsible for most accidents? If so, how can the government find ways to reduce this?
<img src="https://github.com/aidenaslam/UK_Road_Accidents/blob/master/AgePlot.png" width="500" height="200" />

## Data Preparation
* To implement the recurrent neural network, the decomposition of the time series was carried out to identify trend and seasonality. The sliding window method was implemented to de-trend and scale the data between 0 and 1. The data was split using the holdout method with a ratio of 70:30 for the training and testing dataset respectively. 
<img src="https://github.com/aidenaslam/UK_Road_Accidents/blob/master/Capture.PNG" width="500" height="250" />

* Due to limited computing resources, the dataset for the clustering analysis was filtered for severe or fatal accidents in London. The dataset was prepared by scaling the numerical features using normalisation and implementing one-hot-encoding for the categorical features. To reduce dimensionality, Pearson's correlation coefficient was used to remove  features with correlation greater than 0.9.

## Modelling Results
* The basline model for the RNN was a multi-layer perceptron with 2 hidden layers which produced an RMSE of 40.55, MAE of 31.34 and R<sup>2</sup> of 66.95%. Using trial and error, an RNN consisting of 25 hidden dimensions produced the best results, with an RMSE of 40.73, MAE of 31.06 and R<sup>2</sup> of 62.99%. Therefore, the basline model performed better.
<img src="https://github.com/aidenaslam/UK_Road_Accidents/blob/master/Figure14.png" width="500" height="250" />
<img src="https://github.com/aidenaslam/UK_Road_Accidents/blob/master/Figure15.png" width="500" height="250" />

* The elbow method indicated that the optimal number of clusters was 3 and principal component analysis was used to plot the clusters.
<img src="https://github.com/aidenaslam/UK_Road_Accidents/blob/master/Figure12.png" width="500" height="250" />

* An analysis of cluster 1, showed that the drivers within the cluster were mostly under 30 and one of the main sources of accidents was driving at night time. 
<img src="https://github.com/aidenaslam/UK_Road_Accidents/blob/master/Figure18.png" width="500" height="250" />
<img src="https://github.com/aidenaslam/UK_Road_Accidents/blob/master/Figure19.png" width="500" height="250" />


## Conclusions
* The multi-layer perceptron was able to predict road accidents better than the RNN - outlining the weakness of RNN to recall long-term patterns

* The k-means clustering showed that additional night-time training for younger drivers can be a potential way for the UK government to reduce the number of accidents. This was also highlighted in the 2019 road safety report published by the department of transport.

## Limitations and Future Work
* Given the large dataset, only a few hypotheses were considered for the project. Future work would involve using optimisation techniques to produce a better model to predict the number of accidents. Multiple models specific to localised regions would also assist with local governments to help allocate resources needed for accidents.

* The clustering analysis was only for London and in the future, this can be expanded for areas across the nation.

## References
[1] https://data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-safety-data
