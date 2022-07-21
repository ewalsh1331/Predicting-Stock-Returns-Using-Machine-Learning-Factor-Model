# Predicting-Stock-Returns-Using-Machine-Learning-Factor-Model

This project was created as a way to employ machine learning with stock data. Stock data provides a
specific challenge in the sense that there is a large amount of data, and the data itself is split
into multiple different tickers. This means formatting for the data often falls into hierchical 
structures, which can be difficult to implement with machine learning. Not only was this a challenge, but it is also
time series data (and temporal aspects are incredibly important), so care is needed when dealing with the temporal
aspects. 

The project itself showcases the strength of complex models when trying to garner a small edge (as is often the case with 
predicting stock retruns, who's day to day movements are volatile and random). The project employs gradient boosted 
regression trees to create return predictions for specefic tickers. These black-box models can be hard to interpret, 
so the project also employs SHAP values, a realtively new technique to understand why a complex model is making certain
decisions. (Link to the original reserach paper: https://arxiv.org/abs/1705.07874). 



1. Preparing the Model Data
This file deals with data ingestion, data cleaning, data formatting and factor creation. Unfrotunately, the
data used for this project is not available for public use, but some techniques here are usefull and provide
understanding to the rest of the model. 


2. Trading Signals

Train seperate models for different lookaheads, in this case focusing on 1 day, 5 day and 21 day returns. We also
set different training/testing lengths to test as hyperparameters using cross validation. Then, using the LightGBM module, 
run hyperparameter testing, using spearman rank correlation coefficient as the measuring of model strength. Stores all the 
results for each cross validation run and hyperparameter combination. 


3. Evaluate Trading Signals

Using the results from the previous step, assess the hyperparameters by their information coefficient from the
previous step. Creates visualizations of the different models that were trained, and choose which models performed
the best. 
Breaks down the best models for each lookahead, showing how they performed over time. Combines the predictions from the top 
5 models, and creates factor returns over different time frames. Analyzes the returns over time, and shows the alpha the model
created in the validation runs (using Alphalens module). 


4. Model Interpretation

Train a model on the best hyperparameters, and asses how the model is making decisions. This is done by both using feature importance
and SHAP values. 

5. Making out of Sample Predictions

Uses the model to create out-of-sample predictions. Trains a model, then uses the model to create factors from the model(s). Does this 
for a 1 year out of sample period, updating the model over time depending on how the train/test lengths were done
during the hyperparameter optimization. 


6. Using Predictions to Draw Conclusions

Analyze how the model is performing out-of-sample. Uses some SHAP values to look into how the model reached certain predictions as well.
Uses factor quantile breakdowns to analyze the strength of the model. 


7. Backtesting with Backtrader

Uses backtrader to set up some simple backtesting environements with commission fees to see if the model can be leveraged
in a real world environments. Creates visuals and some breakdowns for how the model is performing. Also has some simple drawdown
and volatility measurements. 


