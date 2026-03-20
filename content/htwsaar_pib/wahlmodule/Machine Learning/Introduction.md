
2 Types of methods : supervised methods vs non supervised methods 
Problems that require data : supervised problems 


Regression example : 
predict reasonable price for a used car 
predict price for real estate in the city 


meaning what we want to predict is continous 


Classification : 
discreet, only so many values we could choose 
- news paper article :  predict what topic it is, news, sports, 
- determine disease : either a patient has covid, or they dont 

it is possible to *cast* regression problems to classification problems
either a used is interested in a movie, or they are not 
At the End, either yes or no, or : politics, sports, etc.
	methods under the hood predict probability values 


Clustering : 
Given Data, group them, make sense of them, 
Data points in a cluster have a high coherence, DP in different clusters are not coherent

After Clustering : goal is to have a typical Classification of the data points 
Grouping based on contents of the data 


Neural Networks : 

back to 1940s, originally inspired by human brain of mammals works 
People didnt understand how to train neural networks 

~2010 Neural Networks got a revival 
training on GPUs is much better than on CPUs 
LLMs are based on a special form of neural networks : transformers 


we can learn from Models : a car that has been driven a million miles has a worse condition than cars with fewer miles 

In the last 20 years [[Machine Learning]] has become common, before companies didnt record data, nowadays there is much more data to be used 

Recommend Systems, search, etc. are being driven by [[Machine Learning]] 

there is structured data, and semi-structured data
we will focus on structured data 

rows : datapoints 
columns : features 

there are also un-structured and semi-structured data 

un-structured : sequence of characters, example : E-Mail 
semi-structured : content doesnt have a fixed structure

many methods rely on structured data

we are not interested in data types, but types of features 
german : " skalen niveau "
Essentially : what operations can we apply to them 

### 1 Nominal Features  ( =, != )
we can compare two values -> is it the same value ? 
> e.g gender of person, color of car 

what is the most frequent value ? 
` We can not compute anything with it ` `

does it make sense to compute a mean ? 
	
### 2 Ordinal Features ( < , > )
We can do everything we can do with nominal features and more 

There is a *natural order* in features : 
> e.g customer satisfaction level, energy [[class]] of car 

A - customer is really satisfied 
B - customer is okay with it
[[C]]...


### 3 Numerical Features ( +, -, * , / )
anything we can do with nominal and ordinal feaetures 
Numerical Features allow arithmetic operations : 

> e.g income of household, number of emissions,

 We can : compute difference, mean, variance, 


EstateType : Nominal Feature 
EnergyClass : Ordinal Features 
MonthlyRent, Area, DistanceToCenter : Numerical Features 


## Supervised vs Unsupervised Learning 
Supervised methods assume that training data is available -> target feature 
Unsuoervised Learning : task is not to structure data, but find out what DP do not look like other data points 
	which temperature points do not make sense -> temp sensor recording 2000º




## Classification 
Decision Trees being used to determine e.g a Topic of an article 
We can see why a document was classified as a sports, politics document 


## Neural Networks 
backbone of artifical intelligence 
we learn to approximate arbitrary functions 
	any function that evaluates to true / false 

## Supervised Methods
Require  Pior Data to learn from, and be able to predict a target feature

## Unsupervised Methods
Don't require previous Data, Try to make sense out of the Data itself, e.g group DataPoints, or locate Outliers

## Semi-supervised Learning
Takes both labeled Data (for which the target feaeture is known)
And unlabeled Data (for which target is unknown)
## Reinforcement Learning
Learns to choose suitable Actions to be able to maximize a Reward Function 




# Remember : 
Types of Features : Nominal, Ordinal, Numerical Features 
...



# Chapter 2 : Regression 

	Aims at predicting a numerical Target Feature



One ore more features, 
we want to predict another feature, they are numerical
we need to make a model assumption 

x-axis feature is given 
y-axis feature we want to predict 

for hte training data, we know the correct value for y 

we identify a plane, find a plane that best approximates data points 
how can we fit more complex data points ? 

# Chapter 3 : Classification 

	Aims at prediciting a nominal target feature based on one or multiple numerical features

### Example applications:

- classify an incoming e-mail as spam or not-spam

-  determine sentiment (e.g., negative, neutral, positive) of a customer review for a specific product


# Chapter 4 : Clustering 

	Aims at revealing the structure of data by grouping data points 

	Similiar Points are grouped, dissimilar ones are separated 

### Example applications:

- identify segments of customers based on their purchase histories (e.g., for marketing campaigns)

- group newspaper articles according to topic (e.g., to [[build]] a portal organized by topics)

# Neural Networks 

	Are the BackBone of Modern Aritifial Intelligence 
Drive Image recognition, Large Language models 

# Summary 

	Machine learning aims at gaining insights from data and making predictions based on it

- Nominal, ordinal, and numerical features differ in the operations that can be applied to them

- Regression and classification methods are supervised and predict a numerical and nominal target feature, respectively based on other (numerical) features

- Clustering methods are unsupervised and group similar data points together



