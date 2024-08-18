
![Orange Bright Colorful Modern Abstract Money Finance YouTube Thumbnail ](https://github.com/user-attachments/assets/344fe9c4-bde4-490a-b78b-6cb0b715f8eb)



## Load the Necessary Libraries
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

## Load the Data
```python
df = pd.read_csv(r'\Users\TOH TICKETING\Downloads\SampleSuperstore.csv')
```

## Basic Data Inspection
```python
df.head()
```





    

<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ship Mode</th>
      <th>Segment</th>
      <th>Country</th>
      <th>City</th>
      <th>State</th>
      <th>Postal Code</th>
      <th>Region</th>
      <th>Category</th>
      <th>Sub-Category</th>
      <th>Sales</th>
      <th>Quantity</th>
      <th>Discount</th>
      <th>Profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Bookcases</td>
      <td>261.9600</td>
      <td>2</td>
      <td>0.00</td>
      <td>41.9136</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>731.9400</td>
      <td>3</td>
      <td>0.00</td>
      <td>219.5820</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Second Class</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90036</td>
      <td>West</td>
      <td>Office Supplies</td>
      <td>Labels</td>
      <td>14.6200</td>
      <td>2</td>
      <td>0.00</td>
      <td>6.8714</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Tables</td>
      <td>957.5775</td>
      <td>5</td>
      <td>0.45</td>
      <td>-383.0310</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311</td>
      <td>South</td>
      <td>Office Supplies</td>
      <td>Storage</td>
      <td>22.3680</td>
      <td>2</td>
      <td>0.20</td>
      <td>2.5164</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 9994 entries, 0 to 9993
    Data columns (total 13 columns):
     #   Column        Non-Null Count  Dtype  
    ---  ------        --------------  -----  
     0   Ship Mode     9994 non-null   object 
     1   Segment       9994 non-null   object 
     2   Country       9994 non-null   object 
     3   City          9994 non-null   object 
     4   State         9994 non-null   object 
     5   Postal Code   9994 non-null   int64  
     6   Region        9994 non-null   object 
     7   Category      9994 non-null   object 
     8   Sub-Category  9994 non-null   object 
     9   Sales         9994 non-null   float64
     10  Quantity      9994 non-null   int64  
     11  Discount      9994 non-null   float64
     12  Profit        9994 non-null   float64
    dtypes: float64(3), int64(2), object(8)
    memory usage: 1015.1+ KB
    
## Data Cleaning

```python
df.isnull().sum()
```




    Ship Mode       0
    Segment         0
    Country         0
    City            0
    State           0
    Postal Code     0
    Region          0
    Category        0
    Sub-Category    0
    Sales           0
    Quantity        0
    Discount        0
    Profit          0
    dtype: int64




```python
df.duplicated().sum()
```




    np.int64(17)




```python
df.dropna()
```




  
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ship Mode</th>
      <th>Segment</th>
      <th>Country</th>
      <th>City</th>
      <th>State</th>
      <th>Postal Code</th>
      <th>Region</th>
      <th>Category</th>
      <th>Sub-Category</th>
      <th>Sales</th>
      <th>Quantity</th>
      <th>Discount</th>
      <th>Profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Bookcases</td>
      <td>261.9600</td>
      <td>2</td>
      <td>0.00</td>
      <td>41.9136</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>731.9400</td>
      <td>3</td>
      <td>0.00</td>
      <td>219.5820</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Second Class</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90036</td>
      <td>West</td>
      <td>Office Supplies</td>
      <td>Labels</td>
      <td>14.6200</td>
      <td>2</td>
      <td>0.00</td>
      <td>6.8714</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Tables</td>
      <td>957.5775</td>
      <td>5</td>
      <td>0.45</td>
      <td>-383.0310</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311</td>
      <td>South</td>
      <td>Office Supplies</td>
      <td>Storage</td>
      <td>22.3680</td>
      <td>2</td>
      <td>0.20</td>
      <td>2.5164</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9989</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Miami</td>
      <td>Florida</td>
      <td>33180</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Furnishings</td>
      <td>25.2480</td>
      <td>3</td>
      <td>0.20</td>
      <td>4.1028</td>
    </tr>
    <tr>
      <th>9990</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Costa Mesa</td>
      <td>California</td>
      <td>92627</td>
      <td>West</td>
      <td>Furniture</td>
      <td>Furnishings</td>
      <td>91.9600</td>
      <td>2</td>
      <td>0.00</td>
      <td>15.6332</td>
    </tr>
    <tr>
      <th>9991</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Costa Mesa</td>
      <td>California</td>
      <td>92627</td>
      <td>West</td>
      <td>Technology</td>
      <td>Phones</td>
      <td>258.5760</td>
      <td>2</td>
      <td>0.20</td>
      <td>19.3932</td>
    </tr>
    <tr>
      <th>9992</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Costa Mesa</td>
      <td>California</td>
      <td>92627</td>
      <td>West</td>
      <td>Office Supplies</td>
      <td>Paper</td>
      <td>29.6000</td>
      <td>4</td>
      <td>0.00</td>
      <td>13.3200</td>
    </tr>
    <tr>
      <th>9993</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Westminster</td>
      <td>California</td>
      <td>92683</td>
      <td>West</td>
      <td>Office Supplies</td>
      <td>Appliances</td>
      <td>243.1600</td>
      <td>2</td>
      <td>0.00</td>
      <td>72.9480</td>
    </tr>
  </tbody>
</table>
<p>9994 rows × 13 columns</p>
</div>




```python
df.drop_duplicates()
```





<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ship Mode</th>
      <th>Segment</th>
      <th>Country</th>
      <th>City</th>
      <th>State</th>
      <th>Postal Code</th>
      <th>Region</th>
      <th>Category</th>
      <th>Sub-Category</th>
      <th>Sales</th>
      <th>Quantity</th>
      <th>Discount</th>
      <th>Profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Bookcases</td>
      <td>261.9600</td>
      <td>2</td>
      <td>0.00</td>
      <td>41.9136</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>731.9400</td>
      <td>3</td>
      <td>0.00</td>
      <td>219.5820</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Second Class</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90036</td>
      <td>West</td>
      <td>Office Supplies</td>
      <td>Labels</td>
      <td>14.6200</td>
      <td>2</td>
      <td>0.00</td>
      <td>6.8714</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Tables</td>
      <td>957.5775</td>
      <td>5</td>
      <td>0.45</td>
      <td>-383.0310</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311</td>
      <td>South</td>
      <td>Office Supplies</td>
      <td>Storage</td>
      <td>22.3680</td>
      <td>2</td>
      <td>0.20</td>
      <td>2.5164</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9989</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Miami</td>
      <td>Florida</td>
      <td>33180</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Furnishings</td>
      <td>25.2480</td>
      <td>3</td>
      <td>0.20</td>
      <td>4.1028</td>
    </tr>
    <tr>
      <th>9990</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Costa Mesa</td>
      <td>California</td>
      <td>92627</td>
      <td>West</td>
      <td>Furniture</td>
      <td>Furnishings</td>
      <td>91.9600</td>
      <td>2</td>
      <td>0.00</td>
      <td>15.6332</td>
    </tr>
    <tr>
      <th>9991</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Costa Mesa</td>
      <td>California</td>
      <td>92627</td>
      <td>West</td>
      <td>Technology</td>
      <td>Phones</td>
      <td>258.5760</td>
      <td>2</td>
      <td>0.20</td>
      <td>19.3932</td>
    </tr>
    <tr>
      <th>9992</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Costa Mesa</td>
      <td>California</td>
      <td>92627</td>
      <td>West</td>
      <td>Office Supplies</td>
      <td>Paper</td>
      <td>29.6000</td>
      <td>4</td>
      <td>0.00</td>
      <td>13.3200</td>
    </tr>
    <tr>
      <th>9993</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Westminster</td>
      <td>California</td>
      <td>92683</td>
      <td>West</td>
      <td>Office Supplies</td>
      <td>Appliances</td>
      <td>243.1600</td>
      <td>2</td>
      <td>0.00</td>
      <td>72.9480</td>
    </tr>
  </tbody>
</table>
<p>9977 rows × 13 columns</p>
</div>




```python
df.fillna('mean') 
```




<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ship Mode</th>
      <th>Segment</th>
      <th>Country</th>
      <th>City</th>
      <th>State</th>
      <th>Postal Code</th>
      <th>Region</th>
      <th>Category</th>
      <th>Sub-Category</th>
      <th>Sales</th>
      <th>Quantity</th>
      <th>Discount</th>
      <th>Profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Bookcases</td>
      <td>261.9600</td>
      <td>2</td>
      <td>0.00</td>
      <td>41.9136</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Henderson</td>
      <td>Kentucky</td>
      <td>42420</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Chairs</td>
      <td>731.9400</td>
      <td>3</td>
      <td>0.00</td>
      <td>219.5820</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Second Class</td>
      <td>Corporate</td>
      <td>United States</td>
      <td>Los Angeles</td>
      <td>California</td>
      <td>90036</td>
      <td>West</td>
      <td>Office Supplies</td>
      <td>Labels</td>
      <td>14.6200</td>
      <td>2</td>
      <td>0.00</td>
      <td>6.8714</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Tables</td>
      <td>957.5775</td>
      <td>5</td>
      <td>0.45</td>
      <td>-383.0310</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Fort Lauderdale</td>
      <td>Florida</td>
      <td>33311</td>
      <td>South</td>
      <td>Office Supplies</td>
      <td>Storage</td>
      <td>22.3680</td>
      <td>2</td>
      <td>0.20</td>
      <td>2.5164</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9989</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Miami</td>
      <td>Florida</td>
      <td>33180</td>
      <td>South</td>
      <td>Furniture</td>
      <td>Furnishings</td>
      <td>25.2480</td>
      <td>3</td>
      <td>0.20</td>
      <td>4.1028</td>
    </tr>
    <tr>
      <th>9990</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Costa Mesa</td>
      <td>California</td>
      <td>92627</td>
      <td>West</td>
      <td>Furniture</td>
      <td>Furnishings</td>
      <td>91.9600</td>
      <td>2</td>
      <td>0.00</td>
      <td>15.6332</td>
    </tr>
    <tr>
      <th>9991</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Costa Mesa</td>
      <td>California</td>
      <td>92627</td>
      <td>West</td>
      <td>Technology</td>
      <td>Phones</td>
      <td>258.5760</td>
      <td>2</td>
      <td>0.20</td>
      <td>19.3932</td>
    </tr>
    <tr>
      <th>9992</th>
      <td>Standard Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Costa Mesa</td>
      <td>California</td>
      <td>92627</td>
      <td>West</td>
      <td>Office Supplies</td>
      <td>Paper</td>
      <td>29.6000</td>
      <td>4</td>
      <td>0.00</td>
      <td>13.3200</td>
    </tr>
    <tr>
      <th>9993</th>
      <td>Second Class</td>
      <td>Consumer</td>
      <td>United States</td>
      <td>Westminster</td>
      <td>California</td>
      <td>92683</td>
      <td>West</td>
      <td>Office Supplies</td>
      <td>Appliances</td>
      <td>243.1600</td>
      <td>2</td>
      <td>0.00</td>
      <td>72.9480</td>
    </tr>
  </tbody>
</table>
<p>9994 rows × 13 columns</p>
</div>




```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 9994 entries, 0 to 9993
    Data columns (total 13 columns):
     #   Column        Non-Null Count  Dtype  
    ---  ------        --------------  -----  
     0   Ship Mode     9994 non-null   object 
     1   Segment       9994 non-null   object 
     2   Country       9994 non-null   object 
     3   City          9994 non-null   object 
     4   State         9994 non-null   object 
     5   Postal Code   9994 non-null   int64  
     6   Region        9994 non-null   object 
     7   Category      9994 non-null   object 
     8   Sub-Category  9994 non-null   object 
     9   Sales         9994 non-null   float64
     10  Quantity      9994 non-null   int64  
     11  Discount      9994 non-null   float64
     12  Profit        9994 non-null   float64
    dtypes: float64(3), int64(2), object(8)
    memory usage: 1015.1+ KB
    

## univarite analysis

### Analyze individual variables to understand their distributions.

```python
# Sales distribution
plt.figure(figsize=(10, 6))
sns.histplot(df['Sales'], bins=30, kde=True)
plt.title('Distribution of Sales')
plt.xlabel('Sales')
plt.ylabel('Frequency')
plt.show()
```
![download](https://github.com/user-attachments/assets/14cdbb66-b379-4849-9ffa-2c4a78fdd99a)



    

    



```python
# Profit distribution
plt.figure(figsize=(10, 6))
sns.histplot(df['Profit'], bins=30, kde=True)
plt.title('Distribution of Profit')
plt.xlabel('Profit')
plt.ylabel('Frequency')
plt.show()

```
![download](https://github.com/user-attachments/assets/b4cc1585-1147-41f2-a09e-cb199766b3b4)


  



```python

# Quantity distribution
plt.figure(figsize=(10, 6))
sns.histplot(df['Quantity'], bins=30, kde=True)
plt.title('Distribution of Quantity')
plt.xlabel('Quantity')
plt.ylabel('Frequency')
plt.show()



```

![download](https://github.com/user-attachments/assets/86074082-81d9-404c-b5ce-abd063c60cf4)

    

    



```python
# Count of categories
plt.figure(figsize=(12, 6))
sns.countplot(data=df, x='Category')
plt.title('Count of Categories')
plt.xlabel('Category')
plt.ylabel('Count')
plt.show()
```

![download](https://github.com/user-attachments/assets/7b0aa5f6-6345-46e8-8fd2-622b9c7e91db)

    



    


## Bivariate analysis

### Analyze the relationships between pairs of variables.
```python
plt.figure(figsize=(10,5))
sns.scatterplot(data=df,x='Sales',y='Profit')
plt.title('Sales vs. Profit')
plt.xlabel('Sales')
plt.ylabel('Profit')
plt.show()
```

![download](https://github.com/user-attachments/assets/1ae3963b-13c7-4b5e-96f2-e86b1e873347)

    

    



```python
#sales by category
plt.figure(figsize=(7,5))
sns.boxplot(data=df,x='Category',y='Sales')
plt.title('sales by category')
plt.xlabel('Sales')
plt.ylabel('Category')
plt.show()
```

![download](https://github.com/user-attachments/assets/61ef9481-4b78-46c8-b28b-82a776803833)

    

    

```python
#sales by region

plt.figure(figsize=(7,5))
sns.boxplot(data=df,x='Sales',y='Region')
plt.title('sales by region')
plt.xlabel('Sales')
plt.ylabel('Region')
plt.show()

![download](https://github.com/user-attachments/assets/f911e188-5dcf-4b08-97e1-7336a1fbc0b9)

```
## Multivariate analysis

### Explore the relationships among multiple variables.

```python
# Select only numeric columns
numeric_df = df.select_dtypes(include=['number'])

print("\nNumeric DataFrame:")
print(numeric_df)


```

    
    Numeric DataFrame:
          Postal Code     Sales  Quantity  Discount    Profit
    0           42420  261.9600         2      0.00   41.9136
    1           42420  731.9400         3      0.00  219.5820
    2           90036   14.6200         2      0.00    6.8714
    3           33311  957.5775         5      0.45 -383.0310
    4           33311   22.3680         2      0.20    2.5164
    ...           ...       ...       ...       ...       ...
    9989        33180   25.2480         3      0.20    4.1028
    9990        92627   91.9600         2      0.00   15.6332
    9991        92627  258.5760         2      0.20   19.3932
    9992        92627   29.6000         4      0.00   13.3200
    9993        92683  243.1600         2      0.00   72.9480
    
    [9994 rows x 5 columns]
    


```python
# Generate a heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(numeric_df.corr(), annot=True, cmap='coolwarm')
plt.title('correlation Heatmap')
plt.show()

```


    

![download](https://github.com/user-attachments/assets/c01a253d-1274-4d0f-ab9a-40cbf33ee75c)
    



```python
# Pairplot for selected variables
sns.pairplot(df[['Sales', 'Profit', 'Quantity', 'Discount']])
plt.show()
```


    

![download](https://github.com/user-attachments/assets/d09eeac4-51ae-4831-b2d5-c956897dad39)
    



```python
# Sales by Category and Region
plt.figure(figsize=(14, 8))
sns.barplot(data=df, x='Category', y='Sales', hue='Region')
plt.title('Sales by Category and Region')
plt.xlabel('Category')
plt.ylabel('Sales')
plt.show()
```


    

![download](https://github.com/user-attachments/assets/3b483aa1-59d1-404c-b6ab-1f0a04e251e6)
    



