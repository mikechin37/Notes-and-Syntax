#
Grouping Data
#

1. Groupby Average
```python
# Average everything in dataframe with respect to continent
df.groupby('continent').mean()

# Which continent drinks more beer on average?
df.groupby('continent')['beer_servings'].mean()

2. Print statistics for x variable per continent
# spits out count, mean, std, min, max
df.groupby('continent')['wine_servings'].describe()
```

3. Groupby Median

4. Convert pandas.core.groupby.SeriesGroupBy to dataframe

```python
# a) .apply
seriesObj.apply(pd.DataFrame)

# b) .agg with multiple functions
df.groupby('continent').beer_servings.agg(['sum', 'mean', 'min', 'max'])
```

5. Converting categorical vars to numerical (eg. Getting male gender ratio per occupation)
```python
# create function
def gender_to_numeric(x):
    if x == 'M':
        return 1
    if x == 'F':
        return 0

# apply function to gender column in df and create new column
df['gender_n'] = df['gender'].apply(gender_to_numeric)

# Use groupby to create series Object of gender ratio per occupation
gender_ratio = df.groupby('occupation').gender_n.sum() / df.occupation.value_counts() * 100
gender_ratio.sort_values(ascending = False)
```

6. Groupby with combination of two x vars
```python
# For each combination of occupation and gender, find mean age
df.groupby(['occupation', 'gender']).age.mean()
```

7. Get percentage of x var per group
```python
a) For each occupation present the percentage of women and men
# Create dataframe of just gender counts
gender_count = df.groupby(['occupation', 'gender']).agg({'gender':'count'})

# Create dataframe of just occupation counts
occup_count = df.groupby(['occupation']).agg('count')

# Divide the two dataframes to get gender per occupation
occup_gender = gender_count.div(occup_count, level = "occupation") * 100
occup_gender.loc[:, 'gender']
```

