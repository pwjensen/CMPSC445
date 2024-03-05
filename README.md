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

## Model Creation

## Conclusion
