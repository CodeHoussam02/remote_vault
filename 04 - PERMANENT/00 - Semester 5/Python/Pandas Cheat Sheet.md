
- In pandas we mainly deal with two types of data :
	- Series object : 1D array with indesies
			California : 385214661
			Florida : 22554689
			New York : 19651127
			Texas : 265899423

	- dataframe Object : 2D arrays 

| c          | Area   | Population |
| ---------- | ------ | ---------- |
| California | 423967 | 38332521   |
| Florida    | 170312 | 19552860   |
| New York   | 141297 | 19651127   |
| Texas      | 695662 | 26448193   |

--- 

### O1. Deal with pandas 

- import pandas and work with it 

```python 
import pandas as pd
import numpy as np 
```

---

##### 01. Deal with series object 

- create a serie in pandas 

```python
data = pd.Series([15, 12, 44, 35])
data # in order to print out the data
```

this will show the indesies explicitly 

- output 

	0  15
	1  12 
	2  44
	3  35

- convert into Numpy array 

```python 
data.values
type(data.values) # numpy.ndarray
```

- Indexing in Series 

```python
data[0]
```

- custum indexing

```python
data = pd.Series([55, 69, 455, 4], index=['first', 'second', 'third', 'fourth'])
```

- How to create a pandas serie from a python dict

```python
population_dict = {
    'california' : 38332521,
    'New York': 54514554, 
    'Florida': 57784456,
    'Huston': 477956231
}
da = pd.Series(population_dict)
```

- Implicit and explicit indexing 

```python
da['california':'FLodida'] # includes the end 
da[:-2] # desn't include the end
```


## 02. How to deal with Dataframes 

- how to create a dataframe from 2 or more series 

```python
pop_dict = {
    'Morocco': 127272,
    'United Kingdom': 123123,   
    'United States of America': 1229022, 
    'China': 29292930292, 
}
pop2 = pd.Series(pop_dict)
area_dict = {
    "Morocco": 102, 
    "United Kingdom": 130,
    "United States of America": 202, 
    "China": 202
}
area1 = pd.Series(area_dict)

# create a dataframe using the two series 
dataframe = pd.DataFrame({'population': pop2, 'area': area1})
dataframe
```

- using this method here we can create dataframes from regular python objects 
- we add the 'index=' attribute in order to give a name or labeling each row

```python
pd.DataFrame({
    'population': [2329293, 1282839, 38291823, 3828192],
    'area': [202, 18, 192, 102]
}, index=["Rabat", "Casablanca", "Tangier", "Marrakech"])
```

- in order to view or list the index labels using pandas we do the following 

```python 
temp_data.index # Index(['Rabat', 'Casablanca', 'Tangier', 'Marrakech'], dtype='object')
```

- list columns names 

```python
temp_data.columns # Index(['population', 'area'], dtype='object')
```

- get the `area` column

```python
temp_data['area']

"""
output 

Rabat 202 
Casablanca 18 
Tangier 192 
Marrakech 102 
Name: area, dtype: int64
"""
```

- create a dataframe from a single serie object 

```python
notes = pd.Series([12, 15.6, 14, 16], index=['houssam', 
'laila', 'Abdelhay','soukaina'])

# dataframe
note_df = pd.DataFrame(notes, columns = ['Notes'])
note_df2 = pd.DataFrame({'notes': notes})

# note_df
# note_df2
```

### 01. Indexing and selection in dataframes :

- Read from a csv file

```python 
import pandas as pd 

df = pd.read_csv('./Ramen-rating.csv')
df # list our new created datafrane
```

- read five first/last rows of a dataframe

```python
# read from a csv file
df = pd.read_csv('./ramen-ratings.csv')

# list first 5 rows 
df.head() # list 5 first rows by default
df.head(10) # explicitly list the first 10 rows
df.tail() # list 5 last rows by default
df.tail(20) # explicitly list the first 20 rows
```

- Retrieve the `country` column

```python
df['Country']
df.Country
```

- Implicit & Explicit indexing 
	- 

- Select the first column

```python

# iloc
df.iloc[0, :] # or df.iloc[0]
"""
output :
Review # 2580 
Brand New Touch Variety T's 
Restaurant Tantanmen 
Style Cup 
Country Japan 
Stars 3.75 
Top Ten NaN 
Name: 0, dtype: object
"""
```

- select the first 3 rows 

```python
df.iloc[0:3, :]
df.head(3)
```

- select the last row 

```python
# df.iloc[-1: :]
df.tail(1)
```

- select the last column of your dataframe

```python
df.iloc[:, -1]
```

- Fancy indexing in pandas 
- extract the 1, 20, 182 rows from your df

```python
df.iloc[[1, 20, 182], :]
```

- select the last 10 rows of your data 

```python 
df.iloc[-10:, :]
df.tail(10)
```
#### 02. Label based selection :

- select `brand`, `style` and `stars` columns

```python
df.loc[:, ['Brand', 'Style', 'Stars']]
```


#### 03. Understand the diff between `loc` & `.iloc` ?

- `iloc` : implicit indexing <font color="#ee4545" style="text-decoration: underline; font-weight: bold">( doesn't include the end )</font>
- `loc`  : explicit indexing <font color="#ee4545" style="text-decoration: underline; font-weight: bold">( it includes the end )</font>

### 03. Conditional Selecting data

-  to explore the data, you gotta ask interesting questions.
- extract all the reamen dishes served in Taiwan.
- Masking : check where condition is true and where it's not

```python
# masking 
df['Country'] == 'Taiwan'
# selection 
df.loc[df['Country'] == 'Taiwan']
```

- extract all the stores that have a rating above the avarage rating 2.5

```python
new_df = df[df.Stars != 'Unrated']
new_df.Stars = new_df.Stars.astype(float)
new_df[new_df.Stars >= 2.5] # or df.loc[new_df.Stars >= 2.5]
```

- dishes served in taiwan with a rating above the avarage rating 
	- & : and percent
	- | : or 
	- ~ : not 

```python
new_df[(new_df.Country == 'Taiwan') & (new_df.Stars >= 2.5)]
```

- Get only the `Brand` and `style` of these dishes

```python
new_df.loc[(new_df.Country == 'Taiwan') & (new_df.Stars >= 2.5), ['Brand', 'Style']]
```

- let's have a look to dishes served in both `Finland` and `Sweden`

> [!error] Note 
> always put the condition between () brackets otherwise it wont work the selection

```python
df.loc[(df.Country == 'Finland') | (df.Country == 'Sweden')]
```

- get the not null values from the `Top Ten` column

```python
df[~df['Top Ten'].isnull()] # using the not operator in pandas 
df[df['Top Ten'].notnull()]
```


### 04. Assigning data in pandas 

- sksk

```python
```

- create a new column in our dataframe

```python
df['isStyleCup'] = df.Style == 'Cup'

"""
|Review #|Brand|Variety|Style|Country|Stars|Top Ten|isStyleCup|
|---|---|---|---|---|---|---|---|
|0|2580|hi|T's Restaurant Tantanmen|Cup|Japan|3.75|NaN|True|
|1|2579|hi|Noodles Spicy Hot Sesame Spicy Hot Sesame Guan...|Pack|Taiwan|1|NaN|False|
"""

```