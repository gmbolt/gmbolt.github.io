+++
title = "PhD"
hascode = false
date = Date(2022, 2, 19)
rss = "Phd project."
+++
@def tags = ["syntax", "code"]

# Statistical Analysis of Multiple Interaction Network Data (PhD)

* Intro as colab with Elsevier who want to improve platforms for users
* Research aims/goals - new methods which can be applied to 
    * Analyse clickstream data 
    * Group users 
    * Summarise/interpret groups 
* We took a network-analytic approach to this problem by viewing user data as series of "network interactions" 


## Users as interaction networks 

* Describe a users data 
* Introduce network data 
* Contrast with *interaction* network data 
* Multiple observations - mirrors recent developments in literature

## Distances between users 

* Becomes distance between interaction networks 
* Distances between networks has been considered before but only for graph representations, not respecting interactions as observations 
* Drew on inspiration from various other research areas, e.g. time series, sequence analysis, optimal transport 
* Culminated in a paper 
* Use cases: embedding users for visualisation, grouping users, prediction via Knn 

## Finding the average user  

* Here we want to take a group of users and summarise them 
* Our approach was to seek a representative network which one could see as an "average user"
* We proposed a Bayesian model which effectively looks like a Gaussian distribution over the space of networks
* Key to setting-up our model is having a notion of distance between networks, where we leant on our previous work 
