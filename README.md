

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```


```python
averagepricefile = 'average_price_by_zip_code.csv'
housingdatafile = 'kc_house_data.csv'
censusdatafile = 'ac2015_king_county_wa_zip_code_data.csv'
```


```python
average_price = pd.read_csv(averagepricefile)
average_price.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>zipcode</th>
      <th>Average_Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>98001</td>
      <td>2.808047e+05</td>
    </tr>
    <tr>
      <th>1</th>
      <td>98002</td>
      <td>2.342840e+05</td>
    </tr>
    <tr>
      <th>2</th>
      <td>98003</td>
      <td>2.941113e+05</td>
    </tr>
    <tr>
      <th>3</th>
      <td>98004</td>
      <td>1.355927e+06</td>
    </tr>
    <tr>
      <th>4</th>
      <td>98005</td>
      <td>8.101649e+05</td>
    </tr>
  </tbody>
</table>
</div>




```python
housing_df = pd.read_csv(housingdatafile)
housing_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>...</th>
      <th>grade</th>
      <th>sqft_above</th>
      <th>sqft_basement</th>
      <th>yr_built</th>
      <th>yr_renovated</th>
      <th>zipcode</th>
      <th>lat</th>
      <th>long</th>
      <th>sqft_living15</th>
      <th>sqft_lot15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>20141013T000000</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1180</td>
      <td>0</td>
      <td>1955</td>
      <td>0</td>
      <td>98178</td>
      <td>47.5112</td>
      <td>-122.257</td>
      <td>1340</td>
      <td>5650</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6414100192</td>
      <td>20141209T000000</td>
      <td>538000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>2570</td>
      <td>7242</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>2170</td>
      <td>400</td>
      <td>1951</td>
      <td>1991</td>
      <td>98125</td>
      <td>47.7210</td>
      <td>-122.319</td>
      <td>1690</td>
      <td>7639</td>
    </tr>
    <tr>
      <th>2</th>
      <td>5631500400</td>
      <td>20150225T000000</td>
      <td>180000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>770</td>
      <td>10000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>6</td>
      <td>770</td>
      <td>0</td>
      <td>1933</td>
      <td>0</td>
      <td>98028</td>
      <td>47.7379</td>
      <td>-122.233</td>
      <td>2720</td>
      <td>8062</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2487200875</td>
      <td>20141209T000000</td>
      <td>604000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>1960</td>
      <td>5000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>7</td>
      <td>1050</td>
      <td>910</td>
      <td>1965</td>
      <td>0</td>
      <td>98136</td>
      <td>47.5208</td>
      <td>-122.393</td>
      <td>1360</td>
      <td>5000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1954400510</td>
      <td>20150218T000000</td>
      <td>510000.0</td>
      <td>3</td>
      <td>2.00</td>
      <td>1680</td>
      <td>8080</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>8</td>
      <td>1680</td>
      <td>0</td>
      <td>1987</td>
      <td>0</td>
      <td>98074</td>
      <td>47.6168</td>
      <td>-122.045</td>
      <td>1800</td>
      <td>7503</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 21 columns</p>
</div>




```python
census_df = pd.read_csv(censusdatafile)
census_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>zipcode</th>
      <th>Total_Population</th>
      <th>Men</th>
      <th>Women</th>
      <th>Under_5_Years</th>
      <th>5_to_9_Years</th>
      <th>10_to_14_Years</th>
      <th>15_to_19_Years</th>
      <th>20_to_24_Years</th>
      <th>25_to_34_Years</th>
      <th>...</th>
      <th>Walk_%</th>
      <th>Other_Transporation_%</th>
      <th>Work_At_Home_%</th>
      <th>Average_Commute_Time_in_Minutes</th>
      <th>Employed</th>
      <th>Private_Wage_and_Salary_Workers_%</th>
      <th>Government_Workers_%</th>
      <th>Self_Employed_%</th>
      <th>Unpaid_Family_Workers_%</th>
      <th>Unemployment_Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>98001</td>
      <td>32194</td>
      <td>15665</td>
      <td>16529</td>
      <td>1831</td>
      <td>2181</td>
      <td>2123</td>
      <td>2456</td>
      <td>2110</td>
      <td>3661</td>
      <td>...</td>
      <td>0.4</td>
      <td>1.1</td>
      <td>3.6</td>
      <td>29.8</td>
      <td>15530</td>
      <td>79.5</td>
      <td>15.7</td>
      <td>4.7</td>
      <td>0.1</td>
      <td>7.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>98002</td>
      <td>33817</td>
      <td>16354</td>
      <td>17463</td>
      <td>3074</td>
      <td>2573</td>
      <td>2315</td>
      <td>2046</td>
      <td>2119</td>
      <td>4682</td>
      <td>...</td>
      <td>2.3</td>
      <td>1.6</td>
      <td>2.4</td>
      <td>30.1</td>
      <td>14272</td>
      <td>83.9</td>
      <td>11.8</td>
      <td>4.0</td>
      <td>0.3</td>
      <td>8.9</td>
    </tr>
    <tr>
      <th>2</th>
      <td>98003</td>
      <td>46008</td>
      <td>22650</td>
      <td>23358</td>
      <td>3075</td>
      <td>2840</td>
      <td>3085</td>
      <td>3170</td>
      <td>3834</td>
      <td>6513</td>
      <td>...</td>
      <td>2.9</td>
      <td>0.3</td>
      <td>5.0</td>
      <td>29.8</td>
      <td>21432</td>
      <td>85.4</td>
      <td>9.8</td>
      <td>4.5</td>
      <td>0.3</td>
      <td>8.1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>98004</td>
      <td>32587</td>
      <td>16167</td>
      <td>16420</td>
      <td>1743</td>
      <td>1243</td>
      <td>1703</td>
      <td>1686</td>
      <td>1652</td>
      <td>6743</td>
      <td>...</td>
      <td>13.6</td>
      <td>1.4</td>
      <td>8.9</td>
      <td>19.3</td>
      <td>17207</td>
      <td>89.4</td>
      <td>5.4</td>
      <td>5.1</td>
      <td>0.2</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>98005</td>
      <td>17733</td>
      <td>9104</td>
      <td>8629</td>
      <td>1033</td>
      <td>928</td>
      <td>933</td>
      <td>923</td>
      <td>1082</td>
      <td>3032</td>
      <td>...</td>
      <td>2.8</td>
      <td>2.0</td>
      <td>6.6</td>
      <td>21.9</td>
      <td>9006</td>
      <td>85.0</td>
      <td>7.8</td>
      <td>6.6</td>
      <td>0.5</td>
      <td>7.3</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 58 columns</p>
</div>




```python
merged_df = pd.merge(housing_df, census_df, on='zipcode')
merged_df.head(20)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>date</th>
      <th>price</th>
      <th>bedrooms</th>
      <th>bathrooms</th>
      <th>sqft_living</th>
      <th>sqft_lot</th>
      <th>floors</th>
      <th>waterfront</th>
      <th>view</th>
      <th>...</th>
      <th>Walk_%</th>
      <th>Other_Transporation_%</th>
      <th>Work_At_Home_%</th>
      <th>Average_Commute_Time_in_Minutes</th>
      <th>Employed</th>
      <th>Private_Wage_and_Salary_Workers_%</th>
      <th>Government_Workers_%</th>
      <th>Self_Employed_%</th>
      <th>Unpaid_Family_Workers_%</th>
      <th>Unemployment_Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7129300520</td>
      <td>20141013T000000</td>
      <td>221900.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5650</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>1</th>
      <td>4060000240</td>
      <td>20140623T000000</td>
      <td>205425.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>880</td>
      <td>6780</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>4058801670</td>
      <td>20140717T000000</td>
      <td>445000.0</td>
      <td>3</td>
      <td>2.25</td>
      <td>2100</td>
      <td>8201</td>
      <td>1.0</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2976800796</td>
      <td>20140925T000000</td>
      <td>236000.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1300</td>
      <td>5898</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>6874200960</td>
      <td>20150227T000000</td>
      <td>170000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>860</td>
      <td>5265</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>5</th>
      <td>4268200055</td>
      <td>20150501T000000</td>
      <td>245000.0</td>
      <td>3</td>
      <td>1.75</td>
      <td>1740</td>
      <td>11547</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3969300030</td>
      <td>20140723T000000</td>
      <td>165000.0</td>
      <td>4</td>
      <td>1.00</td>
      <td>1000</td>
      <td>7134</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>7</th>
      <td>3969300030</td>
      <td>20141229T000000</td>
      <td>239900.0</td>
      <td>4</td>
      <td>1.00</td>
      <td>1000</td>
      <td>7134</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1678400105</td>
      <td>20150212T000000</td>
      <td>339000.0</td>
      <td>4</td>
      <td>1.50</td>
      <td>2390</td>
      <td>7480</td>
      <td>1.5</td>
      <td>0</td>
      <td>2</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2172000075</td>
      <td>20140623T000000</td>
      <td>290900.0</td>
      <td>2</td>
      <td>2.00</td>
      <td>1610</td>
      <td>17600</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1180003090</td>
      <td>20140906T000000</td>
      <td>190000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>630</td>
      <td>6000</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>11</th>
      <td>561000075</td>
      <td>20141231T000000</td>
      <td>260000.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1180</td>
      <td>5350</td>
      <td>1.5</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1123049053</td>
      <td>20150213T000000</td>
      <td>360000.0</td>
      <td>4</td>
      <td>2.50</td>
      <td>1840</td>
      <td>9611</td>
      <td>2.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>13</th>
      <td>7812800565</td>
      <td>20140814T000000</td>
      <td>289500.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>960</td>
      <td>6400</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>14</th>
      <td>3348401740</td>
      <td>20150127T000000</td>
      <td>188000.0</td>
      <td>2</td>
      <td>1.50</td>
      <td>1120</td>
      <td>17487</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>15</th>
      <td>2171400197</td>
      <td>20140918T000000</td>
      <td>350000.0</td>
      <td>5</td>
      <td>3.00</td>
      <td>2520</td>
      <td>5500</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>16</th>
      <td>5476200160</td>
      <td>20140725T000000</td>
      <td>164808.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1250</td>
      <td>5411</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>17</th>
      <td>9368700223</td>
      <td>20150202T000000</td>
      <td>310000.0</td>
      <td>4</td>
      <td>3.00</td>
      <td>2010</td>
      <td>7426</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>18</th>
      <td>7567600045</td>
      <td>20140827T000000</td>
      <td>825000.0</td>
      <td>2</td>
      <td>1.00</td>
      <td>1150</td>
      <td>12775</td>
      <td>1.0</td>
      <td>1</td>
      <td>4</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
    <tr>
      <th>19</th>
      <td>2171400126</td>
      <td>20140605T000000</td>
      <td>269000.0</td>
      <td>3</td>
      <td>1.00</td>
      <td>1690</td>
      <td>4250</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.3</td>
      <td>2.7</td>
      <td>31.0</td>
      <td>12091</td>
      <td>79.9</td>
      <td>15.3</td>
      <td>4.6</td>
      <td>0.3</td>
      <td>5.8</td>
    </tr>
  </tbody>
</table>
<p>20 rows × 78 columns</p>
</div>




```python
merged_census_df = pd.merge(census_df, average_price, on='zipcode')
merged_census_df.head(20)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>zipcode</th>
      <th>Total_Population</th>
      <th>Men</th>
      <th>Women</th>
      <th>Under_5_Years</th>
      <th>5_to_9_Years</th>
      <th>10_to_14_Years</th>
      <th>15_to_19_Years</th>
      <th>20_to_24_Years</th>
      <th>25_to_34_Years</th>
      <th>...</th>
      <th>Other_Transporation_%</th>
      <th>Work_At_Home_%</th>
      <th>Average_Commute_Time_in_Minutes</th>
      <th>Employed</th>
      <th>Private_Wage_and_Salary_Workers_%</th>
      <th>Government_Workers_%</th>
      <th>Self_Employed_%</th>
      <th>Unpaid_Family_Workers_%</th>
      <th>Unemployment_Rate</th>
      <th>Average_Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>98001</td>
      <td>32194</td>
      <td>15665</td>
      <td>16529</td>
      <td>1831</td>
      <td>2181</td>
      <td>2123</td>
      <td>2456</td>
      <td>2110</td>
      <td>3661</td>
      <td>...</td>
      <td>1.1</td>
      <td>3.6</td>
      <td>29.8</td>
      <td>15530</td>
      <td>79.5</td>
      <td>15.7</td>
      <td>4.7</td>
      <td>0.1</td>
      <td>7.5</td>
      <td>2.808047e+05</td>
    </tr>
    <tr>
      <th>1</th>
      <td>98002</td>
      <td>33817</td>
      <td>16354</td>
      <td>17463</td>
      <td>3074</td>
      <td>2573</td>
      <td>2315</td>
      <td>2046</td>
      <td>2119</td>
      <td>4682</td>
      <td>...</td>
      <td>1.6</td>
      <td>2.4</td>
      <td>30.1</td>
      <td>14272</td>
      <td>83.9</td>
      <td>11.8</td>
      <td>4.0</td>
      <td>0.3</td>
      <td>8.9</td>
      <td>2.342840e+05</td>
    </tr>
    <tr>
      <th>2</th>
      <td>98003</td>
      <td>46008</td>
      <td>22650</td>
      <td>23358</td>
      <td>3075</td>
      <td>2840</td>
      <td>3085</td>
      <td>3170</td>
      <td>3834</td>
      <td>6513</td>
      <td>...</td>
      <td>0.3</td>
      <td>5.0</td>
      <td>29.8</td>
      <td>21432</td>
      <td>85.4</td>
      <td>9.8</td>
      <td>4.5</td>
      <td>0.3</td>
      <td>8.1</td>
      <td>2.941113e+05</td>
    </tr>
    <tr>
      <th>3</th>
      <td>98004</td>
      <td>32587</td>
      <td>16167</td>
      <td>16420</td>
      <td>1743</td>
      <td>1243</td>
      <td>1703</td>
      <td>1686</td>
      <td>1652</td>
      <td>6743</td>
      <td>...</td>
      <td>1.4</td>
      <td>8.9</td>
      <td>19.3</td>
      <td>17207</td>
      <td>89.4</td>
      <td>5.4</td>
      <td>5.1</td>
      <td>0.2</td>
      <td>6.0</td>
      <td>1.355927e+06</td>
    </tr>
    <tr>
      <th>4</th>
      <td>98005</td>
      <td>17733</td>
      <td>9104</td>
      <td>8629</td>
      <td>1033</td>
      <td>928</td>
      <td>933</td>
      <td>923</td>
      <td>1082</td>
      <td>3032</td>
      <td>...</td>
      <td>2.0</td>
      <td>6.6</td>
      <td>21.9</td>
      <td>9006</td>
      <td>85.0</td>
      <td>7.8</td>
      <td>6.6</td>
      <td>0.5</td>
      <td>7.3</td>
      <td>8.101649e+05</td>
    </tr>
    <tr>
      <th>5</th>
      <td>98006</td>
      <td>37519</td>
      <td>18633</td>
      <td>18886</td>
      <td>1989</td>
      <td>2377</td>
      <td>2797</td>
      <td>2401</td>
      <td>1977</td>
      <td>3771</td>
      <td>...</td>
      <td>1.0</td>
      <td>8.5</td>
      <td>26.0</td>
      <td>18235</td>
      <td>83.8</td>
      <td>9.9</td>
      <td>6.0</td>
      <td>0.3</td>
      <td>6.6</td>
      <td>8.596848e+05</td>
    </tr>
    <tr>
      <th>6</th>
      <td>98007</td>
      <td>26269</td>
      <td>13954</td>
      <td>12315</td>
      <td>2206</td>
      <td>1225</td>
      <td>979</td>
      <td>1009</td>
      <td>1747</td>
      <td>7172</td>
      <td>...</td>
      <td>0.9</td>
      <td>4.1</td>
      <td>21.6</td>
      <td>14444</td>
      <td>90.2</td>
      <td>6.1</td>
      <td>3.6</td>
      <td>0.1</td>
      <td>5.6</td>
      <td>6.171051e+05</td>
    </tr>
    <tr>
      <th>7</th>
      <td>98008</td>
      <td>24751</td>
      <td>12510</td>
      <td>12241</td>
      <td>1236</td>
      <td>1695</td>
      <td>1422</td>
      <td>1436</td>
      <td>1034</td>
      <td>2933</td>
      <td>...</td>
      <td>1.5</td>
      <td>6.2</td>
      <td>22.9</td>
      <td>12214</td>
      <td>84.4</td>
      <td>10.1</td>
      <td>5.4</td>
      <td>0.1</td>
      <td>6.6</td>
      <td>6.455074e+05</td>
    </tr>
    <tr>
      <th>8</th>
      <td>98010</td>
      <td>4918</td>
      <td>2476</td>
      <td>2442</td>
      <td>336</td>
      <td>384</td>
      <td>224</td>
      <td>357</td>
      <td>199</td>
      <td>385</td>
      <td>...</td>
      <td>0.8</td>
      <td>2.9</td>
      <td>34.1</td>
      <td>2341</td>
      <td>80.4</td>
      <td>16.8</td>
      <td>2.4</td>
      <td>0.3</td>
      <td>4.8</td>
      <td>4.236660e+05</td>
    </tr>
    <tr>
      <th>9</th>
      <td>98011</td>
      <td>31650</td>
      <td>15471</td>
      <td>16179</td>
      <td>2169</td>
      <td>1956</td>
      <td>1797</td>
      <td>1848</td>
      <td>1633</td>
      <td>4829</td>
      <td>...</td>
      <td>0.8</td>
      <td>6.8</td>
      <td>28.5</td>
      <td>16774</td>
      <td>82.7</td>
      <td>13.3</td>
      <td>3.6</td>
      <td>0.4</td>
      <td>6.3</td>
      <td>4.903515e+05</td>
    </tr>
    <tr>
      <th>10</th>
      <td>98014</td>
      <td>6973</td>
      <td>3565</td>
      <td>3408</td>
      <td>428</td>
      <td>403</td>
      <td>424</td>
      <td>535</td>
      <td>208</td>
      <td>808</td>
      <td>...</td>
      <td>1.7</td>
      <td>8.4</td>
      <td>35.8</td>
      <td>3964</td>
      <td>83.4</td>
      <td>8.7</td>
      <td>7.6</td>
      <td>0.3</td>
      <td>5.1</td>
      <td>4.556171e+05</td>
    </tr>
    <tr>
      <th>11</th>
      <td>98019</td>
      <td>11143</td>
      <td>5295</td>
      <td>5848</td>
      <td>630</td>
      <td>908</td>
      <td>899</td>
      <td>1002</td>
      <td>378</td>
      <td>964</td>
      <td>...</td>
      <td>1.5</td>
      <td>6.2</td>
      <td>36.4</td>
      <td>5672</td>
      <td>81.5</td>
      <td>15.1</td>
      <td>3.5</td>
      <td>0.0</td>
      <td>7.8</td>
      <td>4.247887e+05</td>
    </tr>
    <tr>
      <th>12</th>
      <td>98022</td>
      <td>21567</td>
      <td>10560</td>
      <td>11007</td>
      <td>1225</td>
      <td>1157</td>
      <td>1515</td>
      <td>1252</td>
      <td>1208</td>
      <td>2490</td>
      <td>...</td>
      <td>1.9</td>
      <td>5.7</td>
      <td>34.1</td>
      <td>10562</td>
      <td>77.9</td>
      <td>13.0</td>
      <td>8.4</td>
      <td>0.6</td>
      <td>6.2</td>
      <td>3.157093e+05</td>
    </tr>
    <tr>
      <th>13</th>
      <td>98023</td>
      <td>50065</td>
      <td>25122</td>
      <td>24943</td>
      <td>3429</td>
      <td>3187</td>
      <td>3357</td>
      <td>3843</td>
      <td>3417</td>
      <td>7259</td>
      <td>...</td>
      <td>1.6</td>
      <td>4.5</td>
      <td>32.3</td>
      <td>25296</td>
      <td>79.5</td>
      <td>15.0</td>
      <td>5.2</td>
      <td>0.2</td>
      <td>8.0</td>
      <td>2.867328e+05</td>
    </tr>
    <tr>
      <th>14</th>
      <td>98024</td>
      <td>5847</td>
      <td>3068</td>
      <td>2779</td>
      <td>234</td>
      <td>331</td>
      <td>589</td>
      <td>371</td>
      <td>256</td>
      <td>549</td>
      <td>...</td>
      <td>0.6</td>
      <td>8.4</td>
      <td>30.0</td>
      <td>2780</td>
      <td>73.4</td>
      <td>13.2</td>
      <td>13.5</td>
      <td>0.0</td>
      <td>7.4</td>
      <td>5.805268e+05</td>
    </tr>
    <tr>
      <th>15</th>
      <td>98027</td>
      <td>27855</td>
      <td>13459</td>
      <td>14396</td>
      <td>1587</td>
      <td>1868</td>
      <td>1630</td>
      <td>1590</td>
      <td>1289</td>
      <td>3443</td>
      <td>...</td>
      <td>1.9</td>
      <td>8.0</td>
      <td>28.7</td>
      <td>14967</td>
      <td>82.8</td>
      <td>12.4</td>
      <td>4.8</td>
      <td>0.0</td>
      <td>4.7</td>
      <td>6.169906e+05</td>
    </tr>
    <tr>
      <th>16</th>
      <td>98028</td>
      <td>21568</td>
      <td>10520</td>
      <td>11048</td>
      <td>1557</td>
      <td>1434</td>
      <td>1539</td>
      <td>1075</td>
      <td>1071</td>
      <td>2674</td>
      <td>...</td>
      <td>1.9</td>
      <td>9.3</td>
      <td>32.1</td>
      <td>10783</td>
      <td>82.0</td>
      <td>10.6</td>
      <td>7.3</td>
      <td>0.1</td>
      <td>6.3</td>
      <td>4.624800e+05</td>
    </tr>
    <tr>
      <th>17</th>
      <td>98029</td>
      <td>26586</td>
      <td>12476</td>
      <td>14110</td>
      <td>2028</td>
      <td>2288</td>
      <td>1886</td>
      <td>1276</td>
      <td>928</td>
      <td>3936</td>
      <td>...</td>
      <td>0.7</td>
      <td>9.3</td>
      <td>29.9</td>
      <td>13667</td>
      <td>85.2</td>
      <td>9.6</td>
      <td>5.1</td>
      <td>0.2</td>
      <td>6.7</td>
      <td>6.126536e+05</td>
    </tr>
    <tr>
      <th>18</th>
      <td>98030</td>
      <td>36730</td>
      <td>18168</td>
      <td>18562</td>
      <td>3188</td>
      <td>3316</td>
      <td>2687</td>
      <td>2796</td>
      <td>2376</td>
      <td>6294</td>
      <td>...</td>
      <td>0.7</td>
      <td>4.2</td>
      <td>30.2</td>
      <td>16092</td>
      <td>80.1</td>
      <td>14.1</td>
      <td>5.6</td>
      <td>0.2</td>
      <td>8.3</td>
      <td>2.961880e+05</td>
    </tr>
    <tr>
      <th>19</th>
      <td>98031</td>
      <td>36390</td>
      <td>18233</td>
      <td>18157</td>
      <td>2232</td>
      <td>2215</td>
      <td>2153</td>
      <td>3075</td>
      <td>3084</td>
      <td>5171</td>
      <td>...</td>
      <td>1.3</td>
      <td>3.7</td>
      <td>30.7</td>
      <td>17983</td>
      <td>81.5</td>
      <td>13.2</td>
      <td>5.1</td>
      <td>0.2</td>
      <td>8.8</td>
      <td>3.005399e+05</td>
    </tr>
  </tbody>
</table>
<p>20 rows × 59 columns</p>
</div>




```python
len(merged_census_df)
```




    70




```python
plt.scatter(merged_df['price'], merged_df['Median_Household_Income'], s=1)
plt.xlim(0,3500000)
plt.show()
```


![png](output_8_0.png)



```python
fig, ax = plt.subplots()
fit = np.polyfit(merged_df['price'], merged_df['Median_Household_Income'], deg=1)
ax.plot(merged_df['price'], fit[0] * merged_df['price'] + fit[1], color='red')
ax.scatter(merged_df['price'], merged_df['Median_Household_Income'], s=1)
plt.xlim(0,3500000)
plt.ylim(25000,180000)
plt.show()
```


![png](output_9_0.png)



```python
pd.Series(merged_df['price']).corr(merged_df['Median_Household_Income'])
```




    0.38386791196030995




```python
plt.scatter(merged_df['price'], merged_df['Unemployment_Rate'], s=1)
plt.xlim(0,3500000)
plt.show()
```


![png](output_11_0.png)



```python
fig, ax = plt.subplots()
fit = np.polyfit(merged_df['price'], merged_df['Unemployment_Rate'], deg=1)
ax.plot(merged_df['price'], fit[0] * merged_df['price'] + fit[1], color='red')
ax.scatter(merged_df['price'], merged_df['Unemployment_Rate'], s=1)
plt.xlim(0,3500000)
plt.ylim(2,11)
plt.show()
```


![png](output_12_0.png)



```python
pd.Series(merged_df['price']).corr(merged_df['Unemployment_Rate'])
```




    -0.29458854717368049




```python
plt.scatter(merged_df['price'], merged_df['Income_Per_Capita'], s=1)
plt.xlim(0,3000000)
plt.show()
```


![png](output_14_0.png)



```python
fig, ax = plt.subplots()
fit = np.polyfit(merged_df['price'], merged_df['Income_Per_Capita'], deg=1)
ax.plot(merged_df['price'], fit[0] * merged_df['price'] + fit[1], color='red')
ax.scatter(merged_df['price'], merged_df['Income_Per_Capita'], s=1)
plt.xlim(0,3500000)
plt.ylim(0,100000)
plt.show()
```


![png](output_15_0.png)



```python
pd.Series(merged_df['price']).corr(merged_df['Income_Per_Capita'])
```




    0.57136726461975051




```python
plt.scatter(merged_df['price'], merged_df['Mean_Household_Income'], s=1)
plt.xlim(0,3000000)
plt.show()
```


![png](output_17_0.png)



```python
fig, ax = plt.subplots()
fit = np.polyfit(merged_df['price'], merged_df['Mean_Household_Income'], deg=1)
ax.plot(merged_df['price'], fit[0] * merged_df['price'] + fit[1], color='red')
ax.scatter(merged_df['price'], merged_df['Mean_Household_Income'], s=1)
plt.xlim(0,3500000)
plt.ylim(50000,200000)
plt.show()
```


![png](output_18_0.png)



```python
pd.Series(merged_df['price']).corr(merged_df['Mean_Household_Income'])
```




    0.5017464786098903




```python
plt.scatter(merged_census_df['Average_Price'], merged_census_df['Median_Household_Income'], s=1)
plt.xlim(0,2500000)
plt.show()
```


![png](output_20_0.png)



```python
fig, ax = plt.subplots()
fit = np.polyfit(merged_census_df['Average_Price'], merged_census_df['Median_Household_Income'], deg=1)
ax.plot(merged_census_df['Average_Price'], fit[0] * merged_census_df['Average_Price'] + fit[1], color='red')
ax.scatter(merged_census_df['Average_Price'], merged_census_df['Median_Household_Income'], s=1)
plt.title('King County Average Home Sales Price vs. Median Household Income by Zipcode')
plt.xlabel('Average Home Sales Price $ May 2014 - May 2015')
plt.ylabel('Median Household Income $ in 2015')
plt.xlim(0,2500000)
plt.ylim(40000,180000)
xlabels = [format(label, ',.0f') for label in ax.get_xticks()]
ax.set_xticklabels(xlabels)
ylabels = [format(label, ',.0f') for label in ax.get_yticks()]
ax.set_yticklabels(ylabels)
plt.show()
```


![png](output_21_0.png)



```python
pd.Series(merged_census_df['Average_Price']).corr(merged_census_df['Median_Household_Income'])
```




    0.66682985760035884




```python
plt.scatter(merged_census_df['Average_Price'], merged_census_df['Mean_Household_Income'], s=1)
plt.xlim(0,2500000)
plt.show()
```


![png](output_23_0.png)



```python
fig, ax = plt.subplots()
fit = np.polyfit(merged_census_df['Average_Price'], merged_census_df['Mean_Household_Income'], deg=1)
ax.plot(merged_census_df['Average_Price'], fit[0] * merged_census_df['Average_Price'] + fit[1], color='red')
ax.scatter(merged_census_df['Average_Price'], merged_census_df['Mean_Household_Income'], s=1)
plt.title('King County Average Home Sales Price vs. Average Household Income by Zipcode')
plt.xlabel('Average Home Sales Price $ May 2014 - May 2015')
plt.ylabel('Average Household Income $ in 2015')
plt.xlim(0,2500000)
plt.ylim(50000,300000)
xlabels = [format(label, ',.0f') for label in ax.get_xticks()]
ax.set_xticklabels(xlabels)
ylabels = [format(label, ',.0f') for label in ax.get_yticks()]
ax.set_yticklabels(ylabels)
plt.show()
```


![png](output_24_0.png)



```python
pd.Series(merged_census_df['Average_Price']).corr(merged_census_df['Mean_Household_Income'])
```




    0.83227853973800592




```python
plt.scatter(merged_census_df['Average_Price'], merged_census_df['Unemployment_Rate'], s=1)
plt.xlim(0,2500000)
plt.show()
```


![png](output_26_0.png)



```python
fig, ax = plt.subplots()
fit = np.polyfit(merged_census_df['Average_Price'], merged_census_df['Unemployment_Rate'], deg=1)
ax.plot(merged_census_df['Average_Price'], fit[0] * merged_census_df['Average_Price'] + fit[1], color='red')
ax.scatter(merged_census_df['Average_Price'], merged_census_df['Unemployment_Rate'], s=1)
plt.title('King County Average Home Sales Price vs. Unemployment Rate by Zipcode')
plt.xlabel('Average Home Sales Price $ May 2014 - May 2015')
plt.ylabel('Unemployment Rate % in 2015')
plt.xlim(0,2500000)
xlabels = [format(label, ',.0f') for label in ax.get_xticks()]
ax.set_xticklabels(xlabels)
plt.show()
```


![png](output_27_0.png)



```python
pd.Series(merged_census_df['Average_Price']).corr(merged_census_df['Unemployment_Rate'])
```




    -0.50458755517041354




```python
plt.scatter(merged_census_df['Average_Price'], merged_census_df['Income_Per_Capita'], s=1)
plt.xlim(0,2500000)
plt.show()
```


![png](output_29_0.png)



```python
fig, ax = plt.subplots()
fit = np.polyfit(merged_census_df['Average_Price'], merged_census_df['Income_Per_Capita'], deg=1)
ax.plot(merged_census_df['Average_Price'], fit[0] * merged_census_df['Average_Price'] + fit[1], color='red')
ax.scatter(merged_census_df['Average_Price'], merged_census_df['Income_Per_Capita'], s=1)
plt.title('King County Average Home Sales Price vs. Income Per Capita by Zipcode')
plt.xlabel('Average Home Sales Price $ May 2014 - May 2015')
plt.ylabel('Income Per Capita $ in 2015')
plt.xlim(0,2500000)
xlabels = [format(label, ',.0f') for label in ax.get_xticks()]
ax.set_xticklabels(xlabels)
ylabels = [format(label, ',.0f') for label in ax.get_yticks()]
ax.set_yticklabels(ylabels)
plt.show()
```


![png](output_30_0.png)



```python
pd.Series(merged_census_df['Average_Price']).corr(merged_census_df['Income_Per_Capita'])
```




    0.89584942246614685




```python
top_five_zip_codes = average_price.groupby(["zipcode"]).sum().nlargest(5,"Average_Price")
print("Top Five Zipcodes With Highest Average Home Sales Prices in King County May 2014 - May 2015")
pd.options.display.float_format = '{:.2f}'.format
top_five_zip_codes
```

    Top Five Zipcodes With Highest Average Home Sales Prices in King County May 2014 - May 2015
    




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average_Price</th>
    </tr>
    <tr>
      <th>zipcode</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>98039</th>
      <td>2160606.60</td>
    </tr>
    <tr>
      <th>98004</th>
      <td>1355927.08</td>
    </tr>
    <tr>
      <th>98040</th>
      <td>1194230.02</td>
    </tr>
    <tr>
      <th>98112</th>
      <td>1095499.34</td>
    </tr>
    <tr>
      <th>98102</th>
      <td>901258.27</td>
    </tr>
  </tbody>
</table>
</div>




```python
merged_census_df = merged_census_df.set_index('zipcode')
merged_census_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total_Population</th>
      <th>Men</th>
      <th>Women</th>
      <th>Under_5_Years</th>
      <th>5_to_9_Years</th>
      <th>10_to_14_Years</th>
      <th>15_to_19_Years</th>
      <th>20_to_24_Years</th>
      <th>25_to_34_Years</th>
      <th>35_to_44_Years</th>
      <th>...</th>
      <th>Other_Transporation_%</th>
      <th>Work_At_Home_%</th>
      <th>Average_Commute_Time_in_Minutes</th>
      <th>Employed</th>
      <th>Private_Wage_and_Salary_Workers_%</th>
      <th>Government_Workers_%</th>
      <th>Self_Employed_%</th>
      <th>Unpaid_Family_Workers_%</th>
      <th>Unemployment_Rate</th>
      <th>Average_Price</th>
    </tr>
    <tr>
      <th>zipcode</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>98001</th>
      <td>32194</td>
      <td>15665</td>
      <td>16529</td>
      <td>1831</td>
      <td>2181</td>
      <td>2123</td>
      <td>2456</td>
      <td>2110</td>
      <td>3661</td>
      <td>4380</td>
      <td>...</td>
      <td>1.10</td>
      <td>3.60</td>
      <td>29.80</td>
      <td>15530</td>
      <td>79.50</td>
      <td>15.70</td>
      <td>4.70</td>
      <td>0.10</td>
      <td>7.50</td>
      <td>280804.69</td>
    </tr>
    <tr>
      <th>98002</th>
      <td>33817</td>
      <td>16354</td>
      <td>17463</td>
      <td>3074</td>
      <td>2573</td>
      <td>2315</td>
      <td>2046</td>
      <td>2119</td>
      <td>4682</td>
      <td>4837</td>
      <td>...</td>
      <td>1.60</td>
      <td>2.40</td>
      <td>30.10</td>
      <td>14272</td>
      <td>83.90</td>
      <td>11.80</td>
      <td>4.00</td>
      <td>0.30</td>
      <td>8.90</td>
      <td>234284.04</td>
    </tr>
    <tr>
      <th>98003</th>
      <td>46008</td>
      <td>22650</td>
      <td>23358</td>
      <td>3075</td>
      <td>2840</td>
      <td>3085</td>
      <td>3170</td>
      <td>3834</td>
      <td>6513</td>
      <td>5336</td>
      <td>...</td>
      <td>0.30</td>
      <td>5.00</td>
      <td>29.80</td>
      <td>21432</td>
      <td>85.40</td>
      <td>9.80</td>
      <td>4.50</td>
      <td>0.30</td>
      <td>8.10</td>
      <td>294111.28</td>
    </tr>
    <tr>
      <th>98004</th>
      <td>32587</td>
      <td>16167</td>
      <td>16420</td>
      <td>1743</td>
      <td>1243</td>
      <td>1703</td>
      <td>1686</td>
      <td>1652</td>
      <td>6743</td>
      <td>4545</td>
      <td>...</td>
      <td>1.40</td>
      <td>8.90</td>
      <td>19.30</td>
      <td>17207</td>
      <td>89.40</td>
      <td>5.40</td>
      <td>5.10</td>
      <td>0.20</td>
      <td>6.00</td>
      <td>1355927.08</td>
    </tr>
    <tr>
      <th>98005</th>
      <td>17733</td>
      <td>9104</td>
      <td>8629</td>
      <td>1033</td>
      <td>928</td>
      <td>933</td>
      <td>923</td>
      <td>1082</td>
      <td>3032</td>
      <td>2702</td>
      <td>...</td>
      <td>2.00</td>
      <td>6.60</td>
      <td>21.90</td>
      <td>9006</td>
      <td>85.00</td>
      <td>7.80</td>
      <td>6.60</td>
      <td>0.50</td>
      <td>7.30</td>
      <td>810164.88</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 58 columns</p>
</div>




```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df.iloc[24,17], merged_census_df.iloc[24,18], merged_census_df.iloc[24,19], merged_census_df.iloc[24,21]]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0, 0.05, 0, 0)

plt.title("Ethnicity Distribution for 98039 in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_34_0.png)



```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df.iloc[3,17], merged_census_df.iloc[3,18], merged_census_df.iloc[3,19], merged_census_df.iloc[3,21]]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0, 0.05, 0, 0)

plt.title("Ethnicity Distribution for 98004 in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_35_0.png)



```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df.iloc[25,17], merged_census_df.iloc[25,18], merged_census_df.iloc[25,19], merged_census_df.iloc[25,21]]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0, 0.05, 0, 0)

plt.title("Ethnicity Distribution for 98040 in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_36_0.png)



```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df.iloc[48,17], merged_census_df.iloc[48,18], merged_census_df.iloc[48,19], merged_census_df.iloc[48,21]]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0, 0.05, 0, 0)

plt.title("Ethnicity Distribution for 98112 in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_37_0.png)



```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df.iloc[41,17], merged_census_df.iloc[41,18], merged_census_df.iloc[41,19], merged_census_df.iloc[41,21]]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0, 0.05, 0, 0)

plt.title("Ethnicity Distribution for 98102 in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_38_0.png)



```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df['Hispanic_%'].mean(), merged_census_df['White_%'].mean(), merged_census_df['Black_%'].mean(), merged_census_df['Asian_%'].mean()]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0, 0.05, 0, 0)

plt.title("Ethnicity Distribution for King County in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_39_0.png)



```python
bottom_five_zip_codes = average_price.groupby(["zipcode"]).sum().nsmallest(5,"Average_Price")
print("Bottom Five Zipcodes With Lowest Average Home Sales Prices in King County May 2014 - May 2015")
pd.options.display.float_format = '{:.2f}'.format
bottom_five_zip_codes
```

    Bottom Five Zipcodes With Lowest Average Home Sales Prices in King County May 2014 - May 2015
    




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average_Price</th>
    </tr>
    <tr>
      <th>zipcode</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>98002</th>
      <td>234284.04</td>
    </tr>
    <tr>
      <th>98168</th>
      <td>240328.37</td>
    </tr>
    <tr>
      <th>98032</th>
      <td>251296.24</td>
    </tr>
    <tr>
      <th>98001</th>
      <td>280804.69</td>
    </tr>
    <tr>
      <th>98148</th>
      <td>284908.60</td>
    </tr>
  </tbody>
</table>
</div>




```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df.iloc[1,17], merged_census_df.iloc[1,18], merged_census_df.iloc[1,19], merged_census_df.iloc[1,21]]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0.05, 0, 0, 0)

plt.title("Ethnicity Distribution for 98002 in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_41_0.png)



```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df.iloc[64,17], merged_census_df.iloc[64,18], merged_census_df.iloc[64,19], merged_census_df.iloc[64,21]]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0.05, 0, 0, 0)

plt.title("Ethnicity Distribution for 98168 in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_42_0.png)



```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df.iloc[20,17], merged_census_df.iloc[20,18], merged_census_df.iloc[20,19], merged_census_df.iloc[20,21]]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0.05, 0, 0, 0)

plt.title("Ethnicity Distribution for 98032 in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_43_0.png)



```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df.iloc[0,17], merged_census_df.iloc[0,18], merged_census_df.iloc[0,19], merged_census_df.iloc[0,21]]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0.05, 0, 0, 0)

plt.title("Ethnicity Distribution for 98001 in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_44_0.png)



```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_census_df.iloc[61,17], merged_census_df.iloc[61,18], merged_census_df.iloc[61,19], merged_census_df.iloc[61,21]]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0.05, 0, 0, 0)

plt.title("Ethnicity Distribution for 98148 in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_45_0.png)



```python
merged_high_price_df = pd.merge(top_five_zip_codes, census_df, on='zipcode')
merged_high_price_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>level_0</th>
      <th>index</th>
      <th>zipcode</th>
      <th>Average_Price</th>
      <th>Total_Population</th>
      <th>Men</th>
      <th>Women</th>
      <th>Under_5_Years</th>
      <th>5_to_9_Years</th>
      <th>10_to_14_Years</th>
      <th>...</th>
      <th>Walk_%</th>
      <th>Other_Transporation_%</th>
      <th>Work_At_Home_%</th>
      <th>Average_Commute_Time_in_Minutes</th>
      <th>Employed</th>
      <th>Private_Wage_and_Salary_Workers_%</th>
      <th>Government_Workers_%</th>
      <th>Self_Employed_%</th>
      <th>Unpaid_Family_Workers_%</th>
      <th>Unemployment_Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>98039</td>
      <td>2160606.60</td>
      <td>3120</td>
      <td>1530</td>
      <td>1590</td>
      <td>115</td>
      <td>253</td>
      <td>352</td>
      <td>...</td>
      <td>1.00</td>
      <td>1.20</td>
      <td>4.90</td>
      <td>19.80</td>
      <td>1057</td>
      <td>81.00</td>
      <td>9.50</td>
      <td>9.10</td>
      <td>0.50</td>
      <td>2.40</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>98004</td>
      <td>1355927.08</td>
      <td>32587</td>
      <td>16167</td>
      <td>16420</td>
      <td>1743</td>
      <td>1243</td>
      <td>1703</td>
      <td>...</td>
      <td>13.60</td>
      <td>1.40</td>
      <td>8.90</td>
      <td>19.30</td>
      <td>17207</td>
      <td>89.40</td>
      <td>5.40</td>
      <td>5.10</td>
      <td>0.20</td>
      <td>6.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>2</td>
      <td>98040</td>
      <td>1194230.02</td>
      <td>24120</td>
      <td>11742</td>
      <td>12378</td>
      <td>1128</td>
      <td>1790</td>
      <td>2135</td>
      <td>...</td>
      <td>1.70</td>
      <td>2.20</td>
      <td>10.30</td>
      <td>23.20</td>
      <td>10585</td>
      <td>80.20</td>
      <td>10.60</td>
      <td>9.10</td>
      <td>0.10</td>
      <td>5.10</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>3</td>
      <td>98112</td>
      <td>1095499.34</td>
      <td>22230</td>
      <td>11333</td>
      <td>10897</td>
      <td>1197</td>
      <td>1042</td>
      <td>988</td>
      <td>...</td>
      <td>8.80</td>
      <td>6.80</td>
      <td>10.70</td>
      <td>23.40</td>
      <td>12734</td>
      <td>76.50</td>
      <td>13.80</td>
      <td>9.60</td>
      <td>0.20</td>
      <td>5.30</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>4</td>
      <td>98102</td>
      <td>901258.27</td>
      <td>23655</td>
      <td>12849</td>
      <td>10806</td>
      <td>830</td>
      <td>298</td>
      <td>216</td>
      <td>...</td>
      <td>18.30</td>
      <td>6.50</td>
      <td>5.50</td>
      <td>24.40</td>
      <td>17991</td>
      <td>84.40</td>
      <td>10.80</td>
      <td>4.80</td>
      <td>0.00</td>
      <td>4.00</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 61 columns</p>
</div>




```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_high_price_df['Hispanic_%'].mean(), merged_high_price_df['White_%'].mean(), merged_high_price_df['Black_%'].mean(), merged_high_price_df['Asian_%'].mean()]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0, 0.05, 0, 0)

plt.title("Ethnicity Distribution for Top Five Zipcodes in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_47_0.png)



```python
merged_low_price_df = pd.merge(bottom_five_zip_codes, census_df, on='zipcode')
merged_low_price_df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>zipcode</th>
      <th>Average_Price</th>
      <th>Total_Population</th>
      <th>Men</th>
      <th>Women</th>
      <th>Under_5_Years</th>
      <th>5_to_9_Years</th>
      <th>10_to_14_Years</th>
      <th>15_to_19_Years</th>
      <th>20_to_24_Years</th>
      <th>...</th>
      <th>Walk_%</th>
      <th>Other_Transporation_%</th>
      <th>Work_At_Home_%</th>
      <th>Average_Commute_Time_in_Minutes</th>
      <th>Employed</th>
      <th>Private_Wage_and_Salary_Workers_%</th>
      <th>Government_Workers_%</th>
      <th>Self_Employed_%</th>
      <th>Unpaid_Family_Workers_%</th>
      <th>Unemployment_Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>98002</td>
      <td>234284.04</td>
      <td>33817</td>
      <td>16354</td>
      <td>17463</td>
      <td>3074</td>
      <td>2573</td>
      <td>2315</td>
      <td>2046</td>
      <td>2119</td>
      <td>...</td>
      <td>2.30</td>
      <td>1.60</td>
      <td>2.40</td>
      <td>30.10</td>
      <td>14272</td>
      <td>83.90</td>
      <td>11.80</td>
      <td>4.00</td>
      <td>0.30</td>
      <td>8.90</td>
    </tr>
    <tr>
      <th>1</th>
      <td>98168</td>
      <td>240328.37</td>
      <td>32569</td>
      <td>16803</td>
      <td>15766</td>
      <td>2422</td>
      <td>2136</td>
      <td>2152</td>
      <td>1739</td>
      <td>2172</td>
      <td>...</td>
      <td>1.90</td>
      <td>2.10</td>
      <td>2.40</td>
      <td>26.20</td>
      <td>15655</td>
      <td>80.90</td>
      <td>12.10</td>
      <td>6.80</td>
      <td>0.10</td>
      <td>8.60</td>
    </tr>
    <tr>
      <th>2</th>
      <td>98032</td>
      <td>251296.24</td>
      <td>36368</td>
      <td>18318</td>
      <td>18050</td>
      <td>2898</td>
      <td>2699</td>
      <td>2096</td>
      <td>2080</td>
      <td>3351</td>
      <td>...</td>
      <td>2.60</td>
      <td>3.00</td>
      <td>2.00</td>
      <td>32.10</td>
      <td>17036</td>
      <td>84.20</td>
      <td>10.80</td>
      <td>4.80</td>
      <td>0.10</td>
      <td>8.70</td>
    </tr>
    <tr>
      <th>3</th>
      <td>98001</td>
      <td>280804.69</td>
      <td>32194</td>
      <td>15665</td>
      <td>16529</td>
      <td>1831</td>
      <td>2181</td>
      <td>2123</td>
      <td>2456</td>
      <td>2110</td>
      <td>...</td>
      <td>0.40</td>
      <td>1.10</td>
      <td>3.60</td>
      <td>29.80</td>
      <td>15530</td>
      <td>79.50</td>
      <td>15.70</td>
      <td>4.70</td>
      <td>0.10</td>
      <td>7.50</td>
    </tr>
    <tr>
      <th>4</th>
      <td>98148</td>
      <td>284908.60</td>
      <td>10659</td>
      <td>5413</td>
      <td>5246</td>
      <td>757</td>
      <td>714</td>
      <td>732</td>
      <td>713</td>
      <td>862</td>
      <td>...</td>
      <td>2.40</td>
      <td>2.80</td>
      <td>3.40</td>
      <td>25.40</td>
      <td>5255</td>
      <td>78.60</td>
      <td>13.80</td>
      <td>7.60</td>
      <td>0.10</td>
      <td>5.80</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 59 columns</p>
</div>




```python
races = ["Hispanic", "White", "Black", "Asian"]
percentages = [merged_low_price_df['Hispanic_%'].mean(), merged_low_price_df['White_%'].mean(), merged_low_price_df['Black_%'].mean(), merged_low_price_df['Asian_%'].mean()]
colors = ["yellowgreen", "lightskyblue", "yellow", "lightcoral"]
explode = (0, 0.05, 0, 0)

plt.title("Ethnicity Distribution for Bottom Five Zipcodes in 2015")
plt.pie(percentages, explode=explode, labels=races, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=45)
plt.axis("equal")
plt.show()
```


![png](output_49_0.png)

