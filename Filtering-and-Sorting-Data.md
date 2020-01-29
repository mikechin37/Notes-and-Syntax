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
# without creating new df, this will print the sub df
df[df['price'] > 10]

# Using conditional statements
# (How many times did people order more than one Chicken?)
df[(df['item_name'] == 'Chicken') & (df['quantity'] > 1)]

# with creating new df
df_filtered = df[df.quantity == 1]
```

5. Sort values from greatest to least expensive
```python
# Method 1 - creates series
df['item_name'].sort_values()

# Method 2 - creates dataframe **
df.sort_values(by = "item_name")
df.sort_values(by = "item_price", ascending = False).head()
```

6. Count number of items in sorted dataframe
```python
df_veggie = df[df['item_name'] == "Veggie"]
# Get integer output
len(df_veggie)
# Get more detailed output
df_veggie.count()
```