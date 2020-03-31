#
Filtering and Sorting Data

#

1. Convert column in df to a different type (float)

```python
df['price_float'] = [float(item[1:-1]) for item in df['price']]
```
2. Get subset df from master df with only specified columns
```python
df_subset = df[['item_name', 'price']]
```
3. Delete the duplicates in x columns
```python
df_filtered = df.drop_duplicates(['item_name', 'quantity'])
```
4. Filter dataframe 
```python
# This will print the sub df WITHOUT creating a new df
df[df['price'] > 10]

# Using conditional statements - bitwise operators &, |
# (How many times did people order more than one Chicken?)
df[(df['item_name'] == 'Chicken') & (df['quantity'] > 1)]
df[(df['item_name'] == 'Chicken') | (df['quantity'] > 1)]

# with creating new df
df_filtered = df[df.quantity == 1]

# Filter string in search for certain characters
df[df['Team'].str.startswith('G')]
df[df['Team'].str[:] == ('y')]
```

5. Sort values from greatest to least expensive
```python

# Method 1 - creates dataframe **
df.sort_values(by = "item_name")
df.sort_values(by = "item_price", ascending = False).head()
# 1b - sort sequentially by one column then the other
df.sort_values(['Red Cards', 'Yellow Cards'], ascending = False)

# Method 2 - creates series (sucks)
df['item_name'].sort_values()
```

6. Count number of items in sorted dataframe
```python
df_veggie = df[df['item_name'] == "Veggie"]
# Get integer output
len(df_veggie)
# Get more detailed output
df_veggie.count()
```

7. Slice dataframe via the integer positions to select the first m rows, n columns
```python
# Need single brackets []
df.iloc[0:m , 0:n]
df.iloc[[1, 3, 7], :]
```

8. Slice dataframe via the labels of the columns and indexes to select m rows, n columns
```python
# Need double brackets [[]]
df.loc[df['Team'].isin(['England', 'Italy']), ['Team', 'Goals']]
```

9. Slice dataframe using both iloc and loc
```python
# Select third cell in row named Arizona
df.loc[['Arizona']].iloc[:, 2] # Method 1
df.iloc[:, 3].loc[['Arizona']] # Method 2

10. Set one of the columns as the index
```python
df.set_index('time', inplace = True)
```

