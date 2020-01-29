#
Getting and Knowing your Data
#

1. Get number of observations in dataset

```python
df.shape[0]
df.info()
```

2. Get number of columns in df
```python
df.shape[1]
```
3. Print name of all columns in df
```python
df.columns
```
4. How is dataset indexed?
```python
df.index  # gives you start, stop, & step
```

5. What is the most frequent or highest quantity item? How many items were ordered? 
```python
most = df.groupby('item_name').sum()    #specific to this example where quantity is specified in dataframe
most.sort_values(['quantity'], ascending=False)
most.head(1)
```

6. Apply lambda function to dataframe column. Convert all item prices into float:
```python
fn = lambda x: float(x[1::])
df['item_price'] = df['item_price'].apply(fn)
df['item_price'].dtype
```

7. Get TOTAL number of UNIQUE values, in this case unique 'Order IDs'
```python
	a) df['order_id'].value_counts().count()
	# .value_counts() returns two column series displaying: order ID, count of unique values
	# .count() will count the number of rows in the series
	b) df['order_id'].nunique()
```
8. Get AVERAGE revenue per order
```python
df['revenue'] = df['quantity'] * df['item_price']
df_grouped = df.groupby('order_id').sum()
df_grouped.mean()['revenue']
```

9. Get AVERAGE of ONE COLUMN
```python
avg_age = df['age'].mean()
```

10. What is the age with least occurrence?
```python
df['age'].value_counts().tail()
```

11. Get nth column, in this case 105th column
```python
df.columns[104]
```