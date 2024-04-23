# Predict real estate price
I've built a regression model to predict real-estate property prices based on bedrooms, bathrooms, acre lot size, street, city, state, and house size.
3 regression models were trained and tested to find the best one out of all, to measure this I utilized the mean absolute error and the R Squared Score.
<hr>


# Visualization & Preprocessing
Firstly, I removed all rows with null values. Then I checked how the average prices in each state vary, with this graph I was able to notice the trend between states and some states proved to be outliers. All states with less than
a 1,000 count in the dataset are removed, such as Guam, Virgin Islands, and Alaska.
![vis1](https://github.com/HarshaBeth/Machine-Learning-Price-Prediction/blob/main/vis/vis1.png)

Next, I checked the correlation between the number of bedrooms and the average number of bathrooms. As can be seen from the graph there is a pattern in the beginning and then it changes,
That is where we separate our data and remove the outliers aka noisy data.
![vis2](https://github.com/HarshaBeth/Machine-Learning-Price-Prediction/blob/main/vis/vis2.png)

After I reduced the dataset only to have a maximum number of 12 bathrooms, it also reduced the maximum size of the "acre lot size" in our dataset.
By checking "df_visuals[df_visuals['bed'] <= 12]['acre_lot'].max()", we get 100,000 as the maximum size.

Our final visualization to check for outliers is in the bathrooms column. I check the average price per number of bathrooms throughout our current dataset. From our graph, it is visible
that the data starts going out of the incremental trend after 11 bathrooms. This means the data is either not enough or wrongfully entered. Either way, we remove all rows with bathrooms 
above 11.
![vis3](https://github.com/HarshaBeth/Machine-Learning-Price-Prediction/blob/main/vis/vis3.png)

Further stages of pre-processing our data include finding and deleting the duplicated rows. Moreover, shuffling our data to ensure there is no bias.

<br>

# Training and Testing Regression Models
I trained a Decision Tree Regressor before the pre-processing and got a R-squared score of only 11%. After the pre-processing steps, it increased to 23% with a "mean absolute error" of around 205,000. However, this is not enough. To further enhance this model I tuned and found the best amount of leaf nodes to be 25,000. This reduced our MAE by 10,000 more.

However, I believe other models have a possibility of giving a more accurate prediction.

So I trained a Gradient Booster Regressor and the R-squared score turned out to be an improvement by 20%. But the MAE was around 223,000 which is worse than our first model. Even after my attempts at tuning the Gradient boost regressor it didn't improve by much.

The last model I trained and tested for prediction is the <ins>**Random Forest Regressor**</ins>. Not only was our MAE much better, but our R-squared score was the highest out of all the other models!
MAE is now around 158,000 and our R-squared score is 54.6%. It is a major improvement from what our first model gave us!


