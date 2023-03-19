##**Seoul Bike sharing demand prediction:**
**Business problem**: Currently Rental bikes are introduced in many urban cities for the enhancement of mobility comfort. It is important to make the rental bike available and accessible to the public at the right time as it lessens the waiting time. Eventually, providing the city with a stable supply of rental bikes becomes a major concern. The crucial part is the prediction of bike count required at each hour for the stable supply of rental bikes.

First we import the necessary libraries and look at our data and its characteristics. We have a dataset of 8760 rows and 14 columns with no duplicate/missing data. Next we study the features thoroughly and the data it represents.

In data wrangling, we first see that the column 'Date' is in 'object' datatype, and we convert it to datetime datatype. Later from the date column, we extract, 'day_of_week', 'month' & 'year' (year as a categorical value) We drop the date column and we rename columns for convinence. We convert 'hour' column to 'object' datatype as it should be considered as a categorical value.

Later we visualize our data and perform univariate analysis, bivariate analysis with respect to the dependant variable. The insights found from each chart is described. The linear relationship between the numerical features and dependant variable is also plotted. Finally, we visualize the correlation heatmap and pairplot for better understanding.

Based on our visualizations, we formulate 3 hypothetical statements and perform hypothesis tests. The statements are:

The average bike count in Seoul city at any point of time is greater than 100.
The average temperature in Seoul city at any point is grater than 10 degree Celsius.
The Standard deviation of humdidity in Seoul city is 20.
Now was the time for feature engineering. We handled the outliers in 'Wind speed' column by using the capping method. Based on the correlation heatmap, we had the columns 'dew point temperature' and 'Temperature' were highly correlated. So we dropped the 'dew point temperature' column. In the Days of week column, we obsereved from this column that the pattern of weekdays and weekends is different, in the weekend the demand becomes high in the afternoon. While the demand for office timings is high during weekdays, we can further change this column to weekdays and weekends. Furthur, we performed one hot encoding on our categorical features with dropping the first column being true. We found out during visualization that our dependant variable, 'Rented_bike_count' was right skewed, hence to overcome this we applied a squareroot transformation to get a normal distribution. Next we scaled our data using MinMax scaler. Finally we split our data into train and test in 80-20 ratio.

The data was ready to fit into a machine learning model. First, we used Linear Regression. We got adjusted r2 score as 76.65%. There was no hyperparameter to be tuned. Second, we used Ridge(L2) Regression. We got adjusted r2 score as 76.65%. We used GridSearchCV for hyperparameter tuning in which we saw a slight improvement. Third, We used Lasso(L1) Regression with GridSearchCV for hyperparameter tuning. We got adjusted r2 score as 76.65%. Our fouth algorithm was Random Forest Regressor. With GridSearchCV for setting our hyperparameters, we got adjusted r2 score as **91%**.

So finally, the bike rental company can deploy a machine learning model that uses Random Forest Regressor to predict the demand for city bikes for a particular hour, which can help the company meet the demand accurately. On the contrary when the company predicts to be a low demand day/season, the bikes can be sent to maintainance.
