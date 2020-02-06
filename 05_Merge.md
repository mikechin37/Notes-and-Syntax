# 
Merge
#

1. Append or join two dataframes
```python
# joining along rows aka adding rows
df_join = pd.concat([df1, df2]) # Method 1
df_join = df1.append(df2) # Method 2

# joining along columns aka adding columns
df_join = pd.concat([df1, df2], axis = 1)
```

2. Merge dataframes along common column
```python
pd.merge(df1, df2, on='First name')

# but only if the common column value is shared
pd.merge(df1, df2, on = 'First name', how = 'inner')

# for all values, with matching records where available
pd.merge(df1, df2, on = 'First name', how = 'outer')
```


3. Create random number series from 1 to 100, and add to dataframe
```python
df['rand'] = pd.Series(np.random.randint(1, high = 101, size = df.shape[0]))
```

4. Rename columns based on index
```python
df.rename(columns = {0: 'name', 1: 'age', 2: 'race'}, inplace = True)
```

5. Reset index dataframe in cases where concatening limits the max index
```python
df_concat.reset_index(drop = True, inplace = True)
```