#
Getting and Knowing your Data
#

1. Get number of observations in dataset

```python
df.shape[0]
df.info()
```

2. Create dataframe from raw data given as dictionary, not csv
```python
aw_data = {'col1': ['row1', 'row2', 'row3'],
           'col2: ['row1', 'row2', 'row3']}
df = pd.DataFrame(raw_data)
```

3. Get number of columns in df
```python
df.shape[1]
```
4. Print name of all columns in df
```python
df.columns
```
5. How is dataset indexed?
```python
df.index  # gives you start, stop, & step
```

6. What is the most frequent or highest quantity item? How many items were ordered? 
```python
most = df.groupby('item_name').sum()    #specific to this example where quantity is specified in dataframe
most.sort_values(['quantity'], ascending=False)
most.head(1)
```

7. Apply lambda function to dataframe column. Convert all item prices into float:
```python
fn = lambda x: float(x[1::])
df['item_price'] = df['item_price'].apply(fn)
df['item_price'].dtype
```

8. Get TOTAL number of UNIQUE values, in this case unique 'Order IDs'
```python
	a) df['order_id'].value_counts().count()
	# .value_counts() returns two column series displaying: order ID, count of unique values
	# .count() will count the number of rows in the series
	b) df['order_id'].nunique()
```
9. Get AVERAGE revenue per order
```python
df['revenue'] = df['quantity'] * df['item_price']
df_grouped = df.groupby('order_id').sum()
df_grouped.mean()['revenue']
```

10. Get AVERAGE of ONE COLUMN
```python
avg_age = df['age'].mean()
```

11. What is the age with least occurrence?
```python
df['age'].value_counts().tail()
```

12. Get nth column, in this case 105th column
```python
df.columns[104]
```

13. Set one of columns as index of df
```python
df.set_index('Time', inplace = True) # Method 1
df = df.set_index('Time', drop = True) # Method 2
```

14. Delete columns
```python
del df['Total']
```

15. Get location/index of maximum values 
```python
df.idxmax(0) # outputs row/index for each column's max value
df.idxmax(1) # outputs column for each row's max value
```


