---
title: Pandas Basics by Practice
date: 2019-02-12
permalink: /python-pandas-basics-by-practice-data-science-2019-02.html
header:
categories:
  - Data Science
tags:
  - Python
  - ML
---
This is an overview of very basic pandas functions by using notebook below. One can get a basic understanding of pandas and then can move ahead to more advanced courses. The Python notebook is available [here](https://github.com/pparashar/utils/blob/master/notebooks/learn-pandas-basic-practice.ipynb).




```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Make the graphs a bit prettier, and bigger
#pd.set_option('display.mpl_style', 'default')

# This is necessary to show lots of columns in pandas 0.12. 
# Not necessary in pandas 0.13.
pd.set_option('display.width', 5000) 
pd.set_option('display.max_columns', 60)

plt.rcParams['figure.figsize'] = (15, 5)
```


```python
h = [1,2,3,4,5]
l = [10,20,30,40,50]
```


```python
he = np.array(h)
le = np.array(l+[20,30])
```


```python
le = np.resize(le, he.shape)
le*he
```




    array([ 10,  40,  90, 160, 250])




```python
dict = {"country": ["Brazil", "Russia", "India", "China", "South Africa"],
       "capital": ["Brasilia", "Moscow", "New Dehli", "Beijing", "Pretoria"],
       "area": [8.516, 17.10, 3.286, 9.597, 1.221],
       "population": [200.4, 143.5, 1252, 1357, 52.98] }


brics = pd.DataFrame(dict)
print(brics)
```

         area    capital       country  population
    0   8.516   Brasilia        Brazil      200.40
    1  17.100     Moscow        Russia      143.50
    2   3.286  New Dehli         India     1252.00
    3   9.597    Beijing         China     1357.00
    4   1.221   Pretoria  South Africa       52.98



```python
brics[ brics['area']>7]
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
      <th>area</th>
      <th>capital</th>
      <th>country</th>
      <th>population</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>8.516</td>
      <td>Brasilia</td>
      <td>Brazil</td>
      <td>200.4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>17.100</td>
      <td>Moscow</td>
      <td>Russia</td>
      <td>143.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9.597</td>
      <td>Beijing</td>
      <td>China</td>
      <td>1357.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
brics[0:2]
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
      <th>area</th>
      <th>capital</th>
      <th>country</th>
      <th>population</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>8.516</td>
      <td>Brasilia</td>
      <td>Brazil</td>
      <td>200.4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>17.100</td>
      <td>Moscow</td>
      <td>Russia</td>
      <td>143.5</td>
    </tr>
  </tbody>
</table>
</div>




```python
brics.loc[[2,4]]
brics.iloc[[2,4]]
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
      <th>area</th>
      <th>capital</th>
      <th>country</th>
      <th>population</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>3.286</td>
      <td>New Dehli</td>
      <td>India</td>
      <td>1252.00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.221</td>
      <td>Pretoria</td>
      <td>South Africa</td>
      <td>52.98</td>
    </tr>
  </tbody>
</table>
</div>




```python
brics.sort_values('area', ascending=False)
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
      <th>area</th>
      <th>capital</th>
      <th>country</th>
      <th>population</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>17.100</td>
      <td>Moscow</td>
      <td>Russia</td>
      <td>143.50</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9.597</td>
      <td>Beijing</td>
      <td>China</td>
      <td>1357.00</td>
    </tr>
    <tr>
      <th>0</th>
      <td>8.516</td>
      <td>Brasilia</td>
      <td>Brazil</td>
      <td>200.40</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.286</td>
      <td>New Dehli</td>
      <td>India</td>
      <td>1252.00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.221</td>
      <td>Pretoria</td>
      <td>South Africa</td>
      <td>52.98</td>
    </tr>
  </tbody>
</table>
</div>




```python
brics.T.sort_values('area', 1)
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
      <th>4</th>
      <th>2</th>
      <th>0</th>
      <th>3</th>
      <th>1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>area</th>
      <td>1.221</td>
      <td>3.286</td>
      <td>8.516</td>
      <td>9.597</td>
      <td>17.1</td>
    </tr>
    <tr>
      <th>capital</th>
      <td>Pretoria</td>
      <td>New Dehli</td>
      <td>Brasilia</td>
      <td>Beijing</td>
      <td>Moscow</td>
    </tr>
    <tr>
      <th>country</th>
      <td>South Africa</td>
      <td>India</td>
      <td>Brazil</td>
      <td>China</td>
      <td>Russia</td>
    </tr>
    <tr>
      <th>population</th>
      <td>52.98</td>
      <td>1252</td>
      <td>200.4</td>
      <td>1357</td>
      <td>143.5</td>
    </tr>
  </tbody>
</table>
</div>




```python
a = [a/2 for a in brics['area'] if a > 4]
a
```




    [4.258, 8.55, 4.7985]




```python
# Data from https://www.kaggle.com/c/bluebook-for-bulldozers/data 
df = pd.read_csv('Bulldozer-train-data.csv', low_memory=False)
```


```python
df[df['SalePrice'].isna()]
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
      <th>SalesID</th>
      <th>SalePrice</th>
      <th>MachineID</th>
      <th>ModelID</th>
      <th>datasource</th>
      <th>auctioneerID</th>
      <th>YearMade</th>
      <th>MachineHoursCurrentMeter</th>
      <th>UsageBand</th>
      <th>saledate</th>
      <th>fiModelDesc</th>
      <th>fiBaseModel</th>
      <th>fiSecondaryDesc</th>
      <th>fiModelSeries</th>
      <th>fiModelDescriptor</th>
      <th>ProductSize</th>
      <th>fiProductClassDesc</th>
      <th>state</th>
      <th>ProductGroup</th>
      <th>ProductGroupDesc</th>
      <th>Drive_System</th>
      <th>Enclosure</th>
      <th>Forks</th>
      <th>Pad_Type</th>
      <th>Ride_Control</th>
      <th>Stick</th>
      <th>Transmission</th>
      <th>Turbocharged</th>
      <th>Blade_Extension</th>
      <th>Blade_Width</th>
      <th>Enclosure_Type</th>
      <th>Engine_Horsepower</th>
      <th>Hydraulics</th>
      <th>Pushblock</th>
      <th>Ripper</th>
      <th>Scarifier</th>
      <th>Tip_Control</th>
      <th>Tire_Size</th>
      <th>Coupler</th>
      <th>Coupler_System</th>
      <th>Grouser_Tracks</th>
      <th>Hydraulics_Flow</th>
      <th>Track_Type</th>
      <th>Undercarriage_Pad_Width</th>
      <th>Stick_Length</th>
      <th>Thumb</th>
      <th>Pattern_Changer</th>
      <th>Grouser_Type</th>
      <th>Backhoe_Mounting</th>
      <th>Blade_Type</th>
      <th>Travel_Controls</th>
      <th>Differential_Type</th>
      <th>Steering_Controls</th>
    </tr>
  </thead>
  <tbody>
  </tbody>
</table>
</div>




```python
df.state.value_counts()
```




    Florida           63944
    Texas             51682
    California        29019
    Washington        15955
    Georgia           14309
    Maryland          12965
    Mississippi       12961
    Ohio              12190
    Colorado          11254
    Illinois          11209
    New Jersey        10882
    North Carolina    10404
    Tennessee         10027
    Alabama            9997
    Pennsylvania       9941
    South Carolina     9794
    Arizona            9173
    New York           8604
    Connecticut        8128
    Minnesota          7734
    Missouri           6961
    Nevada             6693
    Louisiana          6450
    Kentucky           5278
    Maine              5095
    Indiana            4086
    Arkansas           3869
    New Mexico         3529
    Utah               2895
    Unspecified        2801
    New Hampshire      2724
    Wisconsin          2668
    Virginia           2288
    Idaho              2018
    Oregon             1775
    Michigan           1763
    Wyoming            1662
    Montana            1327
    Oklahoma           1311
    Iowa               1215
    West Virginia       746
    Nebraska            722
    Kansas              659
    Delaware            509
    Alaska              430
    North Dakota        410
    Massachusetts       328
    Vermont             300
    South Dakota        203
    Hawaii              118
    Rhode Island         82
    Puerto Rico          36
    Washington DC         2
    Name: state, dtype: int64




```python
df.state.value_counts().plot(kind='bar')
```




    <matplotlib.axes._subplots.AxesSubplot at 0x108e66470>




![png](output_14_1.png)



```python
df.describe()
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
      <th>SalesID</th>
      <th>SalePrice</th>
      <th>MachineID</th>
      <th>ModelID</th>
      <th>datasource</th>
      <th>auctioneerID</th>
      <th>YearMade</th>
      <th>MachineHoursCurrentMeter</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>4.011250e+05</td>
      <td>401125.000000</td>
      <td>4.011250e+05</td>
      <td>401125.000000</td>
      <td>401125.000000</td>
      <td>380989.000000</td>
      <td>401125.000000</td>
      <td>1.427650e+05</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>1.919713e+06</td>
      <td>31099.712848</td>
      <td>1.217903e+06</td>
      <td>6889.702980</td>
      <td>134.665810</td>
      <td>6.556040</td>
      <td>1899.156901</td>
      <td>3.457955e+03</td>
    </tr>
    <tr>
      <th>std</th>
      <td>9.090215e+05</td>
      <td>23036.898502</td>
      <td>4.409920e+05</td>
      <td>6221.777842</td>
      <td>8.962237</td>
      <td>16.976779</td>
      <td>291.797469</td>
      <td>2.759026e+04</td>
    </tr>
    <tr>
      <th>min</th>
      <td>1.139246e+06</td>
      <td>4750.000000</td>
      <td>0.000000e+00</td>
      <td>28.000000</td>
      <td>121.000000</td>
      <td>0.000000</td>
      <td>1000.000000</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.418371e+06</td>
      <td>14500.000000</td>
      <td>1.088697e+06</td>
      <td>3259.000000</td>
      <td>132.000000</td>
      <td>1.000000</td>
      <td>1985.000000</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>1.639422e+06</td>
      <td>24000.000000</td>
      <td>1.279490e+06</td>
      <td>4604.000000</td>
      <td>132.000000</td>
      <td>2.000000</td>
      <td>1995.000000</td>
      <td>0.000000e+00</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>2.242707e+06</td>
      <td>40000.000000</td>
      <td>1.468067e+06</td>
      <td>8724.000000</td>
      <td>136.000000</td>
      <td>4.000000</td>
      <td>2000.000000</td>
      <td>3.025000e+03</td>
    </tr>
    <tr>
      <th>max</th>
      <td>6.333342e+06</td>
      <td>142000.000000</td>
      <td>2.486330e+06</td>
      <td>37198.000000</td>
      <td>172.000000</td>
      <td>99.000000</td>
      <td>2013.000000</td>
      <td>2.483300e+06</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[0:2]
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
      <th>SalesID</th>
      <th>SalePrice</th>
      <th>MachineID</th>
      <th>ModelID</th>
      <th>datasource</th>
      <th>auctioneerID</th>
      <th>YearMade</th>
      <th>MachineHoursCurrentMeter</th>
      <th>UsageBand</th>
      <th>saledate</th>
      <th>fiModelDesc</th>
      <th>fiBaseModel</th>
      <th>fiSecondaryDesc</th>
      <th>fiModelSeries</th>
      <th>fiModelDescriptor</th>
      <th>ProductSize</th>
      <th>fiProductClassDesc</th>
      <th>state</th>
      <th>ProductGroup</th>
      <th>ProductGroupDesc</th>
      <th>Drive_System</th>
      <th>Enclosure</th>
      <th>Forks</th>
      <th>Pad_Type</th>
      <th>Ride_Control</th>
      <th>Stick</th>
      <th>Transmission</th>
      <th>Turbocharged</th>
      <th>Blade_Extension</th>
      <th>Blade_Width</th>
      <th>Enclosure_Type</th>
      <th>Engine_Horsepower</th>
      <th>Hydraulics</th>
      <th>Pushblock</th>
      <th>Ripper</th>
      <th>Scarifier</th>
      <th>Tip_Control</th>
      <th>Tire_Size</th>
      <th>Coupler</th>
      <th>Coupler_System</th>
      <th>Grouser_Tracks</th>
      <th>Hydraulics_Flow</th>
      <th>Track_Type</th>
      <th>Undercarriage_Pad_Width</th>
      <th>Stick_Length</th>
      <th>Thumb</th>
      <th>Pattern_Changer</th>
      <th>Grouser_Type</th>
      <th>Backhoe_Mounting</th>
      <th>Blade_Type</th>
      <th>Travel_Controls</th>
      <th>Differential_Type</th>
      <th>Steering_Controls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1139246</td>
      <td>66000</td>
      <td>999089</td>
      <td>3157</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>68.0</td>
      <td>Low</td>
      <td>11/16/2006 0:00</td>
      <td>521D</td>
      <td>521</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Wheel Loader - 110.0 to 120.0 Horsepower</td>
      <td>Alabama</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1139248</td>
      <td>57000</td>
      <td>117657</td>
      <td>77</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>4640.0</td>
      <td>Low</td>
      <td>3/26/2004 0:00</td>
      <td>950FII</td>
      <td>950</td>
      <td>F</td>
      <td>II</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 150.0 to 175.0 Horsepower</td>
      <td>North Carolina</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>23.5</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[0:2,['SalesID', 'YearMade']]
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
      <th>SalesID</th>
      <th>YearMade</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1139246</td>
      <td>2004</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1139248</td>
      <td>1996</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1139249</td>
      <td>2001</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[df['YearMade'].isin([2004,1996])]
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
      <th>SalesID</th>
      <th>SalePrice</th>
      <th>MachineID</th>
      <th>ModelID</th>
      <th>datasource</th>
      <th>auctioneerID</th>
      <th>YearMade</th>
      <th>MachineHoursCurrentMeter</th>
      <th>UsageBand</th>
      <th>saledate</th>
      <th>fiModelDesc</th>
      <th>fiBaseModel</th>
      <th>fiSecondaryDesc</th>
      <th>fiModelSeries</th>
      <th>fiModelDescriptor</th>
      <th>ProductSize</th>
      <th>fiProductClassDesc</th>
      <th>state</th>
      <th>ProductGroup</th>
      <th>ProductGroupDesc</th>
      <th>Drive_System</th>
      <th>Enclosure</th>
      <th>Forks</th>
      <th>Pad_Type</th>
      <th>Ride_Control</th>
      <th>Stick</th>
      <th>Transmission</th>
      <th>Turbocharged</th>
      <th>Blade_Extension</th>
      <th>Blade_Width</th>
      <th>Enclosure_Type</th>
      <th>Engine_Horsepower</th>
      <th>Hydraulics</th>
      <th>Pushblock</th>
      <th>Ripper</th>
      <th>Scarifier</th>
      <th>Tip_Control</th>
      <th>Tire_Size</th>
      <th>Coupler</th>
      <th>Coupler_System</th>
      <th>Grouser_Tracks</th>
      <th>Hydraulics_Flow</th>
      <th>Track_Type</th>
      <th>Undercarriage_Pad_Width</th>
      <th>Stick_Length</th>
      <th>Thumb</th>
      <th>Pattern_Changer</th>
      <th>Grouser_Type</th>
      <th>Backhoe_Mounting</th>
      <th>Blade_Type</th>
      <th>Travel_Controls</th>
      <th>Differential_Type</th>
      <th>Steering_Controls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1139246</td>
      <td>66000</td>
      <td>999089</td>
      <td>3157</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>68.0</td>
      <td>Low</td>
      <td>11/16/2006 0:00</td>
      <td>521D</td>
      <td>521</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Wheel Loader - 110.0 to 120.0 Horsepower</td>
      <td>Alabama</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1139248</td>
      <td>57000</td>
      <td>117657</td>
      <td>77</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>4640.0</td>
      <td>Low</td>
      <td>3/26/2004 0:00</td>
      <td>950FII</td>
      <td>950</td>
      <td>F</td>
      <td>II</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 150.0 to 175.0 Horsepower</td>
      <td>North Carolina</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>23.5</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1139255</td>
      <td>26500</td>
      <td>1001274</td>
      <td>4605</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>508.0</td>
      <td>Low</td>
      <td>12/18/2008 0:00</td>
      <td>310G</td>
      <td>310</td>
      <td>G</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Arizona</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Extended</td>
      <td>Powershuttle</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1139278</td>
      <td>24000</td>
      <td>1024998</td>
      <td>4605</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>1414.0</td>
      <td>Medium</td>
      <td>8/21/2008 0:00</td>
      <td>310G</td>
      <td>310</td>
      <td>G</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Oregon</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>Street</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1139290</td>
      <td>28000</td>
      <td>1058450</td>
      <td>5162</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>320.0</td>
      <td>Low</td>
      <td>1/3/2006 0:00</td>
      <td>214E</td>
      <td>214</td>
      <td>E</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>North Carolina</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>23</th>
      <td>1139346</td>
      <td>73000</td>
      <td>821452</td>
      <td>85</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>17033.0</td>
      <td>High</td>
      <td>10/19/2006 0:00</td>
      <td>966FII</td>
      <td>966</td>
      <td>F</td>
      <td>II</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 200.0 to 225.0 Horsepower</td>
      <td>Maine</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>26.5</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>28</th>
      <td>1139357</td>
      <td>46000</td>
      <td>44800</td>
      <td>19167</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>904.0</td>
      <td>Low</td>
      <td>8/9/2007 0:00</td>
      <td>685B</td>
      <td>685</td>
      <td>B</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Motorgrader - 45.0 to 130.0 Horsepower</td>
      <td>Louisiana</td>
      <td>MG</td>
      <td>Motor Graders</td>
      <td>No</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Base + 1 Function</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>34</th>
      <td>1139379</td>
      <td>18500</td>
      <td>70214</td>
      <td>13395</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>587.0</td>
      <td>Medium</td>
      <td>6/1/2006 0:00</td>
      <td>303CR</td>
      <td>303</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>CR</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Louisiana</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>42</th>
      <td>1139415</td>
      <td>15500</td>
      <td>1066239</td>
      <td>17188</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>5396.0</td>
      <td>Medium</td>
      <td>12/15/2005 0:00</td>
      <td>MF650</td>
      <td>MF650</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Compact</td>
      <td>Wheel Loader - 60.0 to 80.0 Horsepower</td>
      <td>California</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>47</th>
      <td>1139426</td>
      <td>75000</td>
      <td>625882</td>
      <td>23937</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>8270.0</td>
      <td>Low</td>
      <td>8/6/2009 0:00</td>
      <td>160HNA</td>
      <td>160</td>
      <td>H</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Motorgrader - 170.0 to 200.0 Horsepower</td>
      <td>California</td>
      <td>MG</td>
      <td>Motor Graders</td>
      <td>No</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Powershift</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>14'</td>
      <td>Low Profile</td>
      <td>Variable</td>
      <td>Base + 3 Function</td>
      <td>Yes</td>
      <td>Yes</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>14"</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>77</th>
      <td>1139502</td>
      <td>13000</td>
      <td>877241</td>
      <td>3409</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>2565.0</td>
      <td>High</td>
      <td>10/25/2007 0:00</td>
      <td>226B</td>
      <td>226</td>
      <td>B</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1351.0 to 1601.0 Lb Operat...</td>
      <td>Oregon</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>87</th>
      <td>1139531</td>
      <td>57000</td>
      <td>616902</td>
      <td>1269</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>3/12/2009 0:00</td>
      <td>330CL</td>
      <td>330</td>
      <td>C</td>
      <td>NaN</td>
      <td>L</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 33.0 to 40.0 Metr...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Triple</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>88</th>
      <td>1139532</td>
      <td>36000</td>
      <td>1042645</td>
      <td>28741</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>24794.0</td>
      <td>High</td>
      <td>5/17/2007 0:00</td>
      <td>WA5001LC</td>
      <td>WA500</td>
      <td>NaN</td>
      <td>1</td>
      <td>LC</td>
      <td>Medium</td>
      <td>Wheel Loader - 275.0 to 350.0 Horsepower</td>
      <td>Texas</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>29.5</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>93</th>
      <td>1139541</td>
      <td>12500</td>
      <td>742947</td>
      <td>3423</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>7/9/2009 0:00</td>
      <td>246B</td>
      <td>246</td>
      <td>B</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1751.0 to 2201.0 Lb Operat...</td>
      <td>California</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>Yes</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>95</th>
      <td>1139543</td>
      <td>25500</td>
      <td>1024992</td>
      <td>4794</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>1056.0</td>
      <td>Low</td>
      <td>12/15/2005 0:00</td>
      <td>710D</td>
      <td>710</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 16.0 + Ft Standard Digging Depth</td>
      <td>California</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Powershift</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>101</th>
      <td>1139556</td>
      <td>16000</td>
      <td>1034004</td>
      <td>18604</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>1085.0</td>
      <td>Medium</td>
      <td>6/14/2007 0:00</td>
      <td>CTL60</td>
      <td>CTL60</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Missouri</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>102</th>
      <td>1139558</td>
      <td>66000</td>
      <td>113683</td>
      <td>3775</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>1976.0</td>
      <td>Medium</td>
      <td>4/12/2007 0:00</td>
      <td>924G</td>
      <td>924</td>
      <td>G</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Wheel Loader - 120.0 to 135.0 Horsepower</td>
      <td>Florida</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>107</th>
      <td>1139568</td>
      <td>32000</td>
      <td>1042687</td>
      <td>491</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>13582.0</td>
      <td>High</td>
      <td>12/14/2006 0:00</td>
      <td>PC400HD-5</td>
      <td>PC400</td>
      <td>HD</td>
      <td>-5</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 40.0 to 50.0 Metr...</td>
      <td>Maine</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>123</th>
      <td>1139622</td>
      <td>65000</td>
      <td>1028436</td>
      <td>26188</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>2388.0</td>
      <td>Medium</td>
      <td>12/6/2007 0:00</td>
      <td>SK160LC-IV</td>
      <td>SK160</td>
      <td>LC</td>
      <td>#NAME?</td>
      <td>NaN</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 16.0 to 19.0 Metr...</td>
      <td>Ohio</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>10' 2"</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>125</th>
      <td>1139629</td>
      <td>25500</td>
      <td>1050171</td>
      <td>3192</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>3182.0</td>
      <td>Medium</td>
      <td>3/5/2009 0:00</td>
      <td>590SUPER M</td>
      <td>590</td>
      <td>SUPER M</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 15.0 to 16.0 Ft Standard Digg...</td>
      <td>California</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Extended</td>
      <td>Powershuttle</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>141</th>
      <td>1139683</td>
      <td>10500</td>
      <td>311407</td>
      <td>3409</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>2260.0</td>
      <td>High</td>
      <td>7/27/2006 0:00</td>
      <td>226B</td>
      <td>226</td>
      <td>B</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1351.0 to 1601.0 Lb Operat...</td>
      <td>Nevada</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>142</th>
      <td>1139688</td>
      <td>54000</td>
      <td>332099</td>
      <td>1557</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>1897.0</td>
      <td>High</td>
      <td>5/4/2006 0:00</td>
      <td>D4GXL</td>
      <td>D4</td>
      <td>G</td>
      <td>NaN</td>
      <td>XL</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 75.0 to 85.0 Horse...</td>
      <td>Texas</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydrostatic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>151</th>
      <td>1139718</td>
      <td>19500</td>
      <td>1060784</td>
      <td>3466</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>6576.0</td>
      <td>Medium</td>
      <td>8/6/2009 0:00</td>
      <td>312B</td>
      <td>312</td>
      <td>B</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 12.0 to 14.0 Metr...</td>
      <td>New York</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>28 inch</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>165</th>
      <td>1139765</td>
      <td>26000</td>
      <td>1059119</td>
      <td>4605</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>1785.0</td>
      <td>Medium</td>
      <td>11/6/2008 0:00</td>
      <td>310G</td>
      <td>310</td>
      <td>G</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>California</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Two Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Extended</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>167</th>
      <td>1139773</td>
      <td>41000</td>
      <td>1040141</td>
      <td>5894</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>10/21/2010 0:00</td>
      <td>L90E</td>
      <td>L90</td>
      <td>E</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 150.0 to 175.0 Horsepower</td>
      <td>Michigan</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>20.5</td>
      <td>Hydraulic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>174</th>
      <td>1139790</td>
      <td>66000</td>
      <td>1031985</td>
      <td>14310</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>4659.0</td>
      <td>High</td>
      <td>6/19/2008 0:00</td>
      <td>330CLC</td>
      <td>330</td>
      <td>C</td>
      <td>NaN</td>
      <td>LC</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 33.0 to 40.0 Metr...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>32 inch</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>183</th>
      <td>1139816</td>
      <td>27000</td>
      <td>521389</td>
      <td>1096</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>2590.0</td>
      <td>High</td>
      <td>10/25/2007 0:00</td>
      <td>308CCR</td>
      <td>308</td>
      <td>C</td>
      <td>NaN</td>
      <td>CR</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 8.0 to 11.0 Metri...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Manual</td>
      <td>Yes</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>196</th>
      <td>1139877</td>
      <td>10000</td>
      <td>1069266</td>
      <td>17311</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>2178.0</td>
      <td>Medium</td>
      <td>6/2/2011 0:00</td>
      <td>S175</td>
      <td>S175</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1601.0 to 1751.0 Lb Operat...</td>
      <td>Virginia</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>Yes</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>200</th>
      <td>1139886</td>
      <td>60000</td>
      <td>713597</td>
      <td>1453</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>1614.0</td>
      <td>Medium</td>
      <td>8/23/2007 0:00</td>
      <td>928GZ</td>
      <td>928</td>
      <td>G</td>
      <td>NaN</td>
      <td>Z</td>
      <td>Medium</td>
      <td>Wheel Loader - 150.0 to 175.0 Horsepower</td>
      <td>California</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>20.5</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Limited Slip</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>213</th>
      <td>1139945</td>
      <td>32500</td>
      <td>999621</td>
      <td>2752</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>2578.0</td>
      <td>Low</td>
      <td>5/20/2004 0:00</td>
      <td>D4CIII</td>
      <td>D4</td>
      <td>C</td>
      <td>III</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 75.0 to 85.0 Horse...</td>
      <td>Ohio</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <td>...</td>
    </tr>
    <tr>
      <th>400976</th>
      <td>6327984</td>
      <td>12500</td>
      <td>1833625</td>
      <td>20101</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/28/2011 0:00</td>
      <td>TL130</td>
      <td>TL130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Michigan</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400977</th>
      <td>6327985</td>
      <td>10000</td>
      <td>1863915</td>
      <td>20101</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/28/2011 0:00</td>
      <td>TL130</td>
      <td>TL130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>North Carolina</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400978</th>
      <td>6327987</td>
      <td>14000</td>
      <td>1884682</td>
      <td>20101</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>TL130</td>
      <td>TL130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Missouri</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400979</th>
      <td>6327988</td>
      <td>11500</td>
      <td>1939234</td>
      <td>20101</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/7/2011 0:00</td>
      <td>TL130</td>
      <td>TL130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Illinois</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400980</th>
      <td>6327991</td>
      <td>13000</td>
      <td>1823689</td>
      <td>20101</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/2/2011 0:00</td>
      <td>TL130</td>
      <td>TL130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Maryland</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400982</th>
      <td>6327996</td>
      <td>9000</td>
      <td>1812656</td>
      <td>20101</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6/22/2011 0:00</td>
      <td>TL130</td>
      <td>TL130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Texas</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400983</th>
      <td>6327999</td>
      <td>9500</td>
      <td>1816748</td>
      <td>20101</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/26/2011 0:00</td>
      <td>TL130</td>
      <td>TL130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Florida</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400984</th>
      <td>6328000</td>
      <td>9500</td>
      <td>1832952</td>
      <td>20101</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/26/2011 0:00</td>
      <td>TL130</td>
      <td>TL130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Florida</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400985</th>
      <td>6328002</td>
      <td>14000</td>
      <td>1800501</td>
      <td>20101</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/16/2011 0:00</td>
      <td>TL130</td>
      <td>TL130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Texas</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400986</th>
      <td>6328003</td>
      <td>10500</td>
      <td>1944377</td>
      <td>20101</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6/22/2011 0:00</td>
      <td>TL130</td>
      <td>TL130</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Texas</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401010</th>
      <td>6328082</td>
      <td>17500</td>
      <td>1943282</td>
      <td>20102</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/25/2011 0:00</td>
      <td>TL140</td>
      <td>TL140</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2701.0+ Lb Operating Capacity</td>
      <td>Maryland</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>High Flow</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401011</th>
      <td>6328083</td>
      <td>16500</td>
      <td>1808941</td>
      <td>20102</td>
      <td>149</td>
      <td>12.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/21/2011 0:00</td>
      <td>TL140</td>
      <td>TL140</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2701.0+ Lb Operating Capacity</td>
      <td>South Carolina</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401012</th>
      <td>6328084</td>
      <td>16000</td>
      <td>1834609</td>
      <td>20102</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/7/2011 0:00</td>
      <td>TL140</td>
      <td>TL140</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2701.0+ Lb Operating Capacity</td>
      <td>Illinois</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401034</th>
      <td>6328145</td>
      <td>13000</td>
      <td>1905057</td>
      <td>20103</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/4/2011 0:00</td>
      <td>TL150</td>
      <td>TL150</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Texas</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401035</th>
      <td>6328146</td>
      <td>13500</td>
      <td>1806800</td>
      <td>20103</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/26/2011 0:00</td>
      <td>TL150</td>
      <td>TL150</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Florida</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401036</th>
      <td>6328148</td>
      <td>15000</td>
      <td>1896785</td>
      <td>20103</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/18/2011 0:00</td>
      <td>TL150</td>
      <td>TL150</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Maryland</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401037</th>
      <td>6328153</td>
      <td>18500</td>
      <td>1732266</td>
      <td>20103</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/25/2011 0:00</td>
      <td>TL150</td>
      <td>TL150</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Maryland</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401038</th>
      <td>6328154</td>
      <td>18500</td>
      <td>1832703</td>
      <td>20103</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>7/19/2011 0:00</td>
      <td>TL150</td>
      <td>TL150</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Maryland</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401050</th>
      <td>6328439</td>
      <td>10500</td>
      <td>1177366</td>
      <td>10917</td>
      <td>149</td>
      <td>1.0</td>
      <td>1996</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/2/2011 0:00</td>
      <td>806</td>
      <td>806</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Compact</td>
      <td>Wheel Loader - 0.0 to 40.0 Horsepower</td>
      <td>Illinois</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>401051</th>
      <td>6328442</td>
      <td>18000</td>
      <td>1523948</td>
      <td>10917</td>
      <td>149</td>
      <td>1.0</td>
      <td>1996</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/26/2011 0:00</td>
      <td>806</td>
      <td>806</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Compact</td>
      <td>Wheel Loader - 0.0 to 40.0 Horsepower</td>
      <td>Florida</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>401077</th>
      <td>6333213</td>
      <td>9500</td>
      <td>1812257</td>
      <td>21442</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/26/2011 0:00</td>
      <td>45NX</td>
      <td>45</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 4.0 to 5.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401078</th>
      <td>6333216</td>
      <td>13000</td>
      <td>1851957</td>
      <td>21450</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>80NX3</td>
      <td>80</td>
      <td>NX</td>
      <td>3</td>
      <td>NaN</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 8.0 to 11.0 Metri...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401079</th>
      <td>6333217</td>
      <td>16000</td>
      <td>1925895</td>
      <td>21449</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/26/2011 0:00</td>
      <td>80NX</td>
      <td>80</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 8.0 to 11.0 Metri...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401080</th>
      <td>6333221</td>
      <td>18500</td>
      <td>1899876</td>
      <td>21449</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>80NX</td>
      <td>80</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 8.0 to 11.0 Metri...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401083</th>
      <td>6333230</td>
      <td>8000</td>
      <td>1329856</td>
      <td>21434</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/8/2011 0:00</td>
      <td>28N</td>
      <td>28</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Manual</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401096</th>
      <td>6333260</td>
      <td>10000</td>
      <td>1816341</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Georgia</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401098</th>
      <td>6333262</td>
      <td>10500</td>
      <td>1791341</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401099</th>
      <td>6333263</td>
      <td>11000</td>
      <td>1833174</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401100</th>
      <td>6333264</td>
      <td>10500</td>
      <td>1791370</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401101</th>
      <td>6333270</td>
      <td>10000</td>
      <td>1799208</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>36711 rows × 53 columns</p>
</div>




```python
df.iat[1,8]
```




    'Low'




```python
df[df.fiModelSeries.isna()]
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
      <th>SalesID</th>
      <th>SalePrice</th>
      <th>MachineID</th>
      <th>ModelID</th>
      <th>datasource</th>
      <th>auctioneerID</th>
      <th>YearMade</th>
      <th>MachineHoursCurrentMeter</th>
      <th>UsageBand</th>
      <th>saledate</th>
      <th>fiModelDesc</th>
      <th>fiBaseModel</th>
      <th>fiSecondaryDesc</th>
      <th>fiModelSeries</th>
      <th>fiModelDescriptor</th>
      <th>ProductSize</th>
      <th>fiProductClassDesc</th>
      <th>state</th>
      <th>ProductGroup</th>
      <th>ProductGroupDesc</th>
      <th>Drive_System</th>
      <th>Enclosure</th>
      <th>Forks</th>
      <th>Pad_Type</th>
      <th>Ride_Control</th>
      <th>Stick</th>
      <th>Transmission</th>
      <th>Turbocharged</th>
      <th>Blade_Extension</th>
      <th>Blade_Width</th>
      <th>Enclosure_Type</th>
      <th>Engine_Horsepower</th>
      <th>Hydraulics</th>
      <th>Pushblock</th>
      <th>Ripper</th>
      <th>Scarifier</th>
      <th>Tip_Control</th>
      <th>Tire_Size</th>
      <th>Coupler</th>
      <th>Coupler_System</th>
      <th>Grouser_Tracks</th>
      <th>Hydraulics_Flow</th>
      <th>Track_Type</th>
      <th>Undercarriage_Pad_Width</th>
      <th>Stick_Length</th>
      <th>Thumb</th>
      <th>Pattern_Changer</th>
      <th>Grouser_Type</th>
      <th>Backhoe_Mounting</th>
      <th>Blade_Type</th>
      <th>Travel_Controls</th>
      <th>Differential_Type</th>
      <th>Steering_Controls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1139246</td>
      <td>66000</td>
      <td>999089</td>
      <td>3157</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>68.0</td>
      <td>Low</td>
      <td>11/16/2006 0:00</td>
      <td>521D</td>
      <td>521</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Wheel Loader - 110.0 to 120.0 Horsepower</td>
      <td>Alabama</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1139249</td>
      <td>10000</td>
      <td>434808</td>
      <td>7009</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>2838.0</td>
      <td>High</td>
      <td>2/26/2004 0:00</td>
      <td>226</td>
      <td>226</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1351.0 to 1601.0 Lb Operat...</td>
      <td>New York</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1139253</td>
      <td>11000</td>
      <td>1057373</td>
      <td>17311</td>
      <td>121</td>
      <td>3.0</td>
      <td>2007</td>
      <td>722.0</td>
      <td>Medium</td>
      <td>7/23/2009 0:00</td>
      <td>S175</td>
      <td>S175</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1601.0 to 1751.0 Lb Operat...</td>
      <td>New York</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1139255</td>
      <td>26500</td>
      <td>1001274</td>
      <td>4605</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>508.0</td>
      <td>Low</td>
      <td>12/18/2008 0:00</td>
      <td>310G</td>
      <td>310</td>
      <td>G</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Arizona</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Extended</td>
      <td>Powershuttle</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1139256</td>
      <td>21000</td>
      <td>772701</td>
      <td>1937</td>
      <td>121</td>
      <td>3.0</td>
      <td>1993</td>
      <td>11540.0</td>
      <td>High</td>
      <td>8/26/2004 0:00</td>
      <td>790ELC</td>
      <td>790</td>
      <td>E</td>
      <td>NaN</td>
      <td>LC</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 21.0 to 24.0 Metr...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1139261</td>
      <td>27000</td>
      <td>902002</td>
      <td>3539</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>4883.0</td>
      <td>High</td>
      <td>11/17/2005 0:00</td>
      <td>416D</td>
      <td>416</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Illinois</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>Reversible</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1139272</td>
      <td>21500</td>
      <td>1036251</td>
      <td>36003</td>
      <td>121</td>
      <td>3.0</td>
      <td>2008</td>
      <td>302.0</td>
      <td>Low</td>
      <td>8/27/2009 0:00</td>
      <td>430HAG</td>
      <td>430</td>
      <td>HAG</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1139275</td>
      <td>65000</td>
      <td>1016474</td>
      <td>3883</td>
      <td>121</td>
      <td>3.0</td>
      <td>1000</td>
      <td>20700.0</td>
      <td>Medium</td>
      <td>8/9/2007 0:00</td>
      <td>988B</td>
      <td>988</td>
      <td>B</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Large</td>
      <td>Wheel Loader - 350.0 to 500.0 Horsepower</td>
      <td>Florida</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1139278</td>
      <td>24000</td>
      <td>1024998</td>
      <td>4605</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>1414.0</td>
      <td>Medium</td>
      <td>8/21/2008 0:00</td>
      <td>310G</td>
      <td>310</td>
      <td>G</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Oregon</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>Street</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1139282</td>
      <td>22500</td>
      <td>319906</td>
      <td>5255</td>
      <td>121</td>
      <td>3.0</td>
      <td>1998</td>
      <td>2764.0</td>
      <td>Low</td>
      <td>8/24/2006 0:00</td>
      <td>D31E</td>
      <td>D31</td>
      <td>E</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 20.0 to 75.0 Horse...</td>
      <td>Ohio</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>PAT</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1139284</td>
      <td>30500</td>
      <td>1068082</td>
      <td>3542</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>1921.0</td>
      <td>Medium</td>
      <td>1/26/2006 0:00</td>
      <td>420D</td>
      <td>420</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Texas</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1139290</td>
      <td>28000</td>
      <td>1058450</td>
      <td>5162</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>320.0</td>
      <td>Low</td>
      <td>1/3/2006 0:00</td>
      <td>214E</td>
      <td>214</td>
      <td>E</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>North Carolina</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1139291</td>
      <td>19000</td>
      <td>1004810</td>
      <td>4604</td>
      <td>121</td>
      <td>3.0</td>
      <td>1999</td>
      <td>2450.0</td>
      <td>Medium</td>
      <td>11/16/2006 0:00</td>
      <td>310E</td>
      <td>310</td>
      <td>E</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Arkansas</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Two Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1139292</td>
      <td>13500</td>
      <td>1026973</td>
      <td>9510</td>
      <td>121</td>
      <td>3.0</td>
      <td>1999</td>
      <td>1972.0</td>
      <td>Low</td>
      <td>6/14/2007 0:00</td>
      <td>334</td>
      <td>334</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1139299</td>
      <td>9500</td>
      <td>1002713</td>
      <td>21442</td>
      <td>121</td>
      <td>3.0</td>
      <td>2003</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>1/28/2010 0:00</td>
      <td>45NX</td>
      <td>45</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 4.0 to 5.0 Metric...</td>
      <td>Wisconsin</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>16 inch</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1139301</td>
      <td>12500</td>
      <td>125790</td>
      <td>7040</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>994.0</td>
      <td>Low</td>
      <td>3/9/2006 0:00</td>
      <td>302.5</td>
      <td>302.5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1139304</td>
      <td>11500</td>
      <td>1011914</td>
      <td>3177</td>
      <td>121</td>
      <td>3.0</td>
      <td>1991</td>
      <td>8005.0</td>
      <td>Medium</td>
      <td>11/17/2005 0:00</td>
      <td>580SUPER K</td>
      <td>580</td>
      <td>SUPER K</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Illinois</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Two Wheel Drive</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>20</th>
      <td>1139311</td>
      <td>41000</td>
      <td>1014135</td>
      <td>8867</td>
      <td>121</td>
      <td>3.0</td>
      <td>2000</td>
      <td>3259.0</td>
      <td>Medium</td>
      <td>5/18/2006 0:00</td>
      <td>JS260</td>
      <td>JS260</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 24.0 to 28.0 Metr...</td>
      <td>Kansas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>32 inch</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>21</th>
      <td>1139333</td>
      <td>34500</td>
      <td>999192</td>
      <td>3350</td>
      <td>121</td>
      <td>3.0</td>
      <td>1000</td>
      <td>16328.0</td>
      <td>Medium</td>
      <td>10/19/2006 0:00</td>
      <td>120G</td>
      <td>120</td>
      <td>G</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Motorgrader - 45.0 to 130.0 Horsepower</td>
      <td>Nevada</td>
      <td>MG</td>
      <td>Motor Graders</td>
      <td>No</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Powershift</td>
      <td>NaN</td>
      <td>Yes</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Base + 1 Function</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Sideshift &amp; Tip</td>
      <td>13"</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>22</th>
      <td>1139344</td>
      <td>26000</td>
      <td>1044500</td>
      <td>7040</td>
      <td>121</td>
      <td>3.0</td>
      <td>2005</td>
      <td>109.0</td>
      <td>Low</td>
      <td>10/25/2007 0:00</td>
      <td>302.5</td>
      <td>302.5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>Iowa</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>24</th>
      <td>1139348</td>
      <td>33000</td>
      <td>294562</td>
      <td>3542</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>1877.0</td>
      <td>Medium</td>
      <td>5/20/2004 0:00</td>
      <td>420D</td>
      <td>420</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Texas</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25</th>
      <td>1139351</td>
      <td>12500</td>
      <td>833838</td>
      <td>7009</td>
      <td>121</td>
      <td>3.0</td>
      <td>2003</td>
      <td>1028.0</td>
      <td>Medium</td>
      <td>3/9/2006 0:00</td>
      <td>226</td>
      <td>226</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1351.0 to 1601.0 Lb Operat...</td>
      <td>Massachusetts</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>26</th>
      <td>1139354</td>
      <td>15500</td>
      <td>565440</td>
      <td>7040</td>
      <td>121</td>
      <td>3.0</td>
      <td>2003</td>
      <td>356.0</td>
      <td>Low</td>
      <td>3/9/2006 0:00</td>
      <td>302.5</td>
      <td>302.5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>California</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>27</th>
      <td>1139356</td>
      <td>53000</td>
      <td>1004127</td>
      <td>25458</td>
      <td>121</td>
      <td>3.0</td>
      <td>2000</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>2/22/2007 0:00</td>
      <td>EX550STD</td>
      <td>EX550</td>
      <td>STD</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 50.0 to 66.0 Metr...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>28</th>
      <td>1139357</td>
      <td>46000</td>
      <td>44800</td>
      <td>19167</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>904.0</td>
      <td>Low</td>
      <td>8/9/2007 0:00</td>
      <td>685B</td>
      <td>685</td>
      <td>B</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Motorgrader - 45.0 to 130.0 Horsepower</td>
      <td>Louisiana</td>
      <td>MG</td>
      <td>Motor Graders</td>
      <td>No</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Base + 1 Function</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>29</th>
      <td>1139358</td>
      <td>89000</td>
      <td>1018076</td>
      <td>1333</td>
      <td>121</td>
      <td>3.0</td>
      <td>1998</td>
      <td>10466.0</td>
      <td>Medium</td>
      <td>6/1/2006 0:00</td>
      <td>345BL</td>
      <td>345</td>
      <td>BL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 40.0 to 50.0 Metr...</td>
      <td>Minnesota</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>15' 9"</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>30</th>
      <td>1139363</td>
      <td>51000</td>
      <td>871201</td>
      <td>1263</td>
      <td>121</td>
      <td>3.0</td>
      <td>1999</td>
      <td>15633.0</td>
      <td>High</td>
      <td>10/22/2010 0:00</td>
      <td>330BL</td>
      <td>330</td>
      <td>B</td>
      <td>NaN</td>
      <td>L</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 33.0 to 40.0 Metr...</td>
      <td>New Hampshire</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>31</th>
      <td>1139365</td>
      <td>14000</td>
      <td>973717</td>
      <td>9566</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>2097.0</td>
      <td>Medium</td>
      <td>3/22/2007 0:00</td>
      <td>873</td>
      <td>873</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Idaho</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>32</th>
      <td>1139367</td>
      <td>31500</td>
      <td>1036100</td>
      <td>9109</td>
      <td>121</td>
      <td>3.0</td>
      <td>1995</td>
      <td>7542.0</td>
      <td>Medium</td>
      <td>7/27/2006 0:00</td>
      <td>WA250</td>
      <td>WA250</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Wheel Loader - 120.0 to 135.0 Horsepower</td>
      <td>North Carolina</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>33</th>
      <td>1139369</td>
      <td>14000</td>
      <td>1050658</td>
      <td>1918</td>
      <td>121</td>
      <td>3.0</td>
      <td>1000</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>1/28/2010 0:00</td>
      <td>750BLT</td>
      <td>750</td>
      <td>B</td>
      <td>NaN</td>
      <td>LT</td>
      <td>Medium</td>
      <td>Track Type Tractor, Dozer - 130.0 to 160.0 Hor...</td>
      <td>Michigan</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydrostatic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <td>...</td>
    </tr>
    <tr>
      <th>401092</th>
      <td>6333256</td>
      <td>10500</td>
      <td>1872420</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401093</th>
      <td>6333257</td>
      <td>10500</td>
      <td>1945018</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401094</th>
      <td>6333258</td>
      <td>11500</td>
      <td>1874065</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/13/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Maryland</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401095</th>
      <td>6333259</td>
      <td>10500</td>
      <td>1872639</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401096</th>
      <td>6333260</td>
      <td>10000</td>
      <td>1816341</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Georgia</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401097</th>
      <td>6333261</td>
      <td>8500</td>
      <td>1843949</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/28/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401098</th>
      <td>6333262</td>
      <td>10500</td>
      <td>1791341</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401099</th>
      <td>6333263</td>
      <td>11000</td>
      <td>1833174</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401100</th>
      <td>6333264</td>
      <td>10500</td>
      <td>1791370</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401101</th>
      <td>6333270</td>
      <td>10000</td>
      <td>1799208</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401102</th>
      <td>6333272</td>
      <td>10500</td>
      <td>1927142</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401103</th>
      <td>6333273</td>
      <td>12500</td>
      <td>1789856</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Georgia</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401104</th>
      <td>6333275</td>
      <td>10500</td>
      <td>1924623</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401105</th>
      <td>6333276</td>
      <td>10000</td>
      <td>1835350</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401106</th>
      <td>6333278</td>
      <td>10500</td>
      <td>1944702</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401107</th>
      <td>6333279</td>
      <td>12500</td>
      <td>1866563</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Georgia</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401108</th>
      <td>6333280</td>
      <td>10500</td>
      <td>1851633</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401109</th>
      <td>6333281</td>
      <td>10500</td>
      <td>1798958</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401110</th>
      <td>6333282</td>
      <td>10500</td>
      <td>1878866</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Georgia</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401111</th>
      <td>6333283</td>
      <td>10000</td>
      <td>1874235</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401112</th>
      <td>6333284</td>
      <td>10500</td>
      <td>1887654</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401113</th>
      <td>6333285</td>
      <td>10500</td>
      <td>1817165</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401114</th>
      <td>6333287</td>
      <td>12500</td>
      <td>1918242</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401115</th>
      <td>6333290</td>
      <td>10000</td>
      <td>1843374</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401116</th>
      <td>6333302</td>
      <td>8500</td>
      <td>1825337</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401117</th>
      <td>6333307</td>
      <td>10000</td>
      <td>1821747</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401118</th>
      <td>6333311</td>
      <td>9500</td>
      <td>1828862</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2006</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401119</th>
      <td>6333335</td>
      <td>8500</td>
      <td>1798293</td>
      <td>21435</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>30NX</td>
      <td>30</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401123</th>
      <td>6333341</td>
      <td>9000</td>
      <td>1903570</td>
      <td>21435</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>30NX</td>
      <td>30</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401124</th>
      <td>6333342</td>
      <td>7750</td>
      <td>1926965</td>
      <td>21435</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>30NX</td>
      <td>30</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>344217 rows × 53 columns</p>
</div>




```python
df[df.fiModelSeries.isna()==False]
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
      <th>SalesID</th>
      <th>SalePrice</th>
      <th>MachineID</th>
      <th>ModelID</th>
      <th>datasource</th>
      <th>auctioneerID</th>
      <th>YearMade</th>
      <th>MachineHoursCurrentMeter</th>
      <th>UsageBand</th>
      <th>saledate</th>
      <th>fiModelDesc</th>
      <th>fiBaseModel</th>
      <th>fiSecondaryDesc</th>
      <th>fiModelSeries</th>
      <th>fiModelDescriptor</th>
      <th>ProductSize</th>
      <th>fiProductClassDesc</th>
      <th>state</th>
      <th>ProductGroup</th>
      <th>ProductGroupDesc</th>
      <th>Drive_System</th>
      <th>Enclosure</th>
      <th>Forks</th>
      <th>Pad_Type</th>
      <th>Ride_Control</th>
      <th>Stick</th>
      <th>Transmission</th>
      <th>Turbocharged</th>
      <th>Blade_Extension</th>
      <th>Blade_Width</th>
      <th>Enclosure_Type</th>
      <th>Engine_Horsepower</th>
      <th>Hydraulics</th>
      <th>Pushblock</th>
      <th>Ripper</th>
      <th>Scarifier</th>
      <th>Tip_Control</th>
      <th>Tire_Size</th>
      <th>Coupler</th>
      <th>Coupler_System</th>
      <th>Grouser_Tracks</th>
      <th>Hydraulics_Flow</th>
      <th>Track_Type</th>
      <th>Undercarriage_Pad_Width</th>
      <th>Stick_Length</th>
      <th>Thumb</th>
      <th>Pattern_Changer</th>
      <th>Grouser_Type</th>
      <th>Backhoe_Mounting</th>
      <th>Blade_Type</th>
      <th>Travel_Controls</th>
      <th>Differential_Type</th>
      <th>Steering_Controls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>1139248</td>
      <td>57000</td>
      <td>117657</td>
      <td>77</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>4640.0</td>
      <td>Low</td>
      <td>3/26/2004 0:00</td>
      <td>950FII</td>
      <td>950</td>
      <td>F</td>
      <td>II</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 150.0 to 175.0 Horsepower</td>
      <td>North Carolina</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>23.5</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1139251</td>
      <td>38500</td>
      <td>1026470</td>
      <td>332</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>3486.0</td>
      <td>High</td>
      <td>5/19/2011 0:00</td>
      <td>PC120-6E</td>
      <td>PC120</td>
      <td>NaN</td>
      <td>-6E</td>
      <td>NaN</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 12.0 to 14.0 Metr...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1139283</td>
      <td>36000</td>
      <td>1052214</td>
      <td>2232</td>
      <td>121</td>
      <td>3.0</td>
      <td>1998</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>10/20/2005 0:00</td>
      <td>PC200LC6</td>
      <td>PC200</td>
      <td>NaN</td>
      <td>LC</td>
      <td>6</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 19.0 to 21.0 Metr...</td>
      <td>Ohio</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>11' 0"</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>23</th>
      <td>1139346</td>
      <td>73000</td>
      <td>821452</td>
      <td>85</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>17033.0</td>
      <td>High</td>
      <td>10/19/2006 0:00</td>
      <td>966FII</td>
      <td>966</td>
      <td>F</td>
      <td>II</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 200.0 to 225.0 Horsepower</td>
      <td>Maine</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>26.5</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>35</th>
      <td>1139382</td>
      <td>10000</td>
      <td>1068548</td>
      <td>112</td>
      <td>121</td>
      <td>3.0</td>
      <td>1000</td>
      <td>3981.0</td>
      <td>Low</td>
      <td>6/9/2011 0:00</td>
      <td>95ZII</td>
      <td>95</td>
      <td>Z</td>
      <td>II</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 275.0 to 350.0 Horsepower</td>
      <td>Arkansas</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>29.5</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>44</th>
      <td>1139421</td>
      <td>32000</td>
      <td>1048704</td>
      <td>2797</td>
      <td>121</td>
      <td>3.0</td>
      <td>2000</td>
      <td>3817.0</td>
      <td>Low</td>
      <td>6/16/2011 0:00</td>
      <td>EX120-5</td>
      <td>EX120</td>
      <td>NaN</td>
      <td>-5</td>
      <td>NaN</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 8.0 to 11.0 Metri...</td>
      <td>California</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Hydraulic</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>50</th>
      <td>1139445</td>
      <td>35500</td>
      <td>1066661</td>
      <td>13776</td>
      <td>121</td>
      <td>3.0</td>
      <td>1998</td>
      <td>764.0</td>
      <td>Low</td>
      <td>7/15/2004 0:00</td>
      <td>D3CIIIXL</td>
      <td>D3</td>
      <td>C</td>
      <td>III</td>
      <td>XL</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 20.0 to 75.0 Horse...</td>
      <td>Michigan</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>53</th>
      <td>1139451</td>
      <td>30000</td>
      <td>980151</td>
      <td>13776</td>
      <td>121</td>
      <td>3.0</td>
      <td>1998</td>
      <td>3186.0</td>
      <td>Medium</td>
      <td>11/17/2005 0:00</td>
      <td>D3CIIIXL</td>
      <td>D3</td>
      <td>C</td>
      <td>III</td>
      <td>XL</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 20.0 to 75.0 Horse...</td>
      <td>Utah</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydrostatic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4 Valve</td>
      <td>NaN</td>
      <td>Single Shank</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>56</th>
      <td>1139457</td>
      <td>9500</td>
      <td>1063011</td>
      <td>506</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>3576.0</td>
      <td>Medium</td>
      <td>6/28/2007 0:00</td>
      <td>PC40MR-1</td>
      <td>PC40</td>
      <td>MR</td>
      <td>-1</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 4.0 to 5.0 Metric...</td>
      <td>Wisconsin</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>30 inch</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>59</th>
      <td>1139463</td>
      <td>37000</td>
      <td>1033597</td>
      <td>28920</td>
      <td>121</td>
      <td>3.0</td>
      <td>2006</td>
      <td>11121.0</td>
      <td>High</td>
      <td>2/25/2010 0:00</td>
      <td>WA250PT5L</td>
      <td>WA250</td>
      <td>PT</td>
      <td>5</td>
      <td>L</td>
      <td>NaN</td>
      <td>Wheel Loader - 120.0 to 135.0 Horsepower</td>
      <td>Alabama</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>Hydraulic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>63</th>
      <td>1139473</td>
      <td>30500</td>
      <td>1054162</td>
      <td>663</td>
      <td>121</td>
      <td>3.0</td>
      <td>2000</td>
      <td>1894.0</td>
      <td>Medium</td>
      <td>6/15/2004 0:00</td>
      <td>WB150-2</td>
      <td>WB150</td>
      <td>NaN</td>
      <td>-2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 15.0 to 16.0 Ft Standard Digg...</td>
      <td>Missouri</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Extended</td>
      <td>Powershuttle</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>67</th>
      <td>1139481</td>
      <td>29000</td>
      <td>1062393</td>
      <td>13247</td>
      <td>121</td>
      <td>3.0</td>
      <td>2005</td>
      <td>2032.0</td>
      <td>Medium</td>
      <td>4/22/2010 0:00</td>
      <td>580MII</td>
      <td>580</td>
      <td>M</td>
      <td>II</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Texas</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Two Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Powershuttle</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>70</th>
      <td>1139487</td>
      <td>33500</td>
      <td>1054383</td>
      <td>13792</td>
      <td>121</td>
      <td>3.0</td>
      <td>1999</td>
      <td>2413.0</td>
      <td>Medium</td>
      <td>6/3/2004 0:00</td>
      <td>D4CIIIXL</td>
      <td>D4</td>
      <td>C</td>
      <td>III</td>
      <td>XL</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 75.0 to 85.0 Horse...</td>
      <td>Arkansas</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>88</th>
      <td>1139532</td>
      <td>36000</td>
      <td>1042645</td>
      <td>28741</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>24794.0</td>
      <td>High</td>
      <td>5/17/2007 0:00</td>
      <td>WA5001LC</td>
      <td>WA500</td>
      <td>NaN</td>
      <td>1</td>
      <td>LC</td>
      <td>Medium</td>
      <td>Wheel Loader - 275.0 to 350.0 Horsepower</td>
      <td>Texas</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>29.5</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>99</th>
      <td>1139550</td>
      <td>27000</td>
      <td>62171</td>
      <td>13776</td>
      <td>121</td>
      <td>3.0</td>
      <td>2000</td>
      <td>2842.0</td>
      <td>Medium</td>
      <td>6/1/2006 0:00</td>
      <td>D3CIIIXL</td>
      <td>D3</td>
      <td>C</td>
      <td>III</td>
      <td>XL</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 20.0 to 75.0 Horse...</td>
      <td>Louisiana</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydrostatic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>107</th>
      <td>1139568</td>
      <td>32000</td>
      <td>1042687</td>
      <td>491</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>13582.0</td>
      <td>High</td>
      <td>12/14/2006 0:00</td>
      <td>PC400HD-5</td>
      <td>PC400</td>
      <td>HD</td>
      <td>-5</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 40.0 to 50.0 Metr...</td>
      <td>Maine</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>111</th>
      <td>1139583</td>
      <td>83000</td>
      <td>1011281</td>
      <td>13864</td>
      <td>121</td>
      <td>3.0</td>
      <td>1995</td>
      <td>2347.0</td>
      <td>Low</td>
      <td>3/8/2007 0:00</td>
      <td>D6HIIXL</td>
      <td>D6</td>
      <td>H</td>
      <td>II</td>
      <td>XL</td>
      <td>Medium</td>
      <td>Track Type Tractor, Dozer - 160.0 to 190.0 Hor...</td>
      <td>Texas</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Powershift</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>Single Shank</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Differential Steer</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>113</th>
      <td>1139589</td>
      <td>11500</td>
      <td>1066636</td>
      <td>473</td>
      <td>121</td>
      <td>3.0</td>
      <td>2002</td>
      <td>1502.0</td>
      <td>Low</td>
      <td>9/7/2006 0:00</td>
      <td>PC30MR-1</td>
      <td>PC30</td>
      <td>MR</td>
      <td>-1</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Oklahoma</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>123</th>
      <td>1139622</td>
      <td>65000</td>
      <td>1028436</td>
      <td>26188</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>2388.0</td>
      <td>Medium</td>
      <td>12/6/2007 0:00</td>
      <td>SK160LC-IV</td>
      <td>SK160</td>
      <td>LC</td>
      <td>#NAME?</td>
      <td>NaN</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 16.0 to 19.0 Metr...</td>
      <td>Ohio</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>10' 2"</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>133</th>
      <td>1139658</td>
      <td>25500</td>
      <td>1052551</td>
      <td>658</td>
      <td>121</td>
      <td>3.0</td>
      <td>2000</td>
      <td>2083.0</td>
      <td>Medium</td>
      <td>3/25/2004 0:00</td>
      <td>WB140-2</td>
      <td>WB140</td>
      <td>NaN</td>
      <td>-2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Massachusetts</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Extended</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>140</th>
      <td>1139681</td>
      <td>14500</td>
      <td>1004392</td>
      <td>16535</td>
      <td>121</td>
      <td>3.0</td>
      <td>2005</td>
      <td>1526.0</td>
      <td>Medium</td>
      <td>9/20/2007 0:00</td>
      <td>PC27MR-2</td>
      <td>PC27</td>
      <td>MR</td>
      <td>-2</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>166</th>
      <td>1139770</td>
      <td>45000</td>
      <td>1019952</td>
      <td>460</td>
      <td>121</td>
      <td>3.0</td>
      <td>1998</td>
      <td>9270.0</td>
      <td>Medium</td>
      <td>3/23/2006 0:00</td>
      <td>PC300LC6</td>
      <td>PC300</td>
      <td>NaN</td>
      <td>LC</td>
      <td>6</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 33.0 to 40.0 Metr...</td>
      <td>West Virginia</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>32 inch</td>
      <td>10' 6"</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>184</th>
      <td>1139818</td>
      <td>29000</td>
      <td>602039</td>
      <td>1528</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>3059.0</td>
      <td>High</td>
      <td>7/14/2005 0:00</td>
      <td>D3CIIILGP</td>
      <td>D3</td>
      <td>C</td>
      <td>III</td>
      <td>LGP</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 20.0 to 75.0 Horse...</td>
      <td>Texas</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydrostatic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>187</th>
      <td>1139826</td>
      <td>76000</td>
      <td>1041672</td>
      <td>11989</td>
      <td>121</td>
      <td>3.0</td>
      <td>2002</td>
      <td>5657.0</td>
      <td>Medium</td>
      <td>11/15/2007 0:00</td>
      <td>PC300LC7</td>
      <td>PC300</td>
      <td>NaN</td>
      <td>LC</td>
      <td>7</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 33.0 to 40.0 Metr...</td>
      <td>South Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>192</th>
      <td>1139841</td>
      <td>66000</td>
      <td>214394</td>
      <td>13854</td>
      <td>121</td>
      <td>3.0</td>
      <td>1993</td>
      <td>13048.0</td>
      <td>Medium</td>
      <td>5/3/2007 0:00</td>
      <td>D6HII</td>
      <td>D6</td>
      <td>H</td>
      <td>II</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Track Type Tractor, Dozer - 160.0 to 190.0 Hor...</td>
      <td>Arizona</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>Single Shank</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Differential Steer</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>213</th>
      <td>1139945</td>
      <td>32500</td>
      <td>999621</td>
      <td>2752</td>
      <td>121</td>
      <td>3.0</td>
      <td>1996</td>
      <td>2578.0</td>
      <td>Low</td>
      <td>5/20/2004 0:00</td>
      <td>D4CIII</td>
      <td>D4</td>
      <td>C</td>
      <td>III</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 75.0 to 85.0 Horse...</td>
      <td>Ohio</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>231</th>
      <td>1140003</td>
      <td>27000</td>
      <td>350034</td>
      <td>13824</td>
      <td>121</td>
      <td>3.0</td>
      <td>1997</td>
      <td>6658.0</td>
      <td>Medium</td>
      <td>3/8/2007 0:00</td>
      <td>D5CIIIXL</td>
      <td>D5</td>
      <td>C</td>
      <td>III</td>
      <td>XL</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 85.0 to 105.0 Hors...</td>
      <td>West Virginia</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydrostatic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>253</th>
      <td>1140077</td>
      <td>29000</td>
      <td>32010</td>
      <td>209</td>
      <td>121</td>
      <td>3.0</td>
      <td>1999</td>
      <td>2914.0</td>
      <td>Medium</td>
      <td>3/11/2004 0:00</td>
      <td>D37P-5</td>
      <td>D37</td>
      <td>P</td>
      <td>-5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 75.0 to 85.0 Horse...</td>
      <td>Alabama</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>254</th>
      <td>1140081</td>
      <td>85000</td>
      <td>1029985</td>
      <td>385</td>
      <td>121</td>
      <td>3.0</td>
      <td>2005</td>
      <td>1187.0</td>
      <td>Medium</td>
      <td>8/23/2007 0:00</td>
      <td>PC200LC7</td>
      <td>PC200</td>
      <td>NaN</td>
      <td>LC</td>
      <td>7</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 16.0 to 19.0 Metr...</td>
      <td>Alabama</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Manual</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>255</th>
      <td>1140084</td>
      <td>24500</td>
      <td>394814</td>
      <td>1561</td>
      <td>121</td>
      <td>3.0</td>
      <td>1992</td>
      <td>2963.0</td>
      <td>Low</td>
      <td>4/12/2007 0:00</td>
      <td>D4HIILGP</td>
      <td>D4</td>
      <td>H</td>
      <td>II</td>
      <td>LGP</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 85.0 to 105.0 Hors...</td>
      <td>Missouri</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Powershift</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <td>...</td>
    </tr>
    <tr>
      <th>400475</th>
      <td>6316125</td>
      <td>37000</td>
      <td>1285405</td>
      <td>25849</td>
      <td>149</td>
      <td>1.0</td>
      <td>1999</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6/22/2011 0:00</td>
      <td>SE240NLC-3</td>
      <td>SE240</td>
      <td>NLC</td>
      <td>-3</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 24.0 to 28.0 Metr...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>9' 6"</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400476</th>
      <td>6316137</td>
      <td>26000</td>
      <td>1884261</td>
      <td>12263</td>
      <td>149</td>
      <td>1.0</td>
      <td>1995</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/13/2011 0:00</td>
      <td>SE280LC-2</td>
      <td>SE280</td>
      <td>LC</td>
      <td>-2</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 24.0 to 28.0 Metr...</td>
      <td>Maryland</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400477</th>
      <td>6316151</td>
      <td>29000</td>
      <td>1851025</td>
      <td>17583</td>
      <td>149</td>
      <td>1.0</td>
      <td>1999</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/21/2011 0:00</td>
      <td>SE450LC-2</td>
      <td>SE450</td>
      <td>LC</td>
      <td>-2</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 40.0 to 50.0 Metr...</td>
      <td>Washington</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Hydraulic</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400479</th>
      <td>6316157</td>
      <td>18000</td>
      <td>1888406</td>
      <td>12268</td>
      <td>149</td>
      <td>1.0</td>
      <td>1996</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/13/2011 0:00</td>
      <td>SL150-2</td>
      <td>SL150</td>
      <td>NaN</td>
      <td>-2</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 150.0 to 175.0 Horsepower</td>
      <td>Maryland</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>20.5</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>400480</th>
      <td>6316159</td>
      <td>29500</td>
      <td>1805760</td>
      <td>12268</td>
      <td>149</td>
      <td>5.0</td>
      <td>1998</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/16/2011 0:00</td>
      <td>SL150-2</td>
      <td>SL150</td>
      <td>NaN</td>
      <td>-2</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 150.0 to 175.0 Horsepower</td>
      <td>Connecticut</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>400481</th>
      <td>6316160</td>
      <td>19000</td>
      <td>1836493</td>
      <td>12268</td>
      <td>149</td>
      <td>1.0</td>
      <td>1998</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/22/2011 0:00</td>
      <td>SL150-2</td>
      <td>SL150</td>
      <td>NaN</td>
      <td>-2</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 150.0 to 175.0 Horsepower</td>
      <td>Ohio</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>400482</th>
      <td>6316163</td>
      <td>26000</td>
      <td>1815419</td>
      <td>12269</td>
      <td>149</td>
      <td>1.0</td>
      <td>1996</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/21/2011 0:00</td>
      <td>SL180-2</td>
      <td>SL180</td>
      <td>NaN</td>
      <td>-2</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 200.0 to 225.0 Horsepower</td>
      <td>Washington</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>400483</th>
      <td>6316165</td>
      <td>38000</td>
      <td>1128625</td>
      <td>12269</td>
      <td>149</td>
      <td>5.0</td>
      <td>1998</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>SL180-2</td>
      <td>SL180</td>
      <td>NaN</td>
      <td>-2</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 200.0 to 225.0 Horsepower</td>
      <td>Massachusetts</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>400484</th>
      <td>6316166</td>
      <td>21500</td>
      <td>1423793</td>
      <td>12269</td>
      <td>149</td>
      <td>5.0</td>
      <td>1998</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6/24/2011 0:00</td>
      <td>SL180-2</td>
      <td>SL180</td>
      <td>NaN</td>
      <td>-2</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 200.0 to 225.0 Horsepower</td>
      <td>Connecticut</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>23.5</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>400485</th>
      <td>6316167</td>
      <td>24000</td>
      <td>1849156</td>
      <td>12270</td>
      <td>149</td>
      <td>1.0</td>
      <td>1995</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/13/2011 0:00</td>
      <td>SL250-2</td>
      <td>SL250</td>
      <td>NaN</td>
      <td>-2</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 250.0 to 275.0 Horsepower</td>
      <td>Maryland</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>26.5</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>400490</th>
      <td>6317149</td>
      <td>51000</td>
      <td>1895725</td>
      <td>36525</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>TX300LC1</td>
      <td>TX300</td>
      <td>LC</td>
      <td>1</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 28.0 to 33.0 Metr...</td>
      <td>Illinois</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400491</th>
      <td>6317150</td>
      <td>47500</td>
      <td>1838204</td>
      <td>17984</td>
      <td>149</td>
      <td>2.0</td>
      <td>2006</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/19/2011 0:00</td>
      <td>TXC225LC1</td>
      <td>TXC225</td>
      <td>LC</td>
      <td>1</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 21.0 to 24.0 Metr...</td>
      <td>Connecticut</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400499</th>
      <td>6317209</td>
      <td>90000</td>
      <td>1813371</td>
      <td>17990</td>
      <td>149</td>
      <td>5.0</td>
      <td>2008</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/2/2011 0:00</td>
      <td>TXC340LC2</td>
      <td>TXC340</td>
      <td>LC</td>
      <td>2</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 33.0 to 40.0 Metr...</td>
      <td>Connecticut</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydraulic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400500</th>
      <td>6317210</td>
      <td>90000</td>
      <td>1766986</td>
      <td>17990</td>
      <td>149</td>
      <td>5.0</td>
      <td>2008</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/2/2011 0:00</td>
      <td>TXC340LC2</td>
      <td>TXC340</td>
      <td>LC</td>
      <td>2</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 33.0 to 40.0 Metr...</td>
      <td>Connecticut</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400510</th>
      <td>6317698</td>
      <td>86000</td>
      <td>1892288</td>
      <td>17985</td>
      <td>149</td>
      <td>2.0</td>
      <td>2009</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/15/2011 0:00</td>
      <td>TXC225LC2</td>
      <td>TXC225</td>
      <td>LC</td>
      <td>2</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 21.0 to 24.0 Metr...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400511</th>
      <td>6317700</td>
      <td>83000</td>
      <td>1850370</td>
      <td>17984</td>
      <td>149</td>
      <td>1.0</td>
      <td>2007</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>TXC225LC1</td>
      <td>TXC225</td>
      <td>LC</td>
      <td>1</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 21.0 to 24.0 Metr...</td>
      <td>Missouri</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400512</th>
      <td>6317702</td>
      <td>46000</td>
      <td>1834476</td>
      <td>36525</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/8/2011 0:00</td>
      <td>TX300LC1</td>
      <td>TX300</td>
      <td>LC</td>
      <td>1</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 28.0 to 33.0 Metr...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400513</th>
      <td>6317703</td>
      <td>51000</td>
      <td>1882088</td>
      <td>36525</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>TX300LC1</td>
      <td>TX300</td>
      <td>LC</td>
      <td>1</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 28.0 to 33.0 Metr...</td>
      <td>Illinois</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydraulic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400514</th>
      <td>6317704</td>
      <td>43000</td>
      <td>1857056</td>
      <td>17989</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>TXC340LC1</td>
      <td>TXC340</td>
      <td>LC</td>
      <td>1</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 33.0 to 40.0 Metr...</td>
      <td>Illinois</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydraulic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400515</th>
      <td>6317705</td>
      <td>47000</td>
      <td>1854909</td>
      <td>17989</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>TXC340LC1</td>
      <td>TXC340</td>
      <td>LC</td>
      <td>1</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 33.0 to 40.0 Metr...</td>
      <td>Missouri</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400516</th>
      <td>6317706</td>
      <td>52500</td>
      <td>1845241</td>
      <td>17993</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>TXC470LC1</td>
      <td>TXC470</td>
      <td>LC</td>
      <td>1</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 40.0 to 50.0 Metr...</td>
      <td>Illinois</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400517</th>
      <td>6317707</td>
      <td>52500</td>
      <td>1801748</td>
      <td>17993</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>TXC470LC1</td>
      <td>TXC470</td>
      <td>LC</td>
      <td>1</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 40.0 to 50.0 Metr...</td>
      <td>Illinois</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydraulic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>400518</th>
      <td>6317711</td>
      <td>90000</td>
      <td>1871653</td>
      <td>18002</td>
      <td>149</td>
      <td>1.0</td>
      <td>2008</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>TXL5002</td>
      <td>TXL500</td>
      <td>NaN</td>
      <td>2</td>
      <td>NaN</td>
      <td>Medium</td>
      <td>Wheel Loader - 275.0 to 350.0 Horsepower</td>
      <td>Illinois</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>400973</th>
      <td>6327968</td>
      <td>6000</td>
      <td>1851301</td>
      <td>694</td>
      <td>149</td>
      <td>1.0</td>
      <td>1000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/4/2011 0:00</td>
      <td>TL262</td>
      <td>TL26</td>
      <td>NaN</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1751.0 to 2201.0 Lb Operat...</td>
      <td>Texas</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401047</th>
      <td>6328202</td>
      <td>4900</td>
      <td>1887565</td>
      <td>694</td>
      <td>149</td>
      <td>99.0</td>
      <td>1000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/16/2011 0:00</td>
      <td>TL262</td>
      <td>TL26</td>
      <td>NaN</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1751.0 to 2201.0 Lb Operat...</td>
      <td>Mississippi</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401072</th>
      <td>6333184</td>
      <td>11000</td>
      <td>1929774</td>
      <td>21436</td>
      <td>149</td>
      <td>1.0</td>
      <td>1000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/2/2011 0:00</td>
      <td>30NX2</td>
      <td>30</td>
      <td>NX</td>
      <td>2</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Maryland</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401078</th>
      <td>6333216</td>
      <td>13000</td>
      <td>1851957</td>
      <td>21450</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>80NX3</td>
      <td>80</td>
      <td>NX</td>
      <td>3</td>
      <td>NaN</td>
      <td>Small</td>
      <td>Hydraulic Excavator, Track - 8.0 to 11.0 Metri...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401120</th>
      <td>6333336</td>
      <td>10500</td>
      <td>1840702</td>
      <td>21439</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/2/2011 0:00</td>
      <td>35NX2</td>
      <td>35</td>
      <td>NX</td>
      <td>2</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Maryland</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401121</th>
      <td>6333337</td>
      <td>11000</td>
      <td>1830472</td>
      <td>21439</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/2/2011 0:00</td>
      <td>35NX2</td>
      <td>35</td>
      <td>NX</td>
      <td>2</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Maryland</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401122</th>
      <td>6333338</td>
      <td>11500</td>
      <td>1887659</td>
      <td>21439</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/2/2011 0:00</td>
      <td>35NX2</td>
      <td>35</td>
      <td>NX</td>
      <td>2</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Maryland</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>56908 rows × 53 columns</p>
</div>




```python
df2 = df.copy()
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
      <th>SalesID</th>
      <th>SalePrice</th>
      <th>MachineID</th>
      <th>ModelID</th>
      <th>datasource</th>
      <th>auctioneerID</th>
      <th>YearMade</th>
      <th>MachineHoursCurrentMeter</th>
      <th>UsageBand</th>
      <th>saledate</th>
      <th>fiModelDesc</th>
      <th>fiBaseModel</th>
      <th>fiSecondaryDesc</th>
      <th>fiModelSeries</th>
      <th>fiModelDescriptor</th>
      <th>ProductSize</th>
      <th>fiProductClassDesc</th>
      <th>state</th>
      <th>ProductGroup</th>
      <th>ProductGroupDesc</th>
      <th>Drive_System</th>
      <th>Enclosure</th>
      <th>Forks</th>
      <th>Pad_Type</th>
      <th>Ride_Control</th>
      <th>Stick</th>
      <th>Transmission</th>
      <th>Turbocharged</th>
      <th>Blade_Extension</th>
      <th>Blade_Width</th>
      <th>Enclosure_Type</th>
      <th>Engine_Horsepower</th>
      <th>Hydraulics</th>
      <th>Pushblock</th>
      <th>Ripper</th>
      <th>Scarifier</th>
      <th>Tip_Control</th>
      <th>Tire_Size</th>
      <th>Coupler</th>
      <th>Coupler_System</th>
      <th>Grouser_Tracks</th>
      <th>Hydraulics_Flow</th>
      <th>Track_Type</th>
      <th>Undercarriage_Pad_Width</th>
      <th>Stick_Length</th>
      <th>Thumb</th>
      <th>Pattern_Changer</th>
      <th>Grouser_Type</th>
      <th>Backhoe_Mounting</th>
      <th>Blade_Type</th>
      <th>Travel_Controls</th>
      <th>Differential_Type</th>
      <th>Steering_Controls</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1139246</td>
      <td>66000</td>
      <td>999089</td>
      <td>3157</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>68.0</td>
      <td>Low</td>
      <td>11/16/2006 0:00</td>
      <td>521D</td>
      <td>521</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Wheel Loader - 110.0 to 120.0 Horsepower</td>
      <td>Alabama</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1139249</td>
      <td>10000</td>
      <td>434808</td>
      <td>7009</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>2838.0</td>
      <td>High</td>
      <td>2/26/2004 0:00</td>
      <td>226</td>
      <td>226</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1351.0 to 1601.0 Lb Operat...</td>
      <td>New York</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1139253</td>
      <td>11000</td>
      <td>1057373</td>
      <td>17311</td>
      <td>121</td>
      <td>3.0</td>
      <td>2007</td>
      <td>722.0</td>
      <td>Medium</td>
      <td>7/23/2009 0:00</td>
      <td>S175</td>
      <td>S175</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1601.0 to 1751.0 Lb Operat...</td>
      <td>New York</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1139255</td>
      <td>26500</td>
      <td>1001274</td>
      <td>4605</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>508.0</td>
      <td>Low</td>
      <td>12/18/2008 0:00</td>
      <td>310G</td>
      <td>310</td>
      <td>G</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Arizona</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Extended</td>
      <td>Powershuttle</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1139256</td>
      <td>21000</td>
      <td>772701</td>
      <td>1937</td>
      <td>121</td>
      <td>3.0</td>
      <td>1993</td>
      <td>11540.0</td>
      <td>High</td>
      <td>8/26/2004 0:00</td>
      <td>790ELC</td>
      <td>790</td>
      <td>E</td>
      <td>NaN</td>
      <td>LC</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 21.0 to 24.0 Metr...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1139261</td>
      <td>27000</td>
      <td>902002</td>
      <td>3539</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>4883.0</td>
      <td>High</td>
      <td>11/17/2005 0:00</td>
      <td>416D</td>
      <td>416</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Illinois</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>Reversible</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>Yes</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1139272</td>
      <td>21500</td>
      <td>1036251</td>
      <td>36003</td>
      <td>121</td>
      <td>3.0</td>
      <td>2008</td>
      <td>302.0</td>
      <td>Low</td>
      <td>8/27/2009 0:00</td>
      <td>430HAG</td>
      <td>430</td>
      <td>HAG</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1139275</td>
      <td>65000</td>
      <td>1016474</td>
      <td>3883</td>
      <td>121</td>
      <td>3.0</td>
      <td>1000</td>
      <td>20700.0</td>
      <td>Medium</td>
      <td>8/9/2007 0:00</td>
      <td>988B</td>
      <td>988</td>
      <td>B</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Large</td>
      <td>Wheel Loader - 350.0 to 500.0 Horsepower</td>
      <td>Florida</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1139278</td>
      <td>24000</td>
      <td>1024998</td>
      <td>4605</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>1414.0</td>
      <td>Medium</td>
      <td>8/21/2008 0:00</td>
      <td>310G</td>
      <td>310</td>
      <td>G</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Oregon</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>Street</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1139282</td>
      <td>22500</td>
      <td>319906</td>
      <td>5255</td>
      <td>121</td>
      <td>3.0</td>
      <td>1998</td>
      <td>2764.0</td>
      <td>Low</td>
      <td>8/24/2006 0:00</td>
      <td>D31E</td>
      <td>D31</td>
      <td>E</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Track Type Tractor, Dozer - 20.0 to 75.0 Horse...</td>
      <td>Ohio</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>PAT</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1139284</td>
      <td>30500</td>
      <td>1068082</td>
      <td>3542</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>1921.0</td>
      <td>Medium</td>
      <td>1/26/2006 0:00</td>
      <td>420D</td>
      <td>420</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Texas</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1139290</td>
      <td>28000</td>
      <td>1058450</td>
      <td>5162</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>320.0</td>
      <td>Low</td>
      <td>1/3/2006 0:00</td>
      <td>214E</td>
      <td>214</td>
      <td>E</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>North Carolina</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1139291</td>
      <td>19000</td>
      <td>1004810</td>
      <td>4604</td>
      <td>121</td>
      <td>3.0</td>
      <td>1999</td>
      <td>2450.0</td>
      <td>Medium</td>
      <td>11/16/2006 0:00</td>
      <td>310E</td>
      <td>310</td>
      <td>E</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Arkansas</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Two Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1139292</td>
      <td>13500</td>
      <td>1026973</td>
      <td>9510</td>
      <td>121</td>
      <td>3.0</td>
      <td>1999</td>
      <td>1972.0</td>
      <td>Low</td>
      <td>6/14/2007 0:00</td>
      <td>334</td>
      <td>334</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1139299</td>
      <td>9500</td>
      <td>1002713</td>
      <td>21442</td>
      <td>121</td>
      <td>3.0</td>
      <td>2003</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>1/28/2010 0:00</td>
      <td>45NX</td>
      <td>45</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 4.0 to 5.0 Metric...</td>
      <td>Wisconsin</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>16 inch</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1139301</td>
      <td>12500</td>
      <td>125790</td>
      <td>7040</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>994.0</td>
      <td>Low</td>
      <td>3/9/2006 0:00</td>
      <td>302.5</td>
      <td>302.5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1139304</td>
      <td>11500</td>
      <td>1011914</td>
      <td>3177</td>
      <td>121</td>
      <td>3.0</td>
      <td>1991</td>
      <td>8005.0</td>
      <td>Medium</td>
      <td>11/17/2005 0:00</td>
      <td>580SUPER K</td>
      <td>580</td>
      <td>SUPER K</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Illinois</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Two Wheel Drive</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>20</th>
      <td>1139311</td>
      <td>41000</td>
      <td>1014135</td>
      <td>8867</td>
      <td>121</td>
      <td>3.0</td>
      <td>2000</td>
      <td>3259.0</td>
      <td>Medium</td>
      <td>5/18/2006 0:00</td>
      <td>JS260</td>
      <td>JS260</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 24.0 to 28.0 Metr...</td>
      <td>Kansas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>32 inch</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>21</th>
      <td>1139333</td>
      <td>34500</td>
      <td>999192</td>
      <td>3350</td>
      <td>121</td>
      <td>3.0</td>
      <td>1000</td>
      <td>16328.0</td>
      <td>Medium</td>
      <td>10/19/2006 0:00</td>
      <td>120G</td>
      <td>120</td>
      <td>G</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Motorgrader - 45.0 to 130.0 Horsepower</td>
      <td>Nevada</td>
      <td>MG</td>
      <td>Motor Graders</td>
      <td>No</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Powershift</td>
      <td>NaN</td>
      <td>Yes</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Base + 1 Function</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Sideshift &amp; Tip</td>
      <td>13"</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>22</th>
      <td>1139344</td>
      <td>26000</td>
      <td>1044500</td>
      <td>7040</td>
      <td>121</td>
      <td>3.0</td>
      <td>2005</td>
      <td>109.0</td>
      <td>Low</td>
      <td>10/25/2007 0:00</td>
      <td>302.5</td>
      <td>302.5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>Iowa</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>24</th>
      <td>1139348</td>
      <td>33000</td>
      <td>294562</td>
      <td>3542</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>1877.0</td>
      <td>Medium</td>
      <td>5/20/2004 0:00</td>
      <td>420D</td>
      <td>420</td>
      <td>D</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Backhoe Loader - 14.0 to 15.0 Ft Standard Digg...</td>
      <td>Texas</td>
      <td>BL</td>
      <td>Backhoe Loaders</td>
      <td>Four Wheel Drive</td>
      <td>OROPS</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Standard</td>
      <td>Standard</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>25</th>
      <td>1139351</td>
      <td>12500</td>
      <td>833838</td>
      <td>7009</td>
      <td>121</td>
      <td>3.0</td>
      <td>2003</td>
      <td>1028.0</td>
      <td>Medium</td>
      <td>3/9/2006 0:00</td>
      <td>226</td>
      <td>226</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 1351.0 to 1601.0 Lb Operat...</td>
      <td>Massachusetts</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>26</th>
      <td>1139354</td>
      <td>15500</td>
      <td>565440</td>
      <td>7040</td>
      <td>121</td>
      <td>3.0</td>
      <td>2003</td>
      <td>356.0</td>
      <td>Low</td>
      <td>3/9/2006 0:00</td>
      <td>302.5</td>
      <td>302.5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>California</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Manual</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>27</th>
      <td>1139356</td>
      <td>53000</td>
      <td>1004127</td>
      <td>25458</td>
      <td>121</td>
      <td>3.0</td>
      <td>2000</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>2/22/2007 0:00</td>
      <td>EX550STD</td>
      <td>EX550</td>
      <td>STD</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 50.0 to 66.0 Metr...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>28</th>
      <td>1139357</td>
      <td>46000</td>
      <td>44800</td>
      <td>19167</td>
      <td>121</td>
      <td>3.0</td>
      <td>2004</td>
      <td>904.0</td>
      <td>Low</td>
      <td>8/9/2007 0:00</td>
      <td>685B</td>
      <td>685</td>
      <td>B</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Motorgrader - 45.0 to 130.0 Horsepower</td>
      <td>Louisiana</td>
      <td>MG</td>
      <td>Motor Graders</td>
      <td>No</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>No</td>
      <td>Base + 1 Function</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>29</th>
      <td>1139358</td>
      <td>89000</td>
      <td>1018076</td>
      <td>1333</td>
      <td>121</td>
      <td>3.0</td>
      <td>1998</td>
      <td>10466.0</td>
      <td>Medium</td>
      <td>6/1/2006 0:00</td>
      <td>345BL</td>
      <td>345</td>
      <td>BL</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 40.0 to 50.0 Metr...</td>
      <td>Minnesota</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>15' 9"</td>
      <td>None or Unspecified</td>
      <td>Yes</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>30</th>
      <td>1139363</td>
      <td>51000</td>
      <td>871201</td>
      <td>1263</td>
      <td>121</td>
      <td>3.0</td>
      <td>1999</td>
      <td>15633.0</td>
      <td>High</td>
      <td>10/22/2010 0:00</td>
      <td>330BL</td>
      <td>330</td>
      <td>B</td>
      <td>NaN</td>
      <td>L</td>
      <td>Large / Medium</td>
      <td>Hydraulic Excavator, Track - 33.0 to 40.0 Metr...</td>
      <td>New Hampshire</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS w AC</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>31</th>
      <td>1139365</td>
      <td>14000</td>
      <td>973717</td>
      <td>9566</td>
      <td>121</td>
      <td>3.0</td>
      <td>2001</td>
      <td>2097.0</td>
      <td>Medium</td>
      <td>3/22/2007 0:00</td>
      <td>873</td>
      <td>873</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Skid Steer Loader - 2201.0 to 2701.0 Lb Operat...</td>
      <td>Idaho</td>
      <td>SSL</td>
      <td>Skid Steer Loaders</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>32</th>
      <td>1139367</td>
      <td>31500</td>
      <td>1036100</td>
      <td>9109</td>
      <td>121</td>
      <td>3.0</td>
      <td>1995</td>
      <td>7542.0</td>
      <td>Medium</td>
      <td>7/27/2006 0:00</td>
      <td>WA250</td>
      <td>WA250</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Wheel Loader - 120.0 to 135.0 Horsepower</td>
      <td>North Carolina</td>
      <td>WL</td>
      <td>Wheel Loader</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>Conventional</td>
    </tr>
    <tr>
      <th>33</th>
      <td>1139369</td>
      <td>14000</td>
      <td>1050658</td>
      <td>1918</td>
      <td>121</td>
      <td>3.0</td>
      <td>1000</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>1/28/2010 0:00</td>
      <td>750BLT</td>
      <td>750</td>
      <td>B</td>
      <td>NaN</td>
      <td>LT</td>
      <td>Medium</td>
      <td>Track Type Tractor, Dozer - 130.0 to 160.0 Hor...</td>
      <td>Michigan</td>
      <td>TTT</td>
      <td>Track Type Tractors</td>
      <td>NaN</td>
      <td>OROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Hydrostatic</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2 Valve</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
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
      <td>...</td>
    </tr>
    <tr>
      <th>401092</th>
      <td>6333256</td>
      <td>10500</td>
      <td>1872420</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401093</th>
      <td>6333257</td>
      <td>10500</td>
      <td>1945018</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401094</th>
      <td>6333258</td>
      <td>11500</td>
      <td>1874065</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/13/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Maryland</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401095</th>
      <td>6333259</td>
      <td>10500</td>
      <td>1872639</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401096</th>
      <td>6333260</td>
      <td>10000</td>
      <td>1816341</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Georgia</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401097</th>
      <td>6333261</td>
      <td>8500</td>
      <td>1843949</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/28/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401098</th>
      <td>6333262</td>
      <td>10500</td>
      <td>1791341</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401099</th>
      <td>6333263</td>
      <td>11000</td>
      <td>1833174</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401100</th>
      <td>6333264</td>
      <td>10500</td>
      <td>1791370</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401101</th>
      <td>6333270</td>
      <td>10000</td>
      <td>1799208</td>
      <td>21437</td>
      <td>149</td>
      <td>1.0</td>
      <td>2004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>12/14/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>North Carolina</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Rubber</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401102</th>
      <td>6333272</td>
      <td>10500</td>
      <td>1927142</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401103</th>
      <td>6333273</td>
      <td>12500</td>
      <td>1789856</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Georgia</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401104</th>
      <td>6333275</td>
      <td>10500</td>
      <td>1924623</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401105</th>
      <td>6333276</td>
      <td>10000</td>
      <td>1835350</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401106</th>
      <td>6333278</td>
      <td>10500</td>
      <td>1944702</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401107</th>
      <td>6333279</td>
      <td>12500</td>
      <td>1866563</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Georgia</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401108</th>
      <td>6333280</td>
      <td>10500</td>
      <td>1851633</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401109</th>
      <td>6333281</td>
      <td>10500</td>
      <td>1798958</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8/16/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401110</th>
      <td>6333282</td>
      <td>10500</td>
      <td>1878866</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>9/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Georgia</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Auxiliary</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401111</th>
      <td>6333283</td>
      <td>10000</td>
      <td>1874235</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401112</th>
      <td>6333284</td>
      <td>10500</td>
      <td>1887654</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401113</th>
      <td>6333285</td>
      <td>10500</td>
      <td>1817165</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401114</th>
      <td>6333287</td>
      <td>12500</td>
      <td>1918242</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>11/15/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Texas</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401115</th>
      <td>6333290</td>
      <td>10000</td>
      <td>1843374</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401116</th>
      <td>6333302</td>
      <td>8500</td>
      <td>1825337</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401117</th>
      <td>6333307</td>
      <td>10000</td>
      <td>1821747</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401118</th>
      <td>6333311</td>
      <td>9500</td>
      <td>1828862</td>
      <td>21437</td>
      <td>149</td>
      <td>2.0</td>
      <td>2006</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>35N</td>
      <td>35</td>
      <td>N</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 3.0 to 4.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401119</th>
      <td>6333335</td>
      <td>8500</td>
      <td>1798293</td>
      <td>21435</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>30NX</td>
      <td>30</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401123</th>
      <td>6333341</td>
      <td>9000</td>
      <td>1903570</td>
      <td>21435</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>30NX</td>
      <td>30</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>401124</th>
      <td>6333342</td>
      <td>7750</td>
      <td>1926965</td>
      <td>21435</td>
      <td>149</td>
      <td>2.0</td>
      <td>2005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>10/25/2011 0:00</td>
      <td>30NX</td>
      <td>30</td>
      <td>NX</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Mini</td>
      <td>Hydraulic Excavator, Track - 2.0 to 3.0 Metric...</td>
      <td>Florida</td>
      <td>TEX</td>
      <td>Track Excavators</td>
      <td>NaN</td>
      <td>EROPS</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Standard</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>None or Unspecified</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Steel</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>None or Unspecified</td>
      <td>Double</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>344217 rows × 53 columns</p>
</div>




```python
df2 = df2.fillna(value=5)
```


```python
df.SalePrice.apply(lambda x: x - x/2)
```




    0         33000.0
    1         28500.0
    2          5000.0
    3         19250.0
    4          5500.0
    5         13250.0
    6         10500.0
    7         13500.0
    8         10750.0
    9         32500.0
    10        12000.0
    11        11250.0
    12        18000.0
    13        15250.0
    14        14000.0
    15         9500.0
    16         6750.0
    17         4750.0
    18         6250.0
    19         5750.0
    20        20500.0
    21        17250.0
    22        13000.0
    23        36500.0
    24        16500.0
    25         6250.0
    26         7750.0
    27        26500.0
    28        23000.0
    29        44500.0
               ...   
    401095     5250.0
    401096     5000.0
    401097     4250.0
    401098     5250.0
    401099     5500.0
    401100     5250.0
    401101     5000.0
    401102     5250.0
    401103     6250.0
    401104     5250.0
    401105     5000.0
    401106     5250.0
    401107     6250.0
    401108     5250.0
    401109     5250.0
    401110     5250.0
    401111     5000.0
    401112     5250.0
    401113     5250.0
    401114     6250.0
    401115     5000.0
    401116     4250.0
    401117     5000.0
    401118     4750.0
    401119     4250.0
    401120     5250.0
    401121     5500.0
    401122     5750.0
    401123     4500.0
    401124     3875.0
    Name: SalePrice, Length: 401125, dtype: float64




```python
df.state.str.lower()
```




    0                alabama
    1         north carolina
    2               new york
    3                  texas
    4               new york
    5                arizona
    6                florida
    7               illinois
    8                  texas
    9                florida
    10                oregon
    11                  ohio
    12                  ohio
    13                 texas
    14        north carolina
    15              arkansas
    16               florida
    17             wisconsin
    18        north carolina
    19              illinois
    20                kansas
    21                nevada
    22                  iowa
    23                 maine
    24                 texas
    25         massachusetts
    26            california
    27                 texas
    28             louisiana
    29             minnesota
                   ...      
    401095    north carolina
    401096           georgia
    401097           florida
    401098           florida
    401099    north carolina
    401100           florida
    401101    north carolina
    401102           florida
    401103           georgia
    401104           florida
    401105           florida
    401106           florida
    401107           georgia
    401108           florida
    401109           florida
    401110           georgia
    401111           florida
    401112           florida
    401113           florida
    401114             texas
    401115           florida
    401116           florida
    401117           florida
    401118           florida
    401119           florida
    401120          maryland
    401121          maryland
    401122          maryland
    401123           florida
    401124           florida
    Name: state, Length: 401125, dtype: object




```python
rdf = pd.DataFrame(np.random.randn(10, 4))
```


```python
rdf
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-1.374623</td>
      <td>-0.105875</td>
      <td>0.479018</td>
      <td>0.219594</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.078818</td>
      <td>0.170885</td>
      <td>0.768719</td>
      <td>1.568310</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.347130</td>
      <td>-0.109166</td>
      <td>0.604294</td>
      <td>0.473510</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.668734</td>
      <td>0.531239</td>
      <td>-1.383066</td>
      <td>-0.112314</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.138093</td>
      <td>-0.738175</td>
      <td>-0.181868</td>
      <td>1.206248</td>
    </tr>
    <tr>
      <th>5</th>
      <td>-0.322649</td>
      <td>0.759812</td>
      <td>0.177191</td>
      <td>0.583329</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.807030</td>
      <td>0.908411</td>
      <td>0.620137</td>
      <td>-2.250824</td>
    </tr>
    <tr>
      <th>7</th>
      <td>-0.386825</td>
      <td>0.939877</td>
      <td>-0.134417</td>
      <td>1.592687</td>
    </tr>
    <tr>
      <th>8</th>
      <td>-1.100843</td>
      <td>0.809626</td>
      <td>0.247976</td>
      <td>0.961758</td>
    </tr>
    <tr>
      <th>9</th>
      <td>-0.885225</td>
      <td>-0.393236</td>
      <td>0.495758</td>
      <td>-0.748179</td>
    </tr>
  </tbody>
</table>
</div>




```python
rdf2 = pd.DataFrame(np.random.randn(10, 4))
rdf2
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-0.932595</td>
      <td>0.631837</td>
      <td>-0.280079</td>
      <td>-0.755231</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.110607</td>
      <td>0.257214</td>
      <td>0.351674</td>
      <td>-0.820209</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-1.235152</td>
      <td>-1.047121</td>
      <td>1.537491</td>
      <td>-0.367671</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-0.099268</td>
      <td>0.471312</td>
      <td>-1.552961</td>
      <td>1.507591</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.117356</td>
      <td>-0.538943</td>
      <td>1.134315</td>
      <td>-1.075415</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1.827224</td>
      <td>-0.427184</td>
      <td>1.770247</td>
      <td>-1.563801</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.305766</td>
      <td>0.799718</td>
      <td>2.191818</td>
      <td>1.125852</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1.788014</td>
      <td>-0.647355</td>
      <td>2.121841</td>
      <td>1.203579</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0.739412</td>
      <td>-0.682946</td>
      <td>-0.248781</td>
      <td>-0.648947</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0.471974</td>
      <td>-0.379885</td>
      <td>1.932680</td>
      <td>0.539144</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.concat([rdf,rdf2])
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-1.374623</td>
      <td>-0.105875</td>
      <td>0.479018</td>
      <td>0.219594</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1.078818</td>
      <td>0.170885</td>
      <td>0.768719</td>
      <td>1.568310</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0.347130</td>
      <td>-0.109166</td>
      <td>0.604294</td>
      <td>0.473510</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.668734</td>
      <td>0.531239</td>
      <td>-1.383066</td>
      <td>-0.112314</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.138093</td>
      <td>-0.738175</td>
      <td>-0.181868</td>
      <td>1.206248</td>
    </tr>
    <tr>
      <th>5</th>
      <td>-0.322649</td>
      <td>0.759812</td>
      <td>0.177191</td>
      <td>0.583329</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.807030</td>
      <td>0.908411</td>
      <td>0.620137</td>
      <td>-2.250824</td>
    </tr>
    <tr>
      <th>7</th>
      <td>-0.386825</td>
      <td>0.939877</td>
      <td>-0.134417</td>
      <td>1.592687</td>
    </tr>
    <tr>
      <th>8</th>
      <td>-1.100843</td>
      <td>0.809626</td>
      <td>0.247976</td>
      <td>0.961758</td>
    </tr>
    <tr>
      <th>9</th>
      <td>-0.885225</td>
      <td>-0.393236</td>
      <td>0.495758</td>
      <td>-0.748179</td>
    </tr>
    <tr>
      <th>0</th>
      <td>-0.932595</td>
      <td>0.631837</td>
      <td>-0.280079</td>
      <td>-0.755231</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.110607</td>
      <td>0.257214</td>
      <td>0.351674</td>
      <td>-0.820209</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-1.235152</td>
      <td>-1.047121</td>
      <td>1.537491</td>
      <td>-0.367671</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-0.099268</td>
      <td>0.471312</td>
      <td>-1.552961</td>
      <td>1.507591</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.117356</td>
      <td>-0.538943</td>
      <td>1.134315</td>
      <td>-1.075415</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1.827224</td>
      <td>-0.427184</td>
      <td>1.770247</td>
      <td>-1.563801</td>
    </tr>
    <tr>
      <th>6</th>
      <td>0.305766</td>
      <td>0.799718</td>
      <td>2.191818</td>
      <td>1.125852</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1.788014</td>
      <td>-0.647355</td>
      <td>2.121841</td>
      <td>1.203579</td>
    </tr>
    <tr>
      <th>8</th>
      <td>0.739412</td>
      <td>-0.682946</td>
      <td>-0.248781</td>
      <td>-0.648947</td>
    </tr>
    <tr>
      <th>9</th>
      <td>0.471974</td>
      <td>-0.379885</td>
      <td>1.932680</td>
      <td>0.539144</td>
    </tr>
  </tbody>
</table>
</div>




```python
left = pd.DataFrame({'key': ['foo', 'bar'], 'lval': [1, 2]})
right = pd.DataFrame({'key': ['foo', 'bar'], 'rval': [4, 5]})
pd.merge(left, right, on='key')
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
      <th>key</th>
      <th>lval</th>
      <th>rval</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>1</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>bar</td>
      <td>2</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = pd.DataFrame({'A': ['foo', 'bar', 'foo', 'bar',
                         'foo', 'bar', 'foo', 'foo'],
                   'B': ['one', 'one', 'two', 'three',
                        'two', 'two', 'one', 'three'],
                   'C': np.random.randn(8),
                   'D': np.random.randn(8)})
```


```python
df2.groupby('A').sum()
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
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>A</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bar</th>
      <td>-1.058701</td>
      <td>1.660846</td>
    </tr>
    <tr>
      <th>foo</th>
      <td>0.471787</td>
      <td>-0.228091</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.groupby(['A','B']).sum()
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
      <th></th>
      <th>C</th>
      <th>D</th>
    </tr>
    <tr>
      <th>A</th>
      <th>B</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">bar</th>
      <th>one</th>
      <td>0.334745</td>
      <td>2.440534</td>
    </tr>
    <tr>
      <th>three</th>
      <td>-1.637937</td>
      <td>0.508615</td>
    </tr>
    <tr>
      <th>two</th>
      <td>0.244491</td>
      <td>-1.288304</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">foo</th>
      <th>one</th>
      <td>-0.732526</td>
      <td>-1.391596</td>
    </tr>
    <tr>
      <th>three</th>
      <td>0.212081</td>
      <td>0.469666</td>
    </tr>
    <tr>
      <th>two</th>
      <td>0.992233</td>
      <td>0.693839</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = pd.DataFrame({'A': ['one', 'one', 'two', 'three'] * 3,
                   'B': ['A', 'B', 'C'] * 4,
                   'C': ['foo', 'foo', 'foo', 'bar', 'bar', 'bar'] * 2,
                   'D': np.random.randn(12),
                   'E': np.random.randn(12)})
```


```python
df2
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
      <th>A</th>
      <th>B</th>
      <th>C</th>
      <th>D</th>
      <th>E</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>one</td>
      <td>A</td>
      <td>foo</td>
      <td>-2.697845</td>
      <td>-0.138629</td>
    </tr>
    <tr>
      <th>1</th>
      <td>one</td>
      <td>B</td>
      <td>foo</td>
      <td>-0.637220</td>
      <td>0.584159</td>
    </tr>
    <tr>
      <th>2</th>
      <td>two</td>
      <td>C</td>
      <td>foo</td>
      <td>-0.966879</td>
      <td>-0.235519</td>
    </tr>
    <tr>
      <th>3</th>
      <td>three</td>
      <td>A</td>
      <td>bar</td>
      <td>0.786954</td>
      <td>-0.041641</td>
    </tr>
    <tr>
      <th>4</th>
      <td>one</td>
      <td>B</td>
      <td>bar</td>
      <td>0.911488</td>
      <td>-0.943525</td>
    </tr>
    <tr>
      <th>5</th>
      <td>one</td>
      <td>C</td>
      <td>bar</td>
      <td>0.367786</td>
      <td>0.873214</td>
    </tr>
    <tr>
      <th>6</th>
      <td>two</td>
      <td>A</td>
      <td>foo</td>
      <td>-0.531484</td>
      <td>0.188678</td>
    </tr>
    <tr>
      <th>7</th>
      <td>three</td>
      <td>B</td>
      <td>foo</td>
      <td>-0.643770</td>
      <td>0.545261</td>
    </tr>
    <tr>
      <th>8</th>
      <td>one</td>
      <td>C</td>
      <td>foo</td>
      <td>-1.377770</td>
      <td>0.904680</td>
    </tr>
    <tr>
      <th>9</th>
      <td>one</td>
      <td>A</td>
      <td>bar</td>
      <td>0.383375</td>
      <td>-2.258967</td>
    </tr>
    <tr>
      <th>10</th>
      <td>two</td>
      <td>B</td>
      <td>bar</td>
      <td>0.319521</td>
      <td>1.656798</td>
    </tr>
    <tr>
      <th>11</th>
      <td>three</td>
      <td>C</td>
      <td>bar</td>
      <td>1.535191</td>
      <td>-0.785640</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.pivot_table(df2, values='D', index=['A', 'B'], columns=['C'])
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
      <th>C</th>
      <th>bar</th>
      <th>foo</th>
    </tr>
    <tr>
      <th>A</th>
      <th>B</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="3" valign="top">one</th>
      <th>A</th>
      <td>0.383375</td>
      <td>-2.697845</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.911488</td>
      <td>-0.637220</td>
    </tr>
    <tr>
      <th>C</th>
      <td>0.367786</td>
      <td>-1.377770</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">three</th>
      <th>A</th>
      <td>0.786954</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>B</th>
      <td>NaN</td>
      <td>-0.643770</td>
    </tr>
    <tr>
      <th>C</th>
      <td>1.535191</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">two</th>
      <th>A</th>
      <td>NaN</td>
      <td>-0.531484</td>
    </tr>
    <tr>
      <th>B</th>
      <td>0.319521</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>C</th>
      <td>NaN</td>
      <td>-0.966879</td>
    </tr>
  </tbody>
</table>
</div>


