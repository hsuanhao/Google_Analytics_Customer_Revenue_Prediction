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

## Data Exploration, Clean, and Feature Engineering

At first, I explore data, clean data, and study relations between features and target values as shown in [Data_Clean_Explore.ipynb](https://github.com/hsuanhao/Google_Analytics_Customer_Revenue_Prediction/blob/master/Data_Clean_Explore.ipynb). I found that most of features have weak relations with target values, `transactionRevenue`, except for `date`. But those features, like `hits`, `pageviews`, `isMobile`, `weekend`, `Referral`, `Americas`, and `US`, have relations to whether customers will purchase products or not in GStore when they visited the store. Note that `hits` and `pageviews` are stored in json format in `total` attribute, `isMobile` is stored in json format in `device`. Since customers visited the store via `Referral` channel in `channelGrouping` have higher purchasing rate, I generated this feature to denote whether or not customers visits store vial Referral channel. Besides, customers from `Americas` continent and `US` country have higher purchasing rate. Therefore, I built a model to classify whether customers will buy products or not first. For those who won't buy products, the transaction revenue must be zero. Then I built a model for time series data to predict the transaction revenues who will buy products in store since transaction revenue is related to date.
