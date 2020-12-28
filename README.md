# Introduction
Different cities in the world have perfect venues that you cannot live without. In this project we will help people who are living in central Odenplan, Stockholm to find a new home with similar features as Odenplan in Stockholm city. Despite of having dissimilarities of taste, we will look for city parts in Stockholm that looks like Odenplan. By clustering different neighborhood according to venue category may give insights on what defines the Norrmalm, the district of Odenplan. Furthermore, measure quaintly by venues that show how similar city parts are to Odenplan might serve as a variable that can help people to make a decision when they are trying to explore new residence in Stockholm.

# Problem
Identify neighborhoods in Stockholm city that gives a good perception of similar neighborhoods to Odenplan.

## Data gathering
The data on the most common Stockholm areas are scraped from Stockholm stads website. Google maps geocoder API was used to obtain the latitude and longitude values for each city part of interest, which then could be used with Foursquare API to collect the closest venues (supermarket, restaurant, park, etc.). Foursquare API gives very rich information of venues, for instance we can see from the dataframe that each Venue Category seems pretty accurate. The venue Category for each city part was obtained One-Hot-encoded and grouped by city part. By taking the mean value on the the transformed dataframe a densification-factor was obtained per venue category. 

![alt text](https://github.com/Borg93/Battle_of_odenplan/blob/master/one_hot.png?raw=true)
> The table shows a density-factor for each venue category

After the data-preperation a K-means clustering was performed to cluster the city parts into areas data gives insights of Odenplan.

## Methodolgy
K-means is unsupervised cluster analysis which used to find groups from data which have not been explicitly labeled. The K-means algorithm tries cluster data by separating samples in n groups by the density features from the dataframe. The elbow method was used to determine the number of clusters for the data set. Basically, the “elbow” is when the gradient change from the distortion score (from different Ks) is small, i.e the line chart will resemble an elbow of an arm. 

![alt text](https://github.com/Borg93/Battle_of_odenplan/blob/master/elbow_m.png?raw=true)
> The graph shows that the optimal value for k = 3 

This gives a good indication of an inflection point on the curve which shows that the underlying model fits best at that point. Chart above shows that K=3 was optimal for this case which means that there will be 3 clusters in total.

A new dataframe is created to get an overview of the 10 most common venues at each city part

![alt text](https://github.com/Borg93/Battle_of_odenplan/blob/master/common_venue.png?raw=true)
> The table show common venues in different city parts

Folium maps is used to obtain a visual perception of how the different clusters look on a map of Stockholm, see map. The most notable is that central parts  of Stockholm, which has cluster label 1 (blue) are pretty accurate clustered with other central city parts.

![alt text](https://github.com/Borg93/Battle_of_odenplan/blob/master/map_battle.png?raw=true)
> The table show common venues in different city parts

There are various algorithms to help to evaluate the performance of the clustering algorithm and in this case was adjusted rand index used. Rand index computes a similarity measure between two clusters, in this case  all city parts are compared with Odenplan. Perfect similarity would give a score of 1 and bad labelling or independent labelling Is scored 0 or a negative score to -1.


![alt text](https://github.com/Borg93/Battle_of_odenplan/blob/master/common_parts.png?raw=true)
> The table adjusted rand index. 

 The results from table above show that city parts in the suburbs likely, e.g. Rinkeby, are very low scored and city parts that are very central, e.g Kungsholmen, are scored higher.

![alt text](https://github.com/Borg93/Battle_of_odenplan/blob/master/tabell_city.png?raw=true)
> The figure shows city parts that are simlair to Odenplan based on adjusted rang index.

# Concluding remarks
K-means is very simple clustering algorithm that necessary dosent converge to the most optimal result and there are many other different unsupervised clustering algorithms that probably would achieve better results. The project was performed with a selected data set of different popular city parts with 286 different features. However, have more data point of the city and different features could lead to totally different result, for instance price/m^2 would be really good feature to study.

The results from figure 2 are very promising and if you ask me who lives in Stockholm can say that the adjusted rand index is pretty accurate when it comes to similarity of city parts. 

