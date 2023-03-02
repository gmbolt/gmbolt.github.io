+++
title = "PhD project"
date = Date(2023, 3, 2)
+++

# Statistical Analysis of Multiple Interaction Network Data (PhD)

This project was a collaboration between ~~~<a href="https://www.lancaster.ac.uk/stor-i/" target="_blank">STOR-i</a>~~~, the Centre for Doctoral Training (CDT) at Lancaster University where I did my PhD, and ~~~<a href="https://www.elsevier.com/en-gb" target="_blank">Elsevier</a>~~~, an academic publishing company. Elsevier provide various online services and tools for researchers, such as ~~~<a href="https://www.mendeley.com/" target="_blank">Mendeley</a>~~~ and ~~~<a href="https://www.sciencedirect.com/" target="_blank">ScienceDirect</a>~~~, and were interested in the problem of **user segmentation** - understanding who their users are and how they interact with their platforms. Our goal was to develop novel methodologies to assist with this task.

Of particular interest at the time was analysis of **clickstream data** (Fig. 1), which contains information regarding visits of users to Elseiver webpages. The data has two key properties which we decided to leverage. Namely, it is both **intermittent** and **bursty**, with cascades of clicks in quick succession followed by periods of inactivity. As we will show, this provided a means to interpret this as **network data**. 

\figenv{
    /assets/phd-diagrams/clickstream_data.png
}{
    Figure 1: Toy example clickstream data for a single user. These data are intermittent and bursty, with cascades of clicks close in time (e.g. first to second) followed by periods of inactivity (e.g. second to third).
}{
    width: 100%
}


## Users as interaction networks 

In the most general sense, network data consists of relational information amongst a collection of entities. A ubiquitous example is social network data, encoding the friendships (relations) amongst a sample of individuals (entities). The increasing prevalence of data in this form has driven a burgeoning interest in methodologies suitable to their analysis, developing into a sub-field of statistics referred as "statistical network analysis" - see for example the review by Salter-Townsend et al. (2012),[^salter] or the book of Kolaczyk and Csárdi (2014).[^kolaczyk]

How does this relate to clickstreams? Well, by using the intermittent and bursty property of these data, we are able to partition a single user's data into a sequence of paths over webpages (Fig. 2). This represents an instance of a so-called **interaction network**, where one observes interactions amongst entities over time (here entities=webpages and interactions=paths). This differs subtly from the case where relations amongst entities are observed explicitly, such as in traditional social network data, and has led to recent work in the literature on new models.[^crane][^cai]

\figenv{
    /assets/phd-diagrams/interaction_network.png
}{
    Figure 2: Clickstream data as an interaction network.
}{
    width: 100%
}


This, however, is not the complete picture. There is not data on just one user but many, leading to a sample of interaction networks (Fig. 3). Data of this form, where we observe **samples of networks**, is appearing ever more frequently. This is being driven heavily by data collection advancements in fields such as neuroscience, where fMRI brain scan data are being converted to networks summarising brain connectivity. Relative to the case where a single network is observed, this raises new questions for a data analyst. For example, one might wonder what is the "average" network? Or how variable are the networks about this average? This has motivated a string of recent work in the literature on methods capable of providing answers to such questions.[^luna][^durante]


\figenv{
    /assets/phd-diagrams/multiple_interaction_networks.png
}{
    Figure 3: Sample of users => sample of interaction networks.
}{
    width: 100%
}


Herein lies the research problem I looked to solve in my PhD: analysing samples of interaction networks. To the best of our knowledge, this had not be touched upon in the literature. As it transpired, I ended-up focussing on two main problems
1. Measuring the dissimilarity of two interaction networks;
2. Modelling a sample of interaction networks;

details of which can be found below. 

## Comparing interaction networks 

In this part of the project, we looked into ways one could go about defining **distance measures** between interaction networks, serving as a proxy for a distance between Elsevier users (Fig. 4). Given any sample of data points (could be interaction networks, or more familiar vector representations) if you have some way to measure their dissimilarity this immediately opens you up to a variety of analytical methods. This includes dimension reduction methods like [multidimensional scaling](https://en.wikipedia.org/wiki/Multidimensional_scaling) (MDS), which can aide visualisation, clustering algorithms such as [DBSCAN](https://en.wikipedia.org/wiki/DBSCAN), which can be used to group data points, or classification and regression via [k-nearest neighbors](https://en.wikipedia.org/wiki/K-nearest_neighbors_algorithm). Inline with the research motivation, of most interest for us and Elsevier were clustering algorithms, which would provide a means to **group users** based upon their clickstreams.

\figenv{
    /assets/phd-diagrams/distances.png
}{
    Figure 4: Comparing users reduces to comparing interaction networks.
}{
    width: 100%
}

This work culminated in a survey paper which you can view ~~~<a href="https://arxiv.org/abs/2206.08858" target="_blank">here</a>~~~, wherein we reviewed various distances and illustrated their applicability via an example data analysis. In particular, we did an analysis of the in-play football data released by StatsBomb ([see here](https://github.com/statsbomb/open-data)), and a dataset on user interactions with the location-based social network Foursquare released by Yang et al. (2015)[^yang] ([see here](https://sites.google.com/site/yangdingqi/home/foursquare-dataset)).


## Modelling a sample of interaction networks


\figenv{
    /assets/phd-diagrams/modelling.png
}{
    Figure 5: Modelling a sample of interaciton networks. Our model can be seen as a Gaussian-like distribution over the space of interaction networks, being controlled via location and scale parameters. The location parameter then provides a "network average", summarising the common theme among the sample.
}{
    width: 100%
}

When faced with a sample of interaction networks - perhaps a group of users inferred by a clustering algorithm - an immediate question is one of **summarisation**: what does this group represent? In this second part of the project, we considered answering this question via a **Bayesian modelling** approach; eliciting a model for these data via location and scale parameters, akin to a Gaussian distribution. Via a speciliased [Markov chain Monte Carlo](https://en.wikipedia.org/wiki/Markov_chain_Monte_Carlo ) (MCMC) algorithm, we were able to infer these model parameters given a sample of data, providing summary measures for the sample. Most notably, one of these parameters served as the network-equivalent of the mode (Fig. 5), providing a notion of average for this non-standard data structure. 

We drew this work together into a paper which you can view ~~~<a href="https://arxiv.org/abs/2206.09995" target="_blank">here</a>~~~, wherein we conduced simulation studies confirming the efficacy of our methodology and MCMC inference scheme, and conducted an example data analysis of the Foursquare data of Yang et al. (2015).[^yang]

# References 

[^salter]: Salter-Townshend, M., White, A., Gollini, I., & Murphy, T. B. (2012). Review of statistical network analysis: models, algorithms, and software. *Statistical Analysis and Data Mining*, 5(4), 243-264. 
[^kolaczyk]: Kolaczyk, E. D., & Csárdi, G. (2014). Statistical analysis of network data with R (Vol. 65). *New York: Springer.*
[^yang]: Dingqi Yang, Daqing Zhang, Bingqing Qu. Participatory Cultural Mapping Based on Collective Behavior Data in Location Based Social Networks. *ACM Trans. on Intelligent Systems and Technology (TIST)*, 2015
[^cai]: Cai, D., Campbell, T., & Broderick, T. (2016). Edge-exchangeable graphs and sparsity. *Advances in Neural Information Processing Systems*, 29.
[^crane]: Crane, H., & Dempsey, W. (2018). Edge exchangeable models for interaction networks. *Journal of the American Statistical Association*, 113(523), 1311-1326.
[^luna]: Lunagómez, S., Olhede, S. C., & Wolfe, P. J. (2021). Modeling network populations via graph distances. *Journal of the American Statistical Association*, 116(536), 2023-2040.
[^durante]: Durante, D., Dunson, D. B., & Vogelstein, J. T. (2017). Nonparametric Bayes modeling of populations of networks. *Journal of the American Statistical Association*, 112(520), 1516-1530.
