# Introduction
Different cities in the world have perfect venues that you cannot live without. In this project we will help people who are living in central Odenplan, Stockholm to find a new home with similar features as Odenplan in Stockholm city. Despite of having dissimilarities of taste, we will look for city parts in Stockholm that looks like Odenplan. By clustering different neighborhood according to venue category may give insights on what defines the Norrmalm, the district of Odenplan. Furthermore, measure quaintly by venues that show how similar city parts are to Odenplan might serve as a variable that can help people to make a decision when they are trying to explore new residence in Stockholm.

# Problem
Identify neighborhoods in Stockholm city that gives a good perception of similar neighborhoods to Odenplan.

## Data gathering
The data on the most common Stockholm areas are scraped from Stockholm stads website. Using Google maps geocoder API we find the coordinates for each city part of interest, which we then use with Foursquare API to collect the closest venues (supermarket, restaurant, park, etc.).
