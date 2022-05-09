# Surfs Up

## Overview

The purpose of this project is to analyze the weather in a certain location in Hawaii. This analysis will help us determine if opening a store is possible since weather is a large determinant to the success and operation of the store. We performed queries on the SQLite database that holds the weather data.

## Results
- As seen in the June temperature results, the average temperature in June is 75 degrees Fahrenheit with the lowest temperature recorded at 64 and highest at 85. These temperatures would allow for a good day in the ocean.
![June Temp](/June_temp.png)

- The December results show an average temperature of 71 degrees Fahrenheit. While this temperature will allow for a good day at the beach, the lowest recorded temperature is 56 degrees Fahrenheit. This may discourage business as it may be too cold. However, since the average is normal 71 degrees Fahrenheit, December would still generate good business but with possibly slower days than in June. 

- The average temperatures in both months are fairly close and even the highest recorded temperature in each month is similar. The weather stays consistent year round, as the results suggest.

## Summary

The June results suggest that the temperatures would be ideal for people to enjoy the beach and a cold treat. The December results also show an average temperature that would encourage business as well. There may be some cold days as noted by the lowest recorded temperature in December but since the average is usually 71 degrees Fahrenheit and some days can be as hot as 83 degrees Fahrenheit, the store would still operate successfully. In general, these results would suggest that opening a store in this location year round is possible since the weather does not change drastically from the summer season to the winter season. A store opening in this location will likely not have to close due to weather conditions.

### Additional Queries
I would perform queries to understand the precipitation for those two months. This additional data would give a fuller picture of the weather in these months since temperature as well as rain can affect the store. 

#### Query for June Precipitation
```
june_prcp = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 6).all()
june_prcp_list = list(june_prcp)

juneprcp_df = pd.DataFrame(june_prcp_list, columns=['date','precipitation'])
juneprcp_df.set_index(juneprcp_df['date'], inplace=True)
juneprcp_df = juneprcp_df.sort_index()

juneprcp_df.describe()
```

#### Query for December Precipitation
```
dec_prcp = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 12).all()
dec_prcp_list = list(dec_prcp)

decprcp_df = pd.DataFrame(dec_prcp_list, columns=['date','precipitation'])
decprcp_df.set_index(decprcp_df['date'], inplace=True)
decprcp_df = decprcp_df.sort_index()

decprcp_df.describe()
```
