# 
Apply
#

1. Apply function to every value in dataframe
```python 
mult = lambda x: x*10

df.applymap(mult) # Method 1
df[:].apply(mult) # Method 2 