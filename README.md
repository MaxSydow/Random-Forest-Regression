# Predicting Bandwidth Usage With Random Forest Regression

# About
In general, higher bandwidth subscriptions cost more and therefore bring more revenue for an ISP. The Customer Churn data set contains a field named InternetService, which describes the type of internet service a customer subscribes to and reveals that the provider offers both DSL and Fiber Optic based network options. A fiber optic network can provide much higher speeds than DSL, but requires more complex infrastructure. 20 years ago bandwidths on the order of 100MBps or even in excess of 1GBps were not very desirable, but today's consumers often require such higher speeds. Holding on to higher bandwidth using customers and even expanding a fiber optic infrastructure footprint is therefore a worthwhile effort.

The churn data set provides several fields that describe the types of services a customer subribes to, some information on specific devices they use, demographic data and measures of sentiment regarding customer experience. All of these fields may be used to give a profile of high bandwidth using customers. The ability to identify them can be useful to orient marketing and customer service interaction priorities to promote greater retention. Demographic and characteristic data may be available from other sources for geographic regions beyond the current footprint so that areas of potential network expansion may be better identified. Is it possible to create such a predictive customer bandwidth usage profile, and if so which fields have the most influence?

## Predictive Method
Bandwidth usage, as a feature in the Customer Churn ISP data set includes a wide range of continuous numerical values. A classification model would not be appropriate to make predictions, as such a model indicates the likelihood of an outcome going one way or another. To make predictions on a continuous outcome a regression model would be more suitable. Linear regression could be used, but it may turn out that there is not a linear relationship between predictor and target variables. A decision tree based algorithm can capture non-linear subtleties by learning from rules applied to features. (Li, 2019).

A tree structure begins with a root node containing the entire sample of training data that splits into child nodes based on a decision made according to an information gain metric. These child nodes then get split into more child nodes of thier own based on another decision. This process repeats until the final collection of subsets result in a prediction on the target variable. (Gurucharan, 2020). Decision trees can be used for either classification or regression, and the number of of subsequent node splits is referred to as tree depth.

As the depth of a tree gets larger the size of each node's subsets gets smaller. If the tree were allowed to continue to the point of irreducible subset size then predictions may become too specific to individual data points, which poses the risk of overfitting. Two trees applied to the same data may still have differing predictions at the end. Instead of running several trees with different parameters a collection of randomly composed trees can be computed in a single algorithm called a random forest. The random forest considers many permutations of subsets that individual trees use, then returns a majority vote of each of the trees' leaves' predictions.

The random forest regressor needs to know how many trees to use ("n_estimators"), and each tree should have the number of levels specified ("max_depth"). These are parameters of the model that can be tuned through cross validation. Multiple options of these paramaters can be input into a search algorithm to find which ones result in the greatest accuracy. Some other parameters include, but are not limited to, number of features considered in the split decision ("max_features") and the minimum number of samples required in a leaf node ("min_samples_split"). (scikit-learn, 2007-2021)

## Packages Used
The data was processed, modelled and analyzed using Python. The following packages and libraries were used:

Pandas: general dataframe handling

warnings: ignore uneccesary warnings that don't affect outcomes of data operations

sklearn

model_selection

train_test_split: split data into training and testing sets
RandomizedSearchCV: cross validation using random grid elements
ensemble

RandomForestRegressor: create and fit random forest model
metrics

make_scorer: define a specific accuracy score
mean_squared_error: computes mean squared error in predictions
matplotlib.pyplot: plotting and graphics


## Update
This project has been revisited as an attempt to obtain a higher predictive accuracy.  Changes to data cleaning and feature engineering were made, new paramaters were tried, and a comparison to a linear regression model was explored.  These changes can be found in the Random_Forest_Regression_V2.ipynb file.  Note: the commentary needs improvement, but should outline the basic essentials of the new approach.
