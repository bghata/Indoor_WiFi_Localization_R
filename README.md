# Indoor_WiFi_Localization_R

## Data Overview:

Detecting outdoor localization can done simply and accurately by the use of GPS while using mobile devices. However, indoor localization is still an open problem mainly due to the loss of GPS signal in indoor environments. This database is focused on WLAN fingerprint-based ones or Wi-Fi Fingerprinting.  
The database is collected in 2013 from UJI - Institute of New Imaging Technologies, Universitat Jaume Castellón, Spain, which covers three buildings and 5 floors. 
It can be used for classification (BUILIDINGID, FLOOR) or regression (LONGITUDE, LATITUDE). 
This dataset consists of 19937 training data which is the original database to work on, and 1111 validation data which is the test data to predict on.   There are 529 attributes contain the Wi-Fi fingerprint, the coordinates where it was taken, and other useful information.  
Each Wi-Fi fingerprint can be characterized by the detected Wireless Access Points (WAPs) and the corresponding Received Signal Strength Intensity (RSSI).
The range of intensity signal is between -104 dBm (extremely poor signal) to 0 dBm.
Positive value 100 used if WAPs intensity signal was not detected.

Wi-Fi fingerprints are collected from the following 529 attributes:
-	520 WAPs noted as (WAP001 – WAP520)
-	3 buildings noted as (0, 1, 2)
-	5 floors noted as (0, 1, 2, 3, 4)
-	The coordinates (Longitude, Latitude)


## Data pre-processing:

The data requires pre-processing and cleaning to be ready for analysis. The pre-processing was divided in the following steps:

1-	Removing total NA’s from the WAPs’ columns & rows from the training data only, since they are noise and do not lead to accuracy in the analysis process.
2-	Replacing the frequency of WAPs from NA’s to -110 which is a frequency outside the range of the original data so it will not affect the results. This was applied on both training and validation data sets.

3-	Isolate the outliers by replacing the high frequency of WAPs (0 to -40) to -50, since those outliers will skew the data and affect negatively the predictions. This was applied on the training data set only.
4-	Setting the right data type, BUILIDINGID, FLOOR as numeric, and LONGITUDE, LATITUDE as factor. This was applied both training and validation data sets.
5-	Creating 4 separate datasets from the training dataset, and each one of them has only WAPs a one of the following attributes (BUILIDINGID, FLOOR, LONGITUDE, LATITUDE). The purpose of this division is to have a higher accuracy since other attributes will not affect the analysis and when applying the models.


## Models & Algorithms Tested:

3 models with 3 different algorithms were used in order to train and test the data to reach the prediction.
These models are K-NN (K-Nearest-Neighbours), Random Forest, and Gradient Boosting Trees.

The process started by dividing the training dataset into trainSet (to apply the model on) which is 75% of the training data, and testSet (to test the model on) which is 25% of the training data. 
The next step is to apply the model on the validation data and record and compare the results of each model as following:
-	Noting accuracy of BUILIDNGID & FLOOR due to classification data.  
- Noting R-Squared & MAE (Mean Absolute Error) of LONGITUDE & LATITUDE due to regression data.
