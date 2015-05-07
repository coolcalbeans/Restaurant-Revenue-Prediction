# Restaurant-Revenue-Prediction
Problem: With over 1,200 quick service restaurants across the globe, TFI is the company behind some of the world's most   well-known brands: Burger King, Sbarro, Popeyes, Usta Donerci, and Arby’s. They employ over 20,000 people in   Europe and Asia and make significant daily investments in developing new restaurant sites.  Right now, deciding when and where to open new restaurants is largely a subjective process based on the   personal judgement and experience of development teams. This subjective data is difficult to accurately   extrapolate across geographies and cultures.   New restaurant sites take large investments of time and capital to get up and running. When the wrong location   for a restaurant brand is chosen, the site closes within 18 months and operating losses are incurred.   Finding a mathematical model to increase the effectiveness of investments in new restaurant sites would allow   TFI to invest more in other important business areas, like sustainability, innovation, and training for new   employees. Using demographic, real estate, and commercial data, this competition challenges you to predict the   annual restaurant sales of 100,000 regional locations.

Methodology Used:

1) Data Visualization: Understanding and verifying the underlying distribution of data. E.g. whether there are continuous variables, whether variables need transformations to reduce skew and make them more modal/normal. Plotting feature significance and how the training set predictions are lining up. 

2) Data Scrubbing: Making sure all the data types are as expected (Float, int, string etc). In this case, some of the data scrubbing involved: creating dummy/indicator variables for the categorical variables, concatenating the test and training set to account for all values of categorical variables, incrementing the continuous variables P1 to P36 by 1 to not encounter errors while doing log transforms on them and also using log transforms on the revenues to make it normal.

3) Data exploration: I wanted to find a way to reduce the number of continuous variables to figure what features where the most significant impact on revenues. For this, I used multiple Linear regression using StatsModels. At 95% significance, there were 15 variables that where significant. Played around a little bit with 90% significance too.

4) Model Building / Validation: I built the categorical variables on top of those 15 significant features and once used a GBRT regressor to predict revenue on the training data. Cross validating that model on the training set using MSE gave me 97% score. I then went ahead and optimized the GBRT regressor using grid search for the optimal hyper-parameters for learning rate, max depth and leaf nodes. My reasoning was the optimized model, I could get a better prediction of revenues on the test set.

5) Interpretation: On the training data, using the optimized GBRT regressor, the MSE actually went high when I optimized it in grid search. I should have just used the original model for the revenue predictions. But I missed it before the competition was over. Moral of the story: spend more time understanding the validations of the model. If I had used the model with lower MSE, I probably would have had a better score in the competition.

Results:
Ended the competition ranked 1238/2257. Happy to have beaten the sample and random forest benchmark but probably could have done better, if I had notice the sample validations faults earlier. Or had a teammate along.

To Do:

a) Understand why the Grid search was not resulting with the optimized model equal to the initial exploratory model even though I had necessary parameters in the Grid Search for GBRT and the exploratory model had better MSE.

b) Could potentially rework and predict revenues again but there would no way to validate an in improvement since we don’t have the revenues for the test data to validate against.
