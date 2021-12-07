# Ames, IA Housing price prediction model 
##### Thomaz Moon
---

## Problem Statement

A Real Estate investment group hired me to teach their analyst Bob (who is already familiar with python), how to build a prediction model. Along with going over different model types, they would also like me to give some advice and recommedations as to how to deal with future models he might have to deal with without me there.  
#### City Boundary Map
<img src='./imgs/ames.png' title = "Ames City"/>   [image from here](https://zipmap.net/Iowa/Story_County/Ames.htm)

--- ---
## Executive Summary

This project will explore the Ames, Ia dataset found on the kaggle competition hosted by my school. Our goal is to make at least one prediciton on the Kaggle competition, as well as answer our problem statement. Although only 15 students, I still managed to get in a very close first place position and feel as though I am confident enough to answer my problem statement of helping Bob make a good model as well as providing adivce as I had even helped some classmates improve their scores.    

For this project, I split my code into 3 main notebooks. The first notebook will be used to show how I cleaned did some EDA as well as made the Linear Regrssion model. The second notebook will explore the way I went about cleaning and making the model for the Ridge test, as well as how I also test on the Lasso test. The last notebook will mostly be for Bob where I go more indepth about why I decided to do the things I did when making my model such dropping certain columns, dealing with NaN data, as well as future advice for any models he might have to make as the advice is more broad statements rather than focused on these housing model predictions.  

An important thing to note is that I did get some outside information such as the school boundaries and zip codes a I found that the School boundaries did in fact help my score. Below I've included a picture of the map of Ames, as well as the school boundaries for it that I used. I am also listing google maps as a source because I input each neighborhood one at a time on google maps to compare and therefore used it for quiet a bit.   
#### School Boundary Map
<img src='https://www.ames.k12.ia.us/wp-content/uploads/2015/02/Boubdry2018-e1608315021657.png'>

---
## Sources
1. [Ames, IA Dateset](https://www.kaggle.com/c/dsir-830-project-2-regression-challenge/data)  
1. [School Boundrys information](https://www.ames.k12.ia.us/wp-content/uploads/2015/02/Boubdry2018-e1608315021657.png)  
1. [Zip Code for Ames](https://www.unitedstateszipcodes.org/)  
1. [Google Maps](https://maps.google.com)  
1. [Ames city boundry](https://zipmap.net/Iowa/Story_County/Ames.htm)


## Data Dictionary for columns used ([made from this website](https://www.tablesgenerator.com/markdown_tables))
#### [Full Data Dictionary Here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)
|     Column     |  Type |                        Description                        |
|:--------------:|:-----:|:---------------------------------------------------------:|
|    Lot Area    |  int  |                  Lot size in square feet                  |
|  Neighborhood  |  obj  |         Physical locations within Ames city limits        |
|     School     |  obj  |      Schools based where the neighborhood was located     |
|  Overall Qual  |  int  |     Rates the overall material and finish of the house    |
|  Overall Cond  |  int  |          Rates the overall condition of the house         |
|   Year Built   |  int  |                    Year house was built                   |
| Year Remod/Add |  int  |    Year house was remodeled or had additional work done   |
|  BsmtFin SF 1  | float |                Type 1 finished square feet                |
|   Bsmt Unf SF  | float |          Unfinished square feet of basement area          |
|  Total Bsmt SF | float |             Total square feet of basement area            |
|   1st Flr SF   |  int  |                  First Floor square feet                  |
|   2nd Flr SF   |  int  |                  Second floor square feet                 |
|   Gr Liv Area  |  int  |        Above grade (ground) living area square feet       |
| Bsmt Full Bath | float |                  Basement full bathrooms                  |
| Bsmt Half Bath | float |                  Basement half bathrooms                  |
|    Full Bath   |  int  |                 Full bathrooms above grade                |
|    Half Bath   |  int  |                   Half baths above grade                  |
|  Bedroom AbvGr |  int  | Bedrooms above grade (does NOT include basement bedrooms) |
|  Kitchen AbvGr |  int  |                    Kitchens above grade                   |
|  TotRms AbvGrd |  int  |    Total rooms above grade (does not include bathrooms)   |
|   Fireplaces   |  int  |                    Number of fireplaces                   |
|  Garage Yr Blt | float |                   Year garage was built                   |
|   Garage Cars  | float |               Size of garage in car capacity              |
|   Garage Area  | float |               Size of garage in square feet               |
|  Wood Deck SF  |  int  |               Wood deck area in square feet               |
|  Open Porch SF |  int  |               Open porch area in square feet              |
|     Mo Sold    |  int  |                      Month Sold (MM)                      |
|     Yr Sold    |  int  |                      Year Sold (YYYY)                     |
|    SalePrice   |  int  |                       Sale price $$                       |


## Recommendations for Bob
1. To start, a big recommendation I would have for the Real Estate company's analyist (Bob), would be to prioritize cleaning all data for the most ammount of columns you have data for, or can easily access because that will lead to a more accurate model, which will then give you a better understanding of what is actually affecting house prices in your model city, as well as the features/parameters people are paying attention to when purchasing a new home.
> But it is important to know how to spend your time cleaning the data because if the columns aren't worth much information don't bother
2. Don't limit yourself to just what you have at the moment if you can also do a bit more of leg work to get a better model going. Not only might the visual be better, which is what a lot of people understand better than just numerica data, but you can also find new factors to tell your boss to watch out for and look for patterns and trends across your whole Real Estate industry and perhaps make new discoveries.
This isn't to say that the neighborhood column is useless though. You could always find the ranking of schools and try to establish a numeric value towards the neighborhood based on the schools and proximity as well as doing a poly transformation to see how your neighborhood ranking, schools, and numeric data will affect the Mode
> Important to note that not all information will be useful. For example I first wanted to use Zip codes, but realized the there were only 3 zips in total which wouldn't really help me much at all
3. This is going to tie in with the both recommendation 1 and 2. But after you have cleaned your data, it is usually good to try to get some sort of visual going if you can, especially if you will be presenting this later on. More importantly though, you will hopefully be able to get a better understanding of what you're working with. Even if there are thousands of points in your graph, you can zoom out and try to get a bigger picture and understanding. You can also use visuals to help clean up your data by easily spotting outliers.  
>On a side note, make sure to not use confusing or hard to read visuals such as the large heatmap however. Not only will those heatmaps be hard to read and understand because there is so much unneeded information, but can also be a waste of time. Try to also be efficent when using visuals
4. Just because you get good scores on your testing model, doesn't mean that your model will perform as well on new data. Something important to rememebr about the $R^2$ score for example is that it will never go down as you add more features, even if they don't contribute. The score might go up only every so slightly, but thats still a better score. Another thing to remember is that the F-statistics and P value are here to help you look for reasons to reject your null hypothesis. Therefor just say if there is or there isn't a correlation between your feature and your target 'Sale Price' as that is what our null hypothesis is in this case, that there is a contributing factor to sale price based on our y.   
>Also keep in mind that the more features we add and more complex the model is, the less bias it will have, but doesn't necessarily mean that it will have good variance, or that the model isn't too over fit.      
>One last note about these two specific models in general is because schools are generally dependent on which neighborhood you reside in, there is a multicolinearity issue with these two columns as well which would further ruin our modeling process
1. Final Recommendations and tips
  1. Clean Clean Clean, model and clean
  1. Make sure you have a specific target (y) in mind before starting the modeling and cleaning process
  1. Check to make sure that there aren't multicolinear data in your model such as the schools and neighborhoods
  1. Use Outside Sources to your advantage
  1. If one model isn't getting good results and you've already done everything else, try another model.
  1. **What to do when you encounter Missing Data**
      1. If necessary for work, try to contact who ever you need to in order to verify or retreive the data.
      1. If its just a few rows, you might want to consider dropping the rows, esp if they have outlier data in them
      1. Not use the columns that have a lot of missing data as we did.
      1. Make a model to predict the missing values if you're comfortable enough with modeling
