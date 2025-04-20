# Pandas

**Pandas** is a Python library used for working with structured data (like tables). It simplifies the process of data cleaning, exploration, transformation, and preparation for analysis.

### Import pandas library


```python
import pandas as pd
```

## Core Data Structures
### 1. Series
A 1-dimensional labeled array that holds any data type.


```python

# Example: City population
pop = pd.Series([8.9, 3.1, 2.7], index=['London', 'Berlin', 'Paris'])
print(pop)
```

    London    8.9
    Berlin    3.1
    Paris     2.7
    dtype: float64
    

**Purpose**: A Series is useful when you want a labeled list—like a single column of data.

**Importance**: Easier indexing and operations like filtering, math, and mapping with labels.

## Series attributes
|S.no.|function|Syntx|Explanation|
|---|---|---|---|
|1.| index| Series.index| Return all the index values.|
|2.| array| Series.array| Return array of values.|
|3.| values| Series.values| Return values of series.|
|4.| name| Series.name| Returns the name of a series.|
|5.| shape| Series.shape|shape of a series|
|6.| ndim| Series.ndim|dimension of a series|
|7.| size| Series.size|size of a series|
|8.| nbytes| Series.nbytes| Memory occupied by the values.|
|9.| memory usage|Series.memory_usage()| Memory occupied by both index and values.|
|10.| empty|Series.empty| Returns True if series is empty, else false|


```python
a = [1, 2, 3, 4, 5]
index = ["a", "b", "c", "d", "e"]
b = pd.Series(a, index) # index
print(b.index)
```

    Index(['a', 'b', 'c', 'd', 'e'], dtype='object')
    


```python
c = b.array
print(c) # array
```

    <PandasArray>
    [1, 2, 3, 4, 5]
    Length: 5, dtype: int64
    


```python
b.dtype # datatype
```




    dtype('int64')




```python
b.shape # shape
```




    (5,)




```python
b.ndim # dimension
```




    1




```python
b.size # size
```




    5



### Basic mathematical operations

|S.no.|Operations|Method 1|Method 2|Explanation|
|---|---|---|---|---|
|1| addition|a + b|a.add(b)|Addition|
|2| substract|a - b|a.subtract(b)|Subtraction|
|3| multiply|a * b|a.multiply(b)|Multiplication|
|4| division|a / b|a.divide(b)|Division|
|5| modulo|b%a|a.mod(b)|remainder|
|6| power|a ** b|a.pow(b)|raises each value in the DataFrame a specified number of times| 
|7| less than|b < a|b.lt(a)|less than|
|8| greater than|b > a|b.gt(a)|greater than|
|9| equal to|b == a|b.eq(a)/b.equals(a)|compare if they are equal or not|
|10|less than equal to|b <= a|b.le(a)| lesss than or equal to|

### 2. DataFrame
A 2D structure: like an Excel sheet or SQL table.


```python
# Sample DataFrame
data = {
    'City': ['London', 'Berlin', 'Paris'],
    'Population': [8.9, 3.1, 2.7],
    'Area': [1572, 891, 105]
}
cities_df = pd.DataFrame(data)
print(cities_df)

```

         City  Population  Area
    0  London         8.9  1572
    1  Berlin         3.1   891
    2   Paris         2.7   105
    

**Purpose**: Organizes and manipulates tabular data.

**Importance**: Makes filtering, grouping, sorting, and calculations very easy across rows and columns.

### Merging two data frames
Merging two data frames in pandas can be done using the merge() function. The merge() function allows you to combine two data frames based on one or more common columns. Here's an example.

Basic syntax:
    
**result = pd.merge(df1, df2, how='inner', on='common_column')**

where:

df1 and df2 are the dataframes you want to join.

* **how** parameter specifies the type of join you want to perform. You can use 'inner', 'outer', 'left' or 'right'.

* **on** parameter specifies the common column(s) that you want to join on.


```python
# Customers DataFrame
customers = pd.DataFrame({
    'customer_id': [1, 2, 3, 4],
    'name': ['Alice', 'Bob', 'Charlie', 'David'],
    'city': ['Delhi', 'Mumbai', 'Bangalore', 'Chennai']
})

# Orders DataFrame
orders = pd.DataFrame({
    'order_id': [101, 102, 103, 104],
    'customer_id': [2, 2, 4, 5],
    'product': ['Laptop', 'Mouse', 'Monitor', 'Keyboard']
})

customers, orders
```




    (   customer_id     name       city
     0            1    Alice      Delhi
     1            2      Bob     Mumbai
     2            3  Charlie  Bangalore
     3            4    David    Chennai,
        order_id  customer_id   product
     0       101            2    Laptop
     1       102            2     Mouse
     2       103            4   Monitor
     3       104            5  Keyboard)



#### 1. Inner Join
Only matching `customer_id` from both DataFrames will be returned.


```python
pd.merge(customers, orders, on='customer_id', how='inner')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>name</th>
      <th>city</th>
      <th>order_id</th>
      <th>product</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>101</td>
      <td>Laptop</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>102</td>
      <td>Mouse</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>David</td>
      <td>Chennai</td>
      <td>103</td>
      <td>Monitor</td>
    </tr>
  </tbody>
</table>
</div>



#### 2. Left Join
All records from `customers`, and matching from `orders`.


```python
pd.merge(customers, orders, on='customer_id', how='left')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>name</th>
      <th>city</th>
      <th>order_id</th>
      <th>product</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Alice</td>
      <td>Delhi</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>101.0</td>
      <td>Laptop</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>102.0</td>
      <td>Mouse</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Charlie</td>
      <td>Bangalore</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>David</td>
      <td>Chennai</td>
      <td>103.0</td>
      <td>Monitor</td>
    </tr>
  </tbody>
</table>
</div>



#### 3. Right Join
All records from `orders`, and matching from `customers`.


```python
pd.merge(customers, orders, on='customer_id', how='right')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>name</th>
      <th>city</th>
      <th>order_id</th>
      <th>product</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>101</td>
      <td>Laptop</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>102</td>
      <td>Mouse</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>David</td>
      <td>Chennai</td>
      <td>103</td>
      <td>Monitor</td>
    </tr>
    <tr>
      <th>3</th>
      <td>5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>104</td>
      <td>Keyboard</td>
    </tr>
  </tbody>
</table>
</div>



#### 4. Outer Join
All records from both DataFrames, with `NaN` for missing matches.


```python
pd.merge(customers, orders, on='customer_id', how='outer')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>name</th>
      <th>city</th>
      <th>order_id</th>
      <th>product</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Alice</td>
      <td>Delhi</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>101.0</td>
      <td>Laptop</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>102.0</td>
      <td>Mouse</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Charlie</td>
      <td>Bangalore</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>David</td>
      <td>Chennai</td>
      <td>103.0</td>
      <td>Monitor</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>104.0</td>
      <td>Keyboard</td>
    </tr>
  </tbody>
</table>
</div>



#### 5. Join on Different Column Names
If columns are named differently, use `left_on` and `right_on`.


```python
orders_renamed = orders.rename(columns={'customer_id': 'cust_id'}) # renaming columns
pd.merge(customers, orders_renamed, left_on='customer_id', right_on='cust_id', how='inner')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>customer_id</th>
      <th>name</th>
      <th>city</th>
      <th>order_id</th>
      <th>cust_id</th>
      <th>product</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2</td>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>101</td>
      <td>2</td>
      <td>Laptop</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>102</td>
      <td>2</td>
      <td>Mouse</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4</td>
      <td>David</td>
      <td>Chennai</td>
      <td>103</td>
      <td>4</td>
      <td>Monitor</td>
    </tr>
  </tbody>
</table>
</div>



#### 6. Join Using Index
When `customer_id` is set as index in both DataFrames.


```python
customers_indexed = customers.set_index('customer_id')
orders_indexed = orders.set_index('customer_id')
customers_indexed, orders_indexed
```




    (                name       city
     customer_id                    
     1              Alice      Delhi
     2                Bob     Mumbai
     3            Charlie  Bangalore
     4              David    Chennai,
                  order_id   product
     customer_id                    
     2                 101    Laptop
     2                 102     Mouse
     4                 103   Monitor
     5                 104  Keyboard)




```python
pd.merge(customers_indexed, orders_indexed, left_index=True, right_index=True, how='inner')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>city</th>
      <th>order_id</th>
      <th>product</th>
    </tr>
    <tr>
      <th>customer_id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>101</td>
      <td>Laptop</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>102</td>
      <td>Mouse</td>
    </tr>
    <tr>
      <th>4</th>
      <td>David</td>
      <td>Chennai</td>
      <td>103</td>
      <td>Monitor</td>
    </tr>
  </tbody>
</table>
</div>



#### 7. Using `join()` Method
`join()` is a shortcut for index-based merges.


```python
customers_indexed.join(orders_indexed, how='inner')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>city</th>
      <th>order_id</th>
      <th>product</th>
    </tr>
    <tr>
      <th>customer_id</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>101</td>
      <td>Laptop</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Bob</td>
      <td>Mumbai</td>
      <td>102</td>
      <td>Mouse</td>
    </tr>
    <tr>
      <th>4</th>
      <td>David</td>
      <td>Chennai</td>
      <td>103</td>
      <td>Monitor</td>
    </tr>
  </tbody>
</table>
</div>



### Basic data exploration using pandas
|S.no.|Function|Explanation|
|---|---|---|
|1|df.head()|examine first five observation we can assign more values in bracket too|
|2|df.tail()|examine last five observation we can assign more values in bracket too|
|3|df.shape|check the no of rows & columns in a data frame|
|4|df.dtypes| # to check just the datatypes of columns
|5|df.info()|dataframe, index dtype and column dtypes, non-null values and memory usage|
|6|df.drop(columns=['C1', 'C2'])| drop unwanted column|
|7|df.sort_values("C1",ascending = False)|Sorting values|
|8|df['C1'].unique()|All unique values|
|9|df['C1'].nunique()|Number of unique values|
|10|df.isnull()|Identify null values, Null values will be true|
|11|df.fillna(df["C1"].median())|fill the missing values in the df columns|
|12|df.describe()|Summary statistics|
|13|df.rename(columns={'given_name' : 'replacement'})|rename columns|
|14|df['C1].sum()|Addition|
|15|df.C1.map|map catgory into number or vice versa|
|16|df.loc()|splicing columns based on label|
|17|df.iloc()|splicing columns based on index|
|18|df.group_by()|grouping categories and performing some maths|
|19|df.dropna()|Will drop complete row if there is any na|
|20|df.fillna()|fill missing values|
|21|df.replace()|help in encoding|
|22|df.drop_duplicates()|dropping duplicates|



```python
import seaborn as sns
# Load the mpg dataset (similar to mtcars)
mtcars = sns.load_dataset('mpg').dropna()
mtcars.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>usa</td>
      <td>ford torino</td>
    </tr>
  </tbody>
</table>
</div>



## Common Pandas Functions with Explanation

### 1. `shape` 
* Returns number of rows and columns


```python
mtcars.shape
```




    (392, 9)



### 3. `info()`


```python
mtcars.info() # Returns column names, types, and nulls
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 392 entries, 0 to 397
    Data columns (total 9 columns):
     #   Column        Non-Null Count  Dtype  
    ---  ------        --------------  -----  
     0   mpg           392 non-null    float64
     1   cylinders     392 non-null    int64  
     2   displacement  392 non-null    float64
     3   horsepower    392 non-null    float64
     4   weight        392 non-null    int64  
     5   acceleration  392 non-null    float64
     6   model_year    392 non-null    int64  
     7   origin        392 non-null    object 
     8   name          392 non-null    object 
    dtypes: float64(4), int64(3), object(2)
    memory usage: 30.6+ KB
    

### 4. `describe()`


```python
mtcars.describe() # Summary stats for numeric columns
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>392.000000</td>
      <td>392.000000</td>
      <td>392.000000</td>
      <td>392.000000</td>
      <td>392.000000</td>
      <td>392.000000</td>
      <td>392.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>23.445918</td>
      <td>5.471939</td>
      <td>194.411990</td>
      <td>104.469388</td>
      <td>2977.584184</td>
      <td>15.541327</td>
      <td>75.979592</td>
    </tr>
    <tr>
      <th>std</th>
      <td>7.805007</td>
      <td>1.705783</td>
      <td>104.644004</td>
      <td>38.491160</td>
      <td>849.402560</td>
      <td>2.758864</td>
      <td>3.683737</td>
    </tr>
    <tr>
      <th>min</th>
      <td>9.000000</td>
      <td>3.000000</td>
      <td>68.000000</td>
      <td>46.000000</td>
      <td>1613.000000</td>
      <td>8.000000</td>
      <td>70.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>17.000000</td>
      <td>4.000000</td>
      <td>105.000000</td>
      <td>75.000000</td>
      <td>2225.250000</td>
      <td>13.775000</td>
      <td>73.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>22.750000</td>
      <td>4.000000</td>
      <td>151.000000</td>
      <td>93.500000</td>
      <td>2803.500000</td>
      <td>15.500000</td>
      <td>76.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>29.000000</td>
      <td>8.000000</td>
      <td>275.750000</td>
      <td>126.000000</td>
      <td>3614.750000</td>
      <td>17.025000</td>
      <td>79.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>46.600000</td>
      <td>8.000000</td>
      <td>455.000000</td>
      <td>230.000000</td>
      <td>5140.000000</td>
      <td>24.800000</td>
      <td>82.000000</td>
    </tr>
  </tbody>
</table>
</div>



### 5. `head()`


```python
mtcars.head(3) # First 3 rows, by default first 5 rows
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
    </tr>
  </tbody>
</table>
</div>



### 6. `tail()`


```python
mtcars.tail(3) # Last 3 rows, by default last 5 rows
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>395</th>
      <td>32.0</td>
      <td>4</td>
      <td>135.0</td>
      <td>84.0</td>
      <td>2295</td>
      <td>11.6</td>
      <td>82</td>
      <td>usa</td>
      <td>dodge rampage</td>
    </tr>
    <tr>
      <th>396</th>
      <td>28.0</td>
      <td>4</td>
      <td>120.0</td>
      <td>79.0</td>
      <td>2625</td>
      <td>18.6</td>
      <td>82</td>
      <td>usa</td>
      <td>ford ranger</td>
    </tr>
    <tr>
      <th>397</th>
      <td>31.0</td>
      <td>4</td>
      <td>119.0</td>
      <td>82.0</td>
      <td>2720</td>
      <td>19.4</td>
      <td>82</td>
      <td>usa</td>
      <td>chevy s-10</td>
    </tr>
  </tbody>
</table>
</div>



**Purpose**: Get a quick overview of the dataset

**Importance**: Helps check size, structure, and data types before analysis

### 7. Selecting only Columns


```python
mtcars['mpg'] # Returns a Series (1 column)
```




    0      18.0
    1      15.0
    2      18.0
    3      16.0
    4      17.0
           ... 
    393    27.0
    394    44.0
    395    32.0
    396    28.0
    397    31.0
    Name: mpg, Length: 392, dtype: float64




```python
mtcars.mpg # Returns a Series (1 column)
```




    0      18.0
    1      15.0
    2      18.0
    3      16.0
    4      17.0
           ... 
    393    27.0
    394    44.0
    395    32.0
    396    28.0
    397    31.0
    Name: mpg, Length: 392, dtype: float64




```python
mtcars[['mpg', 'horsepower']] # Returns a DataFrame (multiple columns)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>horsepower</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>130.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>165.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>150.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>150.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>140.0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>393</th>
      <td>27.0</td>
      <td>86.0</td>
    </tr>
    <tr>
      <th>394</th>
      <td>44.0</td>
      <td>52.0</td>
    </tr>
    <tr>
      <th>395</th>
      <td>32.0</td>
      <td>84.0</td>
    </tr>
    <tr>
      <th>396</th>
      <td>28.0</td>
      <td>79.0</td>
    </tr>
    <tr>
      <th>397</th>
      <td>31.0</td>
      <td>82.0</td>
    </tr>
  </tbody>
</table>
<p>392 rows × 2 columns</p>
</div>



**Purpose**: Access specific data fields

**Importance**: Focus only on relevant variables for analysis or cleaning

### 8. Selecting only Rows is using `loc` and `iloc`

The Pandas offers .loc[] and .iloc[] methods for data slicing.

- The **.loc[] method is a label based method** that means it takes names or labels of the index when taking the slices, 
- **.iloc[] method is based on the index's position**. It behaves like a regular slicing where we just have to indicate the positional index number and simply get the appropriate slice.



```python
mtcars.iloc[0] # First row (by index position)
```




    mpg                                  18.0
    cylinders                               8
    displacement                        307.0
    horsepower                          130.0
    weight                               3504
    acceleration                         12.0
    model_year                             70
    origin                                usa
    name            chevrolet chevelle malibu
    Name: 0, dtype: object




```python
mtcars.iloc[1:4] # Row 2 to 4
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
    </tr>
  </tbody>
</table>
</div>




```python
mtcars.loc[0] # First row (by label, same as index if default)
```




    mpg                                  18.0
    cylinders                               8
    displacement                        307.0
    horsepower                          130.0
    weight                               3504
    acceleration                         12.0
    model_year                             70
    origin                                usa
    name            chevrolet chevelle malibu
    Name: 0, dtype: object



**Purpose**: Retrieve specific data samples

**Importance**: Useful for data checks, subsetting, and iteration

### 9. Selecting rows and columns using `loc` and `iloc`

#### `loc`


```python
# display records from row 10 to row 16 from mpg columns
mtcars.loc[9:15,"mpg"] # 9 will be row 10 and 15 will be row 16
```




    9     15.0
    10    15.0
    11    14.0
    12    15.0
    13    14.0
    14    24.0
    15    22.0
    Name: mpg, dtype: float64




```python
#see 1st 7 records from mpg to qsec column
mtcars.loc[:6,"mpg":"cylinders"]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>cylinders</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
    </tr>
    <tr>
      <th>5</th>
      <td>15.0</td>
      <td>8</td>
    </tr>
    <tr>
      <th>6</th>
      <td>14.0</td>
      <td>8</td>
    </tr>
  </tbody>
</table>
</div>



#### `iloc`


```python
mtcars.iloc[0:5,4] # row 1 to 5 and column weight index position 4
```




    0    3504
    1    3693
    2    3436
    3    3433
    4    3449
    Name: weight, dtype: int64




```python
mtcars.iloc[0:10,4:6] # row 1 to 5 and column index position 4 and 5
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>weight</th>
      <th>acceleration</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>3504</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>3693</td>
      <td>11.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3436</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3433</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3449</td>
      <td>10.5</td>
    </tr>
    <tr>
      <th>5</th>
      <td>4341</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>4354</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>4312</td>
      <td>8.5</td>
    </tr>
    <tr>
      <th>8</th>
      <td>4425</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>3850</td>
      <td>8.5</td>
    </tr>
  </tbody>
</table>
</div>



### 10. Conditional Filtering


```python
mtcars[mtcars['mpg'] > 30] # selecting cars having mpg greate than 30
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>53</th>
      <td>31.0</td>
      <td>4</td>
      <td>71.0</td>
      <td>65.0</td>
      <td>1773</td>
      <td>19.0</td>
      <td>71</td>
      <td>japan</td>
      <td>toyota corolla 1200</td>
    </tr>
    <tr>
      <th>54</th>
      <td>35.0</td>
      <td>4</td>
      <td>72.0</td>
      <td>69.0</td>
      <td>1613</td>
      <td>18.0</td>
      <td>71</td>
      <td>japan</td>
      <td>datsun 1200</td>
    </tr>
    <tr>
      <th>129</th>
      <td>31.0</td>
      <td>4</td>
      <td>79.0</td>
      <td>67.0</td>
      <td>1950</td>
      <td>19.0</td>
      <td>74</td>
      <td>japan</td>
      <td>datsun b210</td>
    </tr>
    <tr>
      <th>131</th>
      <td>32.0</td>
      <td>4</td>
      <td>71.0</td>
      <td>65.0</td>
      <td>1836</td>
      <td>21.0</td>
      <td>74</td>
      <td>japan</td>
      <td>toyota corolla 1200</td>
    </tr>
    <tr>
      <th>144</th>
      <td>31.0</td>
      <td>4</td>
      <td>76.0</td>
      <td>52.0</td>
      <td>1649</td>
      <td>16.5</td>
      <td>74</td>
      <td>japan</td>
      <td>toyota corona</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>390</th>
      <td>32.0</td>
      <td>4</td>
      <td>144.0</td>
      <td>96.0</td>
      <td>2665</td>
      <td>13.9</td>
      <td>82</td>
      <td>japan</td>
      <td>toyota celica gt</td>
    </tr>
    <tr>
      <th>391</th>
      <td>36.0</td>
      <td>4</td>
      <td>135.0</td>
      <td>84.0</td>
      <td>2370</td>
      <td>13.0</td>
      <td>82</td>
      <td>usa</td>
      <td>dodge charger 2.2</td>
    </tr>
    <tr>
      <th>394</th>
      <td>44.0</td>
      <td>4</td>
      <td>97.0</td>
      <td>52.0</td>
      <td>2130</td>
      <td>24.6</td>
      <td>82</td>
      <td>europe</td>
      <td>vw pickup</td>
    </tr>
    <tr>
      <th>395</th>
      <td>32.0</td>
      <td>4</td>
      <td>135.0</td>
      <td>84.0</td>
      <td>2295</td>
      <td>11.6</td>
      <td>82</td>
      <td>usa</td>
      <td>dodge rampage</td>
    </tr>
    <tr>
      <th>397</th>
      <td>31.0</td>
      <td>4</td>
      <td>119.0</td>
      <td>82.0</td>
      <td>2720</td>
      <td>19.4</td>
      <td>82</td>
      <td>usa</td>
      <td>chevy s-10</td>
    </tr>
  </tbody>
</table>
<p>83 rows × 9 columns</p>
</div>




```python
mtcars[(mtcars['mpg'] > 30) & (mtcars['cylinders'] > 4)] # selecting cars having mpg greate than 30 and cylinder greater than 4
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>327</th>
      <td>36.4</td>
      <td>5</td>
      <td>121.0</td>
      <td>67.0</td>
      <td>2950</td>
      <td>19.9</td>
      <td>80</td>
      <td>europe</td>
      <td>audi 5000s (diesel)</td>
    </tr>
    <tr>
      <th>333</th>
      <td>32.7</td>
      <td>6</td>
      <td>168.0</td>
      <td>132.0</td>
      <td>2910</td>
      <td>11.4</td>
      <td>80</td>
      <td>japan</td>
      <td>datsun 280-zx</td>
    </tr>
    <tr>
      <th>360</th>
      <td>30.7</td>
      <td>6</td>
      <td>145.0</td>
      <td>76.0</td>
      <td>3160</td>
      <td>19.6</td>
      <td>81</td>
      <td>europe</td>
      <td>volvo diesel</td>
    </tr>
    <tr>
      <th>387</th>
      <td>38.0</td>
      <td>6</td>
      <td>262.0</td>
      <td>85.0</td>
      <td>3015</td>
      <td>17.0</td>
      <td>82</td>
      <td>usa</td>
      <td>oldsmobile cutlass ciera (diesel)</td>
    </tr>
  </tbody>
</table>
</div>



**Purpose**: Filter rows based on a condition

**Importance**: Quickly explore data subsets (e.g., fuel-efficient cars)

### 11. Creating or Modifying Columns


```python
mtcars['power_to_weight'] = mtcars['horsepower'] / mtcars['weight']
mtcars.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
      <th>power_to_weight</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
      <td>0.037100</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
      <td>0.044679</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
      <td>0.043655</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
      <td>0.043694</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>usa</td>
      <td>ford torino</td>
      <td>0.040591</td>
    </tr>
  </tbody>
</table>
</div>



**Purpose**: Add derived or calculated metrics

**Importance**: Enables feature engineering for better insights or modeling

### 11. Drop Columns or Rows


```python
mtcars.drop('power_to_weight', axis=1, inplace=True) # axis=1 → column
mtcars.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>mpg</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>usa</td>
      <td>ford torino</td>
    </tr>
  </tbody>
</table>
</div>



**Purpose**: Remove irrelevant data

**Importance**: Keeps dataset clean and focused

### 12. Rename Columns


```python
mtcars.rename(columns={'mpg': 'MilesPerGallon'}, inplace=True) # renaming mpg or column
mtcars.head() 
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MilesPerGallon</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>usa</td>
      <td>ford torino</td>
    </tr>
  </tbody>
</table>
</div>



**Purpose**: Make column names more meaningful

**Importance**: Improves readability and documentation

### 13. Missing Values Handling


```python
mtcars.isnull() # to check if missing values are there True means missing values are present
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MilesPerGallon</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>393</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>394</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>395</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>396</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
    <tr>
      <th>397</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>392 rows × 9 columns</p>
</div>




```python
mtcars.isnull().sum() # Count missing values per column
```




    MilesPerGallon    0
    cylinders         0
    displacement      0
    horsepower        0
    weight            0
    acceleration      0
    model_year        0
    origin            0
    name              0
    dtype: int64




```python
mtcars.fillna(0) # Replace all missing values with 0
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MilesPerGallon</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>usa</td>
      <td>ford torino</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>393</th>
      <td>27.0</td>
      <td>4</td>
      <td>140.0</td>
      <td>86.0</td>
      <td>2790</td>
      <td>15.6</td>
      <td>82</td>
      <td>usa</td>
      <td>ford mustang gl</td>
    </tr>
    <tr>
      <th>394</th>
      <td>44.0</td>
      <td>4</td>
      <td>97.0</td>
      <td>52.0</td>
      <td>2130</td>
      <td>24.6</td>
      <td>82</td>
      <td>europe</td>
      <td>vw pickup</td>
    </tr>
    <tr>
      <th>395</th>
      <td>32.0</td>
      <td>4</td>
      <td>135.0</td>
      <td>84.0</td>
      <td>2295</td>
      <td>11.6</td>
      <td>82</td>
      <td>usa</td>
      <td>dodge rampage</td>
    </tr>
    <tr>
      <th>396</th>
      <td>28.0</td>
      <td>4</td>
      <td>120.0</td>
      <td>79.0</td>
      <td>2625</td>
      <td>18.6</td>
      <td>82</td>
      <td>usa</td>
      <td>ford ranger</td>
    </tr>
    <tr>
      <th>397</th>
      <td>31.0</td>
      <td>4</td>
      <td>119.0</td>
      <td>82.0</td>
      <td>2720</td>
      <td>19.4</td>
      <td>82</td>
      <td>usa</td>
      <td>chevy s-10</td>
    </tr>
  </tbody>
</table>
<p>392 rows × 9 columns</p>
</div>




```python
mtcars.dropna() # # Remove rows with missing values
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MilesPerGallon</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>usa</td>
      <td>ford torino</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>393</th>
      <td>27.0</td>
      <td>4</td>
      <td>140.0</td>
      <td>86.0</td>
      <td>2790</td>
      <td>15.6</td>
      <td>82</td>
      <td>usa</td>
      <td>ford mustang gl</td>
    </tr>
    <tr>
      <th>394</th>
      <td>44.0</td>
      <td>4</td>
      <td>97.0</td>
      <td>52.0</td>
      <td>2130</td>
      <td>24.6</td>
      <td>82</td>
      <td>europe</td>
      <td>vw pickup</td>
    </tr>
    <tr>
      <th>395</th>
      <td>32.0</td>
      <td>4</td>
      <td>135.0</td>
      <td>84.0</td>
      <td>2295</td>
      <td>11.6</td>
      <td>82</td>
      <td>usa</td>
      <td>dodge rampage</td>
    </tr>
    <tr>
      <th>396</th>
      <td>28.0</td>
      <td>4</td>
      <td>120.0</td>
      <td>79.0</td>
      <td>2625</td>
      <td>18.6</td>
      <td>82</td>
      <td>usa</td>
      <td>ford ranger</td>
    </tr>
    <tr>
      <th>397</th>
      <td>31.0</td>
      <td>4</td>
      <td>119.0</td>
      <td>82.0</td>
      <td>2720</td>
      <td>19.4</td>
      <td>82</td>
      <td>usa</td>
      <td>chevy s-10</td>
    </tr>
  </tbody>
</table>
<p>392 rows × 9 columns</p>
</div>



**Purpose**: Identify and manage gaps in data

**Importance**: Essential for ensuring accuracy during analysis or modeling

### 14. GroupBy and Aggregation


```python
mtcars.groupby('cylinders')['MilesPerGallon'].mean() # calculate avg mpg for each cylinder
```




    cylinders
    3    20.550000
    4    29.283920
    5    27.366667
    6    19.973494
    8    14.963107
    Name: MilesPerGallon, dtype: float64



**Purpose**: Group data and compute summary (like mean)

**Importance**: Supports analysis by categories or groups

### 15. Value Counts


```python
mtcars['origin'].value_counts()
```




    usa       245
    japan      79
    europe     68
    Name: origin, dtype: int64



**Purpose**: Count how many values are in each category

**Importance**: Helps understand class balance (e.g., origin of cars)

### 16. Sorting and Ranking


```python
mtcars_sorted = mtcars.sort_values('horsepower', ascending=True)
mtcars_sorted.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MilesPerGallon</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>19</th>
      <td>26.0</td>
      <td>4</td>
      <td>97.0</td>
      <td>46.0</td>
      <td>1835</td>
      <td>20.5</td>
      <td>70</td>
      <td>europe</td>
      <td>volkswagen 1131 deluxe sedan</td>
    </tr>
    <tr>
      <th>102</th>
      <td>26.0</td>
      <td>4</td>
      <td>97.0</td>
      <td>46.0</td>
      <td>1950</td>
      <td>21.0</td>
      <td>73</td>
      <td>europe</td>
      <td>volkswagen super beetle</td>
    </tr>
    <tr>
      <th>326</th>
      <td>43.4</td>
      <td>4</td>
      <td>90.0</td>
      <td>48.0</td>
      <td>2335</td>
      <td>23.7</td>
      <td>80</td>
      <td>europe</td>
      <td>vw dasher (diesel)</td>
    </tr>
    <tr>
      <th>325</th>
      <td>44.3</td>
      <td>4</td>
      <td>90.0</td>
      <td>48.0</td>
      <td>2085</td>
      <td>21.7</td>
      <td>80</td>
      <td>europe</td>
      <td>vw rabbit c (diesel)</td>
    </tr>
    <tr>
      <th>244</th>
      <td>43.1</td>
      <td>4</td>
      <td>90.0</td>
      <td>48.0</td>
      <td>1985</td>
      <td>21.5</td>
      <td>78</td>
      <td>europe</td>
      <td>volkswagen rabbit custom diesel</td>
    </tr>
  </tbody>
</table>
</div>




```python
mtcars['mpg_rank'] = mtcars['MilesPerGallon'].rank()
mtcars.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MilesPerGallon</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
      <th>mpg_rank</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
      <td>116.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
      <td>61.5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
      <td>116.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
      <td>81.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>usa</td>
      <td>ford torino</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>15.0</td>
      <td>8</td>
      <td>429.0</td>
      <td>198.0</td>
      <td>4341</td>
      <td>10.0</td>
      <td>70</td>
      <td>usa</td>
      <td>ford galaxie 500</td>
      <td>61.5</td>
    </tr>
    <tr>
      <th>6</th>
      <td>14.0</td>
      <td>8</td>
      <td>454.0</td>
      <td>220.0</td>
      <td>4354</td>
      <td>9.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet impala</td>
      <td>43.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>14.0</td>
      <td>8</td>
      <td>440.0</td>
      <td>215.0</td>
      <td>4312</td>
      <td>8.5</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth fury iii</td>
      <td>43.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>14.0</td>
      <td>8</td>
      <td>455.0</td>
      <td>225.0</td>
      <td>4425</td>
      <td>10.0</td>
      <td>70</td>
      <td>usa</td>
      <td>pontiac catalina</td>
      <td>43.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>15.0</td>
      <td>8</td>
      <td>390.0</td>
      <td>190.0</td>
      <td>3850</td>
      <td>8.5</td>
      <td>70</td>
      <td>usa</td>
      <td>amc ambassador dpl</td>
      <td>61.5</td>
    </tr>
  </tbody>
</table>
</div>



**Purpose**: Order rows by value or importance

**Importance**: Useful for leaderboards, top-N, or low-performance filtering

### 17. Pivot Tables


```python
mtcars.pivot_table(index='cylinders', values='MilesPerGallon', aggfunc='mean')
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MilesPerGallon</th>
    </tr>
    <tr>
      <th>cylinders</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>20.550000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>29.283920</td>
    </tr>
    <tr>
      <th>5</th>
      <td>27.366667</td>
    </tr>
    <tr>
      <th>6</th>
      <td>19.973494</td>
    </tr>
    <tr>
      <th>8</th>
      <td>14.963107</td>
    </tr>
  </tbody>
</table>
</div>



**Purpose**: Summarize data using statistics

**Importance**: Like Excel pivot tables, great for summary reports

### 18. Mapping and replacing
These two functions are element-wise operations used primarily for value transformation, label conversion, and data cleaning.


```python
origin_map = {'usa': 'United States', 'japan': 'Japan', 'europe': 'Europe'}
mtcars['origin_full'] = mtcars['origin'].map(origin_map)
mtcars.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MilesPerGallon</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
      <th>mpg_rank</th>
      <th>origin_full</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>8</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
      <td>116.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>8</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
      <td>61.5</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>8</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
      <td>116.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>8</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
      <td>81.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>8</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>usa</td>
      <td>ford torino</td>
      <td>96.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>5</th>
      <td>15.0</td>
      <td>8</td>
      <td>429.0</td>
      <td>198.0</td>
      <td>4341</td>
      <td>10.0</td>
      <td>70</td>
      <td>usa</td>
      <td>ford galaxie 500</td>
      <td>61.5</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>6</th>
      <td>14.0</td>
      <td>8</td>
      <td>454.0</td>
      <td>220.0</td>
      <td>4354</td>
      <td>9.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet impala</td>
      <td>43.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>7</th>
      <td>14.0</td>
      <td>8</td>
      <td>440.0</td>
      <td>215.0</td>
      <td>4312</td>
      <td>8.5</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth fury iii</td>
      <td>43.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>8</th>
      <td>14.0</td>
      <td>8</td>
      <td>455.0</td>
      <td>225.0</td>
      <td>4425</td>
      <td>10.0</td>
      <td>70</td>
      <td>usa</td>
      <td>pontiac catalina</td>
      <td>43.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>9</th>
      <td>15.0</td>
      <td>8</td>
      <td>390.0</td>
      <td>190.0</td>
      <td>3850</td>
      <td>8.5</td>
      <td>70</td>
      <td>usa</td>
      <td>amc ambassador dpl</td>
      <td>61.5</td>
      <td>United States</td>
    </tr>
  </tbody>
</table>
</div>




```python
mtcars['cylinders'].replace({4: 'Four', 6: 'Six', 8: 'Eight'}, inplace=True)
mtcars.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MilesPerGallon</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
      <th>mpg_rank</th>
      <th>origin_full</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>Eight</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
      <td>116.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>Eight</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
      <td>61.5</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>Eight</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
      <td>116.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>Eight</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
      <td>81.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>Eight</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>usa</td>
      <td>ford torino</td>
      <td>96.0</td>
      <td>United States</td>
    </tr>
  </tbody>
</table>
</div>



**Purpose**:
* Apply a function, dictionary, or another Series to each element in a Pandas Series (i.e., one column).
* Often used for value transformation, conditional labeling, or converting codes into labels.

**Importance**:
* Efficient for cleaning or annotating categorical values.
* Useful for converting values dynamically, such as turning numbers into labels (e.g., 0 → "No", 1 → "Yes").
* Supports custom logic with lambda or user-defined functions.

### 19. Unique values in a column


```python
mtcars.cylinders.unique()
```




    array(['Eight', 'Four', 'Six', 3, 5], dtype=object)



**Purpose**: To find unique values in a column

**Importance**: Helps to find discrepency in a column

### 20. Exporting & Importing


```python
mtcars.to_csv('mtcars_cleaned.csv', index=False)
df = pd.read_csv('mtcars_cleaned.csv')
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MilesPerGallon</th>
      <th>cylinders</th>
      <th>displacement</th>
      <th>horsepower</th>
      <th>weight</th>
      <th>acceleration</th>
      <th>model_year</th>
      <th>origin</th>
      <th>name</th>
      <th>mpg_rank</th>
      <th>origin_full</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>18.0</td>
      <td>Eight</td>
      <td>307.0</td>
      <td>130.0</td>
      <td>3504</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>chevrolet chevelle malibu</td>
      <td>116.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>1</th>
      <td>15.0</td>
      <td>Eight</td>
      <td>350.0</td>
      <td>165.0</td>
      <td>3693</td>
      <td>11.5</td>
      <td>70</td>
      <td>usa</td>
      <td>buick skylark 320</td>
      <td>61.5</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18.0</td>
      <td>Eight</td>
      <td>318.0</td>
      <td>150.0</td>
      <td>3436</td>
      <td>11.0</td>
      <td>70</td>
      <td>usa</td>
      <td>plymouth satellite</td>
      <td>116.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>3</th>
      <td>16.0</td>
      <td>Eight</td>
      <td>304.0</td>
      <td>150.0</td>
      <td>3433</td>
      <td>12.0</td>
      <td>70</td>
      <td>usa</td>
      <td>amc rebel sst</td>
      <td>81.0</td>
      <td>United States</td>
    </tr>
    <tr>
      <th>4</th>
      <td>17.0</td>
      <td>Eight</td>
      <td>302.0</td>
      <td>140.0</td>
      <td>3449</td>
      <td>10.5</td>
      <td>70</td>
      <td>usa</td>
      <td>ford torino</td>
      <td>96.0</td>
      <td>United States</td>
    </tr>
  </tbody>
</table>
</div>



**Purpose**: Share or store data externally

**Importance**: Enables saving analysis or sending it to collaborators


```python

```
