# dateio-challenge

We believe that detailed transaction data has potential to be used for marketing purposes by banks directly 
or that insights from data could be further streamlined to other businesses.

As a proof of concept, we provide a model predicting whether a client might be interested in getting an insurance, 
based on comparing their spending pattern to patterns of clients that already do pay for insurance.

## Team
Our teammembers are: Lenka Obergriesová, Honza Maršálek, Michal Maršálek

## App
Our idea is various prediction models would run on bank's server, perhaps in a CRON way. Clients identified as belonging to a certain class
(of people that might be interested in a certain financial or other product) are then presented with an offer, for example in their online banking
service - after they log-in.
We believe models for predicting relevant clients for the following products could be developed based on the enriched transactional data:
* Insurance, possibly further distinguished as
    * Travel insurance
    * Car insurance
    * Life insurance
    * Pet insurance
    * Private (extra) medical or dental insurance
    * ...
* Freetime products areas (for B2B):
    * Sport equipment
    * Entertainment
    * Fashion / beauty / health
    * ...

In adddition to these positive recommendations, models could also provide a negative feedback. For example, clients withdrawing most of their
funds are likely not a target group for financial products.
Clients spending a lot on public transport are likely not a target group for car industry related  products etc.


## Model

In the provided dataset we noticed that there were 8% of people that payed insurance by card. We wanted to identify other potential insurance 
clients, based on their spending behaviour.

Our example model focuses on relationships between spending patterns of clients and the fact that they payed for insurance.
Due to high imbalance in classes 0 = doesn't pay for an insurance, 1 = does pay, models generally tend to predict zeroes rather than ones.
That goes against the idea that we would prefer offering
the product to clients that don't end up getting it rather than missing potential clients.

Our model is a simple Random forest classifier.
Random forest is an ensemble method where randomisation is used to mitigate overfitting. It relies on building many independant Classification 
trees and then
consulting their predictions (majority).
A classification tree works by recursively identifying a linear, single variable inequivality that 
best splits the exogenic variables space into two parts. This is done in a greedy fashion.
In addiition to the prediction ability, by consulting the conditions near the root of the tree, one can get an insight as to what
variables and their corresponding values are the most important.

Random forest framework was used due to the limited time, in practice additional statistical and machine learning models could be considered.

Our model for tipping off potential insurance clients features a 16% false negative rate (and 8% false positive). That means that we will
reach 84 % of prospective clients and we will offer the product to 8% of clients who have no interest in purchasing the product.
