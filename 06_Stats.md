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