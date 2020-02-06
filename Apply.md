# 
Apply
#

1. Apply lambda functions to certain colummns
```python
fn = lambda x: x.capitalize()
df['job'] = df['job'].apply(fn) # replaces column
```

2. Apply user defined functions
```python
def legalAge(x):
    if x > 17:
        return True
    else:
        return False

df['legal_drinker'] = df['age'].apply(legalAge)
```

3. Apply function to every value in dataframe
```python 
times10 = lambda x: x*10 if type(x) is int else x

df.applymap(times10) # Method 1
df[:].apply(times10) # Method 2 
```

