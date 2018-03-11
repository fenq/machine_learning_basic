## Child mortality rates
The dataset is created from data provided by UNICEF’s State of the World’s Children 2013 report:
http://www.unicef.org/sowc2013/statistics.html

Child mortality rates (number of children who die before age 5, per 1000 live births) for 195 countries, and a set of other indicators are included.

#### Investigation
1. Which country had the highest child mortality rate in 1990? What was the rate?
Niger	313.7

2. Which country had the highest child mortality rate in 2011? What was the rate?
Sierra Leone 185.3

3. Some countries are missing some features (see original .xlsx/.csv spreadsheet). How is this handled in the function assignment1.load unicef data()?
fill with mean values for the column
```python
# Compute the arithmetic mean along the specified axis. 0 is column and 1 is row
mean_vals = nanmean(values, axis=0) 
# find the place is null
inds = np.where(np.isnan(values))
fill up the null value
values[inds] = np.take(mean_vals, inds[1])
```

For the rest of this question use the following data and splits for train/test and cross-validation.
- Target value: column 2 (Under-5 mortality rate (U5MR) 2011)1
- Input features: columns 8-40.
- Training data: countries 1-100 (Afghanistan to Luxembourg).
- Testing data: countries 101-195 (Madagascar to Zimbabwe).
- Cross-validation: subdivide training data into folds with countries 1-10 (Afghanistan to Austria), 11-20 (Azerbaijan to Bhutan), ... . I.e. train on countries 11-100, validate on 1-10; train on 1-10 and 21-100, validate on 11-20, ...

