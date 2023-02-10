# Predicting RESIDENTIAL REAL ESTATE in Taipei,Taiwan with Cluster, Regression and Visualization

This is my self designed project to make prediction on the residential real estate price in Taipei Taiwan.  
The major techniques involved in the project including **PCA, K-means, Multivariate Regression, Human Mobility, Network Connectivity**, etc.
## Background

Taipei, similar to all the other compact cities in east Asian, holds a great amount of population and thus have an insane house price.  
Among the factors that affect the price of a house, besides its original properties, for exmaple the size, the layout and its condition, the environment around it is of vital importance.  
But how could we describe a house and its surroundings statistically?
**We decide to use POIs (Points Of Interest) to construct a model to predict the house price.**

## Dataset

To construct the model and compose a sound story, we have collected datasets from all aspects.

1. [The transaction data in Taipei in the past 3 years (2019-2022)](https://plvr.land.moi.gov.tw/DownloadOpenData)
2. [The POIs arround each transaction (details below)](https://mapsplatform.google.com/?utm_source=search&utm_medium=googleads&utm_campaign=brand_core_exa_desk_mobile_us&gclid=CjwKCAiAhKycBhAQEiwAgf19egUZrNFQEEPbm2ZlpGah4Hu9IFpB9-jpCCLATsPMplqB6V5XGlAChRoCv-EQAvD_BwE&gclsrc=aw.ds)
3. [District and Sub-district geographical information](https://data.gov.tw/dataset/7438)
4. [Population Distribution](https://ca.gov.taipei/News_Content.aspx?n=8693DC9620A1AABF&sms=D19E9582624D83CB&s=EE7D5719108F4026)
5. [Income distribution](https://data.gov.tw/en/datasets/103066)
6. [Education distribution](https://data.gov.tw/en/datasets/8409)
7. [Daytime/Nighttime population flow](https://segis.moi.gov.tw/)
8. [Age Distribution](https://www-ws.gov.taipei/Download.ashx?u=LzAwMS9VcGxvYWQvMzM1L3JlbGZpbGUvMTYxNTUvODM1MjYzNS8yNzkzNjQ0ZS0zMjU3LTRmZDUtOWQ1Mi0zYTVkM2E0MmEyNWIucGRm&n=MjAyMC1hZ2UucGRm&icon=.pdf)
9. etc.

### POI acquisition and selection

1. We are using Google Map API to acquire the data, there are mainly two APIs that we used.
   1. [Geocoding API](https://developers.google.com/maps/documentation/geocoding/overview)
   2. [Places API](https://developers.google.com/maps/documentation/geocoding/overview)
2. We first use the name of the transaction location to find the latitude and longitude. Use the coordinates to acqure its surrounding POIs.
3. We count POIs of different kind within different radius, we choose the buffer to be
   1. 500m: A walking distance
   2. 1000m: A public transportation distance/ A scooter distance
   3. 3000m: A private transportation distance
4. We choose a list of POI to count
   - Subway Station
   - Bus Station
   - Police Station
   - Hospital
   - Supermarket
   - Library
   - University
   - Primary School
   - Church
   - Nightclub
   - Shopping Mall
   - Park
5. **\*Cautious! Google API can be costful**

## Analysis

### Cluster

We are doing clusters with following combinations

1. 500m POI
2. 1000m POI
3. 3000m POI
4. 1,2,3 + Unit Price of Transaction ($NTD/m^2$)
5. House Properties
6. House Properties + Unit Price of Transaction ($NTD/m^2$)

### Linear Regression

We are conducting linear regression with following combinations

1. All POIs v.s. Unit Price
2. 500m POI v.s. Unit Price
3. 1000m POI v.s. Unit Price
4. 3000m POI v.s. Unit Price
5. House Peroperties v.s. Unit Price

### Socioeconomic Factors

We are considering the following factors in affecting house price

1. Education distribution of different level in different sub-district in Taipei
2. Income distribution of ttl/avg/median income in different sub-district in Taipei
3. Population in each district in daytime and nighttime in weekday/weekend in Taipei

## Repo Structure

Below is the repository tree of the project

- README.md
- Final\_DataClean\_Regression.ipynb
  > This is main code of Data Clearance, PCA, Human Mobility, Network Connectivity and Multivariate Regression.
- Final\_Cluster\_Visualization.ipynb
  > This is the main code from K-means Clustering, Map Visualization.
- socioSHAPES.zip
  > This is the ArcGIS project for network connectivity and other geographical analysis.
- LICENSE
- Output\_CSV/
  > This folder contains the numeric outputs in the form of CSV.
- Raw\_data/
  > This folder contains the raw data used in the project.
  - 01Transaction/
    > This is the folder of transaction raw data
  - 02POI/
    > This is the folder of POIs we have queried from Google API and their processed versions
  - 03Census/
    > This is the folder of Census data: education, income, population flow data.
  - 04Geographic_data/
    > This is the folder of shapefile of Taiwan districts and sub-districts.
- Figures/
  > This folder contains figures generated from the code.
- Report/
  > This folder contains both the presentation slides and the final report.

## Results
Refer to the folder [Report](https://github.com/Eric-Miao/2022Fall-CIVENG263N-FinalProj/tree/main/Report)
