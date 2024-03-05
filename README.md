# Philadelphia Housing Market

## Data Collection

The data in this project was provided by the City of Philadelphia. By accessing the [Philadelphia.gov Properties Data](https://www.phila.gov/property/data/) website, a CSV can be downloaded with the current data for all property data in the Philadelphia area. The dataset contains 81 columns and more than 500,000 rows. The dataset was downloaded as a CSV file and was read into a pandas dataframe for analysis. I attempted to scrape data from both the Zillow API and Homes website but neither cooperated and would not provide the required amount of data.

The dataset primarily contained property inspection data for all types of properties in Philadelphia, including information on the property's inspection information, location, owner(s), sale information, etc.

## Preprocessing

Because of the amount of data, and the lack of consistency in data being input into the dataset, preprocessing took the majority of the time for this project. The preprocessing steps taken include dropping columns, fill empty values, adjusting datatypes, one hot encoding, binary encoding, and removing outliers.

The first step of this process was to remove columns that had huge amounts of data missing. I initially kept all columns that had less than 20% of their data missing. These columns as well as a lot of columns that will not help our models have been removed from the dataset.

After getting rid of the missing data, we can look specifically at the types of properties included. The model that we are trying to create is for residential homes in the Philadelphia, however, this dataset holds other properties like empty land, garages, and apartment buildings. To get a better idea of the price of homes, we will be removing all of these extra rows.

Next we need to change how some of the data is being held in the dataset. Currently, we have a lot of object types, which will not work for our models. To fix this issue, we will change a couple columns to boolean values where applicable, and either one hot encode or binary encode the rest of the categorical data.

One hot encoding helps when there are only a few distinct values in a column, but when there are many different values, using binary encoding works much better as it reduces the dimensions of the data.

After all of the columns are corrected in the way we want them, we can see in the data that there are many outliers that scew the data. To easily remove these, using the interquartile range of the data will remove all rows that contain an outlier of some kind. While this does remove a lot of rows, we still have well over 100,000.

Finally, before moving on to feature selection, we want to scale all of the data. We can do this by using the MinMaxScaler provided in the sklearn.preprocessing module.

## Feature Selection

Since there are so many columns available at the beginning of the preprocessing steps, there is an abundance of options for feature selection. Through different testing, the final csv holds the columns I believe to be the best for creating regression models. Aside from this model, PCA was used in parallel to compare against for each model. Since PCA selects only some of the total features, it could end up being either more or less accurate. In our case, for this exercise PCA results in lower $R^2$ scores.

## Model Creation

Now that the data is preprocessed and we have the features selected for use, we can put out trained data into different models. For each of the models; Linear Regression, Decision Tree, Random Forest, and Gradient Boost, the non-PCA data performed better. Keep in mind, if the dataset is pulled later and cleaned in the same way, results may differ.

**Linear Regression**: $R^2$: .9788 RMS: .0216 MAE: .0077
**PCA**: $R^2$: .6907 RMS: .0829 MAE: .0630

**Decision Tree**: $R^2$: .9958 RMS: .0097 MAE: .0008
**PCA**: $R^2$: .9543 RMS: .0319 MAE: .0139

**Random Forest**: $R^2$: .9979 RMS: .0068 MAE: .0007
**PCA**: $R^2$: .9801 RMS: .0211 MAE: .0095

**Gradient Boost**: $R^2$: .9934 RMS: .0121 MAE: .0041
**PCA**: $R^2$: .9222 RMS: .0416 MAE: .0277

We want the $R^2$ score to be as close to 1 as possible, but not 1, and we want the RMS and MAE of the model to be as close to 0 as possible. Through these tests, we can see how each model performs on our provided data for both accuracy in the model and how well each model predicts values.

## Conclusion/Discussion

This project helped my understanding in the various ways of preprocessing data. The preprocessing aspect of this project was actually the most difficult and time consuming. Because of the dataset chosen, a lot of the data had to be transformed or dropped completely. After all of the practice, however, I have a better understanding on when to use what methods in cleaning data.

The feature selection and model selection parts of the project were both straight forward. Make models to test the features are selected and try to get the best scores as possible is the main idea here. Since this is the case, once the preprocessing was complete, these parts felt like a breeze to complete.

Overall, thie experience in this project gave me a deeper understanding on regression models and using pandas.
