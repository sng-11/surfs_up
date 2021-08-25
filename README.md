# Surfs Up Challenge

## Overview of Analysis
Our client, W.Avy, is interested in amassing weather data in Oahu before deciding to set up a surf shop there. To help him, we use Python, Pandas, and SQLAlchemy to retrieve temperature data for the months of June and December and generate summary statistics.

## Results
_June Weather Summary Statistics_

<img width="173" alt="Screen Shot 2021-08-25 at 4 29 09 PM" src="https://user-images.githubusercontent.com/84816495/130860187-5e31f5de-3e4b-4699-a1fa-5b70f4cf4fe5.png">

_December Weather Summary Statistics_

<img width="207" alt="Screen Shot 2021-08-25 at 4 29 17 PM" src="https://user-images.githubusercontent.com/84816495/130860234-81702dfd-300d-4928-802d-5e13e6977d2f.png">

As shown from the above tables:
1. The mean temperatures between June and December are different but not significantly. June mean temperature is 74.94 degrees while December mean temperature is 71.04 degrees. Since both indicate an average within the 70s, good surfing temperature, it seems like Oahu is a decent location to set up a surf shop.
2. The max temperatures in both June and December are fairly similar, with 85.0 and 83.0 respectively. This indicates that when the temperature does get hot, the most uncomfortable will be the mid 80s. Surfing can still be possible in this weather, albeit maybe requiring thinner surfing setsuits.
3. The min temperatures in both June and December vary, with 64.0 and 56.0 respectively. While it is still comfortable enough to surf at June's coldest, it is quite cold at December's coldest. However, if the 50s are rare and occurring mainly in the winter months, then Oahu is still a good choice for a surf shop for the majority of the year.

## Summary

As summarized in the above bullet points, Oahu seems like a decent location for a surf shop based on temperature data. The mean temperature stays fairly consistent even when comparing June and December. However, just relying on temperature data for 2 months is not enough. I would suggest the queries for the weather data of the month of July and August to be investigated also to further decide whether Oahu is a smart investment decision for a surf shop. These two months are chosen because the summer months are going to be where consumer traffic will be at its peak, with summer vacation and weather.

_What is the precipitation like in the month of July?_

<img width="168" alt="Screen Shot 2021-08-25 at 5 50 50 PM" src="https://user-images.githubusercontent.com/84816495/130869302-fd55fc84-a664-4901-b4aa-5e4b6a6e0d8d.png">

The following code was used to get the results:
```
julpre = []
julpre = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 7).all()
jul_df = pd.DataFrame(julpre, columns=['date','July Precipitation'])
jul_df.describe()
```

_What is the precipitation like in the month of August?_

<img width="180" alt="Screen Shot 2021-08-25 at 5 51 01 PM" src="https://user-images.githubusercontent.com/84816495/130869323-25501145-bdab-4a00-9b1f-5395c1dfbb97.png">

The following code was used to get the results:
```
augpre = []
augpre = session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 8).all()
aug_df = pd.DataFrame(augpre, columns=['date','August Precipitation'])
aug_df.describe()
```
