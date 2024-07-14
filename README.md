# Regressor
 
<h2> Problem Statement </h2>
Develop Regressor optimal ML model to predict car sale prices. The provided dataset is form kaggle and contains information on 426K cars to ensure speed of processing.  The goal is to understand what factors make a car more or less expensive for client such as a used car dealership who would like to know what consumers value in a used car.


<h2> Analysis Processing Summary </h2>

1. There are 426880 unique records of cars.
2. Descriptors variables like VIN, drive, type, size, paint color, condition & cylinders seems have 30% or less data. These variables do not change much for a car as well and hence have been excluded these from the analysis.
3. Amongst numeric columns (odometer, price, , year), no fetures are highly correlated to price. Hence, no features are removed.
4. Removed "ID, VIN, model" variables which have high cardinality.
5. There are 2 unique numeric columns in the dataset.
6. Eight categorical variables - 'region', 'manufacturer', 'fuel', 'title_status', 'transmission', 'type', 'state'
7. "Year' is an ordinal feature
8. I created a column transformer to a) standardize / scale the number values from 0 to 1 and b) One hot encoded the categorical columns. Left with a transformed dataframe with 532 features.
9. Since 532 columns after onehot encoding and its are taking long time for processing, I dropped columns of states where price is less than the mean price of all cars -> resulting in dataframe with 132 features/columns


<h2>** Data Obeservations </h2>

1. Price seems to be in increasing trend post year - 2000
2. States - California followed by Oregon and Delaware has highest prices 
2. Manufactures - Toyota, Chevolet and Meercedes-benz has highest sale prices 
    
<h2> Modeling </h2>
I implemented two models:
1. Simple Linear Regression:
   Fine tuned the model using gridsearch cross validtaion to find optimal parameters: copy_X  & fit_intercept
   
3. Lasso Regressor:
   Fine tuned the lasso model using gridsearch cross validation to find optimal parameters: alpha & max_iter (max iterations)


<h2> Modeling Results </h2>
1. Linear Regression Model 1 Result Summary:
   
   Train mean squared error score is 1.330
   Test mean squared error score is 0.0026
   Mean Test Score of best estimator model is -1109.4

   Given that we can say that model fits and predicts the data well wth low variance. 
   Cross validation picked the best with model with 'copy_X' = True & 'fit_intercept' = False
    

3. Lasso Regression Model 2 Result Summary:

 Train mean absolute score is 1.3333
 Test mean absolute score is 0.00005087
 Given that we can say that lasso model overfits the test data wth low variance. 
 However, cross validation did not help here in arriving at the better model.

Applied Permutation importance to explain feature predictability score towards price

<h2> Model Recommendations to Customer (Findings) </h2>

1. Customers are highly likely to buy high price cars n California.
2. When the car is automatic, the price is selling for high prices.
   However, car transmission being manual or other, also yield high sales but lower by 4 times than automatic transmission cars.
3. Further, amonsgt the fuel types, gas fuelled cars predict high sale price of the cars.
4. Other state that predict high sale prices are oregan
5. Customers are highly likely to buy high price for sedan cars.
   
    
