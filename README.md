# Google_Analytics_Customer_Revenue_Prediction
Predict how much GStore customers will spend

## Data Fields in dataset

- **fullVisitorId**- A unique identifier for each user of the Google Merchandise Store.
- **channelGrouping** - The channel via which the user came to the Store.
- **date** - The date on which the user visited the Store.
- **device** - The specifications for the device used to access the Store.
- **geoNetwork** - This section contains information about the geography of the user.
- **sessionId** - A unique identifier for this visit to the store.
- **socialEngagementType** - Engagement type, either "Socially Engaged" or "Not Socially Engaged".
- **totals** - This section contains aggregate values across the session.
- **trafficSource** - This section contains information about the Traffic Source from which the session originated.
- **visitId** - An identifier for this session. This is part of the value usually stored as the _utmb cookie. This is only unique to the user. For a completely unique ID, you should use a combination of fullVisitorId and visitId.
- **visitNumber** - The session number for this user. If this is the first session, then this is set to 1.
- **visitStartTime** - The timestamp (expressed as POSIX time).
- **hits** - This row and nested fields are populated for any and all types of hits. Provides a record of all page visits. (new in version 2 data set)
- **customDimensions** - This section contains any user-level or session-level custom dimensions that are set for a session. This is a repeated field and has an entry for each dimension that is set. (new in version 2 data set)

## Exploratory Data Analysis (EDA)

At first, I explore data, clean data, and study relations between features and target values as shown in [Data_Clean_Explore.ipynb](https://github.com/hsuanhao/Google_Analytics_Customer_Revenue_Prediction/blob/master/Data_Clean_Explore.ipynb). In the end, I prepared the data for model training.

## Model Construction and Evaluation

As shown in [Model_Train.ipynb](https://github.com/hsuanhao/Google_Analytics_Customer_Revenue_Prediction/blob/master/Model_Train.ipynb), I constructed training model in two steps. First, I created a classifier to classify whether customers will buy products or not per visit in GStore. In this stage, I implemented **Random Forest** for this classification. For those who won't purcase products in store, the transaction revenue is 0 for sure. Hence, the first step is to classify customers whether purchase or not per visit. Then for those who purchase products, I will use **statistical models** or **RNN** for **time series** to predict the transaction revenue per visit. Note that I have examined that the transaction revenue per visit only depends on date.

PS. I'm still figuring out how to deal with time series via statistical models and RNN.


<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a><br />This work by <span xmlns:cc="http://creativecommons.org/ns#" property="cc:attributionName">Hsuan-Hao Fan</span> is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a>.
