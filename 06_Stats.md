# 
Stats
#

1. Get value with most occurrences in a specified column
```python
df['item_count'].idxmax() # Method 1

df[df['item_count'] == df['item_count'].max()] # Method 2
```

2. Get index of median occurrence in column
```python
df[df.item_count == df.item_count.median()]
```

3. Get standard deviation
```python
df.item_count.std()
```

4. Get a summary with mean, min, max, std and quartiles
```python
df.describe()
```
5. Compute how many missing values for each column

```python
df.isnull().sum()

# how many non-missing values
df.notnull().sum() # Method 1 
df.shape[0] - data.isnull().sum() # Method 2
```
6. Get mean of entire dataframe, not just per column
```python
# values converts dataframe to array
# flatten collapses array into 1D
df.fillna(0).values.flatten.mean()
```

7. Get min, max, mean, stdev of each row OR each column
```python
# of each column
df.describe().iloc[[1,2,3,7], :] # Method 1
df.describe(percentiles = []) # Method 2

# of each row
df = pd.DataFrame()  # create dataframe
df['min'] = df0.min(axis = 1) # axis = 1 for row
df['max'] = df0.max(axis = 1)
df['mean'] = df0.mean(axis = 1)
df['std'] = df0.std(axis = 1)

```

5. Read csv while combining columns into datetime type
```python
# case study where column values [15, 12, 1] --> [2015-12-01]
df = pd.read_csv(url, sep = '\s+', parse_dates = [[0, 1, 2]]) #list of lists input 
```

6. Apply function to datetime to correct year
```python
import datetime
def fix_century(x): 
    year = x.year - 100 if x.year > 1989 else x.year
    return datetime.date(year, x.month, x.day)

# apply function to fix year
df['Yr_Mo_Dy'] = df['Yr_Mo_Dy'].apply(fix_century)
```

7. 
