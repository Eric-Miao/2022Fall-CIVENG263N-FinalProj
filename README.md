# CIVENG263N_Projects
 This is the final project for Berkeley course CIVENG 263N in Fall 2022

## Progress

### Data Collection
1. Decide the target city.  
   - **Taipei**
2. Fetech the real-estate data.   
   - **Thanks to the government, they published the data**
   - 41,000 entries

### Data Preprocessing
1. Google Map API to query for the geocoding information based on the text address of each real-estate.
2. Google Map API to query for surrounding POI infos (13 types of POI)
   - Only got 4000 entries' POI info because the Google API is not affordable for our course project.
   - Tend to OpenStreetMap for more info, overpass API.

### Regression Model
1. Use the POI data and real-estate properties to predict on housing price.

### Radiation Model on sub-district flows
1. Use the population (flows if possible, more directly to generate) and the radiation model to 
generate the flows between each sub-district in Taipei.
2. With the flow data, we can come up with a model to describe the importance (weight) of a certain 
area, and corelate that to the housing price.
   - Can be that the more connected/centered the area, the higher the price.

### Community detection
1. Based on the flow data, or more directly the connections of bus_stations/subway_stations and the data
we can regenerate the airport project.

## Results

## Report