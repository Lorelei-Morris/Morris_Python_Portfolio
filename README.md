## Using Jupyter Notebooks
```python
%matplotlib inline
import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sns 
sns.set(style = "darkgrid")
```


```python
df = pd.read_csv('/home/student/Desktop/classroom/myfiles/notebooks/fortune500.csv')
```


```python
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
      <th>Year</th>
      <th>Rank</th>
      <th>Company</th>
      <th>Revenue (in millions)</th>
      <th>Profit (in millions)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>1955</td>
      <td>1</td>
      <td>General Motors</td>
      <td>9823.5</td>
      <td>806</td>
    </tr>
    <tr>
      <td>1</td>
      <td>1955</td>
      <td>2</td>
      <td>Exxon Mobil</td>
      <td>5661.4</td>
      <td>584.8</td>
    </tr>
    <tr>
      <td>2</td>
      <td>1955</td>
      <td>3</td>
      <td>U.S. Steel</td>
      <td>3250.4</td>
      <td>195.4</td>
    </tr>
    <tr>
      <td>3</td>
      <td>1955</td>
      <td>4</td>
      <td>General Electric</td>
      <td>2959.1</td>
      <td>212.6</td>
    </tr>
    <tr>
      <td>4</td>
      <td>1955</td>
      <td>5</td>
      <td>Esmark</td>
      <td>2510.8</td>
      <td>19.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.tail()
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
      <th>Year</th>
      <th>Rank</th>
      <th>Company</th>
      <th>Revenue (in millions)</th>
      <th>Profit (in millions)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>25495</td>
      <td>2005</td>
      <td>496</td>
      <td>Wm. Wrigley Jr.</td>
      <td>3648.6</td>
      <td>493</td>
    </tr>
    <tr>
      <td>25496</td>
      <td>2005</td>
      <td>497</td>
      <td>Peabody Energy</td>
      <td>3631.6</td>
      <td>175.4</td>
    </tr>
    <tr>
      <td>25497</td>
      <td>2005</td>
      <td>498</td>
      <td>Wendy's International</td>
      <td>3630.4</td>
      <td>57.8</td>
    </tr>
    <tr>
      <td>25498</td>
      <td>2005</td>
      <td>499</td>
      <td>Kindred Healthcare</td>
      <td>3616.6</td>
      <td>70.6</td>
    </tr>
    <tr>
      <td>25499</td>
      <td>2005</td>
      <td>500</td>
      <td>Cincinnati Financial</td>
      <td>3614.0</td>
      <td>584</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.columns = ['year', 'rank', 'company', 'revenue', 'profit']
```


```python
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
      <th>year</th>
      <th>rank</th>
      <th>company</th>
      <th>revenue</th>
      <th>profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>1955</td>
      <td>1</td>
      <td>General Motors</td>
      <td>9823.5</td>
      <td>806</td>
    </tr>
    <tr>
      <td>1</td>
      <td>1955</td>
      <td>2</td>
      <td>Exxon Mobil</td>
      <td>5661.4</td>
      <td>584.8</td>
    </tr>
    <tr>
      <td>2</td>
      <td>1955</td>
      <td>3</td>
      <td>U.S. Steel</td>
      <td>3250.4</td>
      <td>195.4</td>
    </tr>
    <tr>
      <td>3</td>
      <td>1955</td>
      <td>4</td>
      <td>General Electric</td>
      <td>2959.1</td>
      <td>212.6</td>
    </tr>
    <tr>
      <td>4</td>
      <td>1955</td>
      <td>5</td>
      <td>Esmark</td>
      <td>2510.8</td>
      <td>19.1</td>
    </tr>
  </tbody>
</table>
</div>




```python
len(df)
```




    25500




```python
df.dtypes
```




    year         int64
    rank         int64
    company     object
    revenue    float64
    profit      object
    dtype: object




```python
non_numeric_profits = df.profit.str.contains('[^0-9,-]')
df.loc[non_numeric_profits].head()
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
      <th>year</th>
      <th>rank</th>
      <th>company</th>
      <th>revenue</th>
      <th>profit</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>1955</td>
      <td>2</td>
      <td>Exxon Mobil</td>
      <td>5661.4</td>
      <td>584.8</td>
    </tr>
    <tr>
      <td>2</td>
      <td>1955</td>
      <td>3</td>
      <td>U.S. Steel</td>
      <td>3250.4</td>
      <td>195.4</td>
    </tr>
    <tr>
      <td>3</td>
      <td>1955</td>
      <td>4</td>
      <td>General Electric</td>
      <td>2959.1</td>
      <td>212.6</td>
    </tr>
    <tr>
      <td>4</td>
      <td>1955</td>
      <td>5</td>
      <td>Esmark</td>
      <td>2510.8</td>
      <td>19.1</td>
    </tr>
    <tr>
      <td>5</td>
      <td>1955</td>
      <td>6</td>
      <td>Chrysler</td>
      <td>2071.6</td>
      <td>18.5</td>
    </tr>
  </tbody>
</table>
</div>




```python
set(df.profit[non_numeric_profits])
```




    {'N.A.',
     '232.7',
     '1019.2',
     '50.2',
     '-122.1',
     '55.6',
     '593.5',
     '2.4',
     '524.1',
     '238.8',
     '-167.9',
     '71.1',
     '70.3',
     '213.8',
     '316.7',
     '296.4',
     '-231.8',
     '180.5',
     '345.3',
     '36.6',
     '436.7',
     '-2370.7',
     '88.2',
     '848.1',
     '65.2',
     '-602.9',
     '528.5',
     '49.7',
     '-1139.2',
     '518.7',
     '-1589.2',
     '379.1',
     '372.6',
     '15.1',
     '154.7',
     '65.9',
     '39.4',
     '624.1',
     '-2696.8',
     '142.3',
     '767.2',
     '531.8',
     '274.2',
     '2197.6',
     '525.4',
     '504.8',
     '135.5',
     '48.6',
     '186.2',
     '32.1',
     '651.5',
     '195.6',
     '605.3',
     '654.5',
     '95.3',
     '1011.2',
     '183.7',
     '103.7',
     '108.2',
     '-394.4',
     '663.3',
     '-880.1',
     '519.6',
     '28.2',
     '474.9',
     '492.4',
     '708.4',
     '97.6',
     '679.8',
     '620.5',
     '174.1',
     '105.9',
     '363.6',
     '1399.1',
     '1532.5',
     '308.3',
     '113.3',
     '-2.7',
     '1271.2',
     '75.2',
     '-24.7',
     '5.4',
     '210.5',
     '109.3',
     '536.2',
     '-448.2',
     '105.3',
     '113.9',
     '76.5',
     '288.5',
     '-18.9',
     '168.5',
     '788.5',
     '75.4',
     '15.6',
     '556.2',
     '179.9',
     '223.9',
     '784.4',
     '420.8',
     '151.6',
     '55.5',
     '23.5',
     '-66.3',
     '123.5',
     '215.1',
     '422.8',
     '84.1',
     '1298.4',
     '348.8',
     '25.1',
     '1388.1',
     '4295.2',
     '1984.2',
     '250.8',
     '162.8',
     '-281.5',
     '277.1',
     '588.9',
     '-14.3',
     '-754.7',
     '-0.3',
     '1042.5',
     '392.4',
     '-36.1',
     '398.8',
     '735.1',
     '370.1',
     '424.2',
     '412.3',
     '781.8',
     '627.3',
     '53.9',
     '903.9',
     '649.1',
     '303.6',
     '670.4',
     '41.2',
     '109.4',
     '-1.3',
     '215.4',
     '1125.6',
     '1837.6',
     '366.3',
     '110.9',
     '344.9',
     '24.3',
     '455.7',
     '813.6',
     '-271.9',
     '114.5',
     '41.5',
     '117.7',
     '178.2',
     '1403.8',
     '30.2',
     '3.7',
     '251.5',
     '223.6',
     '159.8',
     '213.2',
     '-123.5',
     '4618.8',
     '181.7',
     '808.8',
     '58.7',
     '188.5',
     '85.6',
     '130.9',
     '650.6',
     '173.3',
     '97.9',
     '-1260.5',
     '-2.6',
     '355.6',
     '332.3',
     '-386.4',
     '189.3',
     '412.9',
     '328.6',
     '99.8',
     '1925.3',
     '-153.5',
     '-98.3',
     '204.4',
     '191.8',
     '-162.8',
     '-59.2',
     '487.5',
     '-24.8',
     '442.3',
     '84.2',
     '191.9',
     '393.7',
     '469.8',
     '342.4',
     '225.1',
     '-258.9',
     '815.4',
     '205.1',
     '341.2',
     '170.7',
     '1.5',
     '39.1',
     '353.9',
     '1704.5',
     '221.3',
     '36.8',
     '627.2',
     '155.6',
     '20.8',
     '67.3',
     '58.3',
     '-74.6',
     '415.1',
     '-25.6',
     '128.9',
     '-1177.7',
     '104.6',
     '228.2',
     '-158.4',
     '142.8',
     '1876.7',
     '-2.2',
     '670.2',
     '247.1',
     '514.3',
     '260.3',
     '347.3',
     '482.2',
     '-12.6',
     '-586.8',
     '3204.7',
     '84.8',
     '101.7',
     '179.3',
     '5.9',
     '521.7',
     '-45.7',
     '-17462.2',
     '-460.2',
     '468.8',
     '1947.9',
     '-15.6',
     '456.7',
     '22.8',
     '856.4',
     '578.3',
     '774.8',
     '114.1',
     '482.8',
     '-752.8',
     '40.9',
     '183.4',
     '83.6',
     '-69.9',
     '-505.3',
     '-116.5',
     '2094.5',
     '79.9',
     '-1001.5',
     '291.8',
     '119.1',
     '-238.6',
     '503.6',
     '642.8',
     '211.5',
     '386.1',
     '155.3',
     '138.5',
     '418.6',
     '8.8',
     '73.5',
     '13.4',
     '-257.8',
     '486.8',
     '1186.1',
     '1255.4',
     '2007.2',
     '62.3',
     '490.1',
     '-19.3',
     '265.9',
     '516.5',
     '1204.9',
     '167.8',
     '1024.1',
     '-360.7',
     '-78.1',
     '332.2',
     '273.3',
     '87.1',
     '579.4',
     '631.3',
     '136.3',
     '482.3',
     '5.5',
     '263.4',
     '65.5',
     '-273.6',
     '73.7',
     '1710.7',
     '332.7',
     '75.6',
     '853.5',
     '-56.6',
     '297.7',
     '587.4',
     '283.5',
     '121.5',
     '129.4',
     '367.9',
     '449.1',
     '202.5',
     '79.5',
     '39.2',
     '105.6',
     '185.9',
     '90.5',
     '-40.6',
     '880.1',
     '409.4',
     '315.4',
     '-46.9',
     '508.9',
     '29.7',
     '88.9',
     '97.7',
     '-75.5',
     '-19.9',
     '-254.5',
     '664.1',
     '72.1',
     '181.8',
     '191.6',
     '717.1',
     '565.4',
     '165.2',
     '170.5',
     '1230.6',
     '550.7',
     '563.1',
     '-13082.2',
     '156.6',
     '-47.8',
     '45.5',
     '26.6',
     '-62.7',
     '-64.4',
     '95.7',
     '12.3',
     '8.7',
     '-1060.1',
     '-680.4',
     '232.1',
     '158.9',
     '1651.4',
     '474.3',
     '-55.1',
     '143.9',
     '391.2',
     '172.6',
     '809.9',
     '-385.1',
     '553.2',
     '131.9',
     '-234.2',
     '92.9',
     '970.9',
     '22.1',
     '348.1',
     '75.7',
     '118.9',
     '-624.6',
     '635.6',
     '-589.1',
     '1599.8',
     '-4.2',
     '37.7',
     '930.8',
     '1017.5',
     '318.9',
     '-63.3',
     '-645.7',
     '276.9',
     '277.6',
     '1026.2',
     '-112.2',
     '567.5',
     '501.7',
     '-1.9',
     '470.5',
     '81.6',
     '-230.2',
     '516.8',
     '51.1',
     '419.8',
     '-1391.9',
     '103.9',
     '421.6',
     '970.3',
     '335.1',
     '50.3',
     '451.6',
     '2290.9',
     '308.9',
     '375.9',
     '1928.8',
     '-10.5',
     '305.5',
     '106.3',
     '-354.6',
     '144.7',
     '338.5',
     '133.5',
     '148.9',
     '-299.8',
     '443.2',
     '999.9',
     '439.7',
     '132.4',
     '5890.5',
     '135.7',
     '266.8',
     '-4282.8',
     '79.8',
     '-43.9',
     '1575.5',
     '591.7',
     '783.6',
     '195.2',
     '-71.4',
     '751.4',
     '-378.1',
     '197.5',
     '278.2',
     '22.5',
     '716.6',
     '1027.4',
     '470.3',
     '150.6',
     '-152.5',
     '25.7',
     '292.4',
     '143.2',
     '64.3',
     '131.6',
     '118.6',
     '76.9',
     '161.7',
     '60.7',
     '139.5',
     '-163.5',
     '429.4',
     '169.7',
     '786.5',
     '459.3',
     '299.3',
     '107.6',
     '81.2',
     '288.6',
     '-80.4',
     '540.2',
     '153.5',
     '501.8',
     '290.8',
     '244.8',
     '253.6',
     '139.4',
     '-11.9',
     '503.8',
     '660.9',
     '264.8',
     '208.3',
     '45.8',
     '525.3',
     '403.5',
     '133.4',
     '160.5',
     '386.7',
     '157.7',
     '2779.9',
     '245.4',
     '62.6',
     '694.1',
     '-191.9',
     '437.6',
     '-8.9',
     '56.3',
     '3011.3',
     '-54.6',
     '174.3',
     '168.6',
     '106.9',
     '772.5',
     '47.1',
     '2892.7',
     '452.2',
     '195.4',
     '488.3',
     '-33.8',
     '68.9',
     '260.6',
     '333.1',
     '147.3',
     '136.7',
     '10.2',
     '3765.6',
     '513.6',
     '185.4',
     '611.6',
     '161.1',
     '263.2',
     '71.4',
     '-610.5',
     '145.2',
     '182.4',
     '808.9',
     '-90.9',
     '113.6',
     '-207.7',
     '108.7',
     '1286.1',
     '54.3',
     '340.1',
     '817.3',
     '-7.4',
     '-307.5',
     '1572.9',
     '526.1',
     '360.8',
     '346.9',
     '25.3',
     '-111.2',
     '199.4',
     '322.4',
     '939.5',
     '-18.3',
     '32.8',
     '294.2',
     '1784.7',
     '44.5',
     '37.5',
     '604.5',
     '391.9',
     '431.2',
     '10.3',
     '-90.8',
     '510.2',
     '301.7',
     '241.8',
     '371.5',
     '194.8',
     '445.4',
     '1338.7',
     '99.7',
     '131.4',
     '595.3',
     '3235.9',
     '98.7',
     '833.9',
     '69.9',
     '547.1',
     '1239.1',
     '45.4',
     '23.9',
     '100.7',
     '-76.9',
     '175.5',
     '296.6',
     '1212.8',
     '144.8',
     '421.8',
     '259.7',
     '-13.7',
     '116.7',
     '126.3',
     '489.5',
     '666.1',
     '403.8',
     '536.7',
     '12.9',
     '27.9',
     '135.3',
     '59.8',
     '46.5',
     '-1.1',
     '62.1',
     '620.2',
     '630.8',
     '758.1',
     '500.6',
     '474.6',
     '-22.7',
     '555.5',
     '221.8',
     '119.3',
     '750.1',
     '468.5',
     '1023.7',
     '2642.5',
     '4614.1',
     '-930.9',
     '40.7',
     '148.7',
     '869.7',
     '136.9',
     '16.7',
     '241.2',
     '226.1',
     '28.7',
     '26.9',
     '53.2',
     '-828.6',
     '1923.5',
     '84.5',
     '1031.3',
     '35.7',
     '43.1',
     '709.9',
     '134.6',
     '126.1',
     '90.1',
     '579.5',
     '878.2',
     '-514.8',
     '-55.5',
     '527.5',
     '111.2',
     '1327.4',
     '2278.5',
     '1405.8',
     '114.7',
     '112.4',
     '266.3',
     '199.2',
     '47.6',
     '100.8',
     '-48.5',
     '-16.9',
     '-657.8',
     '-336.5',
     '1105.9',
     '510.9',
     '299.7',
     '561.4',
     '890.6',
     '152.6',
     '-29.4',
     '610.6',
     '477.3',
     '149.2',
     '585.6',
     '-303.1',
     '182.5',
     '294.8',
     '-6.5',
     '679.7',
     '118.1',
     '374.3',
     '907.2',
     '924.7',
     '144.4',
     '-16.2',
     '200.9',
     '157.3',
     '871.5',
     '221.5',
     '-676.1',
     '-435.8',
     '178.1',
     '373.9',
     '197.8',
     '253.3',
     '290.7',
     '398.2',
     '402.7',
     '720.9',
     '1098.5',
     '944.9',
     '418.8',
     '-30.5',
     '1586.4',
     '787.1',
     '132.3',
     '-355.4',
     '302.1',
     '250.5',
     '358.7',
     '590.9',
     '1471.5',
     '95.6',
     '115.3',
     '281.7',
     '538.6',
     '702.1',
     '361.4',
     '145.5',
     '-16.4',
     '47.9',
     '18.5',
     '21.6',
     '-1393.3',
     '1292.4',
     '116.6',
     '813.3',
     '44.2',
     '1506.5',
     '874.2',
     '5636.1',
     '538.1',
     '774.3',
     '257.9',
     '280.7',
     '-53.9',
     '-52.5',
     '770.4',
     '38.1',
     '176.6',
     '2567.9',
     '197.9',
     '962.7',
     '43.9',
     '86.9',
     '321.9',
     '7149.5',
     '57.5',
     '336.5',
     '301.5',
     '193.2',
     '8.4',
     '568.3',
     '133.9',
     '1609.9',
     '636.5',
     '-141.1',
     '254.8',
     '92.7',
     '394.8',
     '183.1',
     '-436.7',
     '-288.8',
     '327.8',
     '934.5',
     '104.7',
     '288.4',
     '320.5',
     '-180.3',
     '-127.1',
     '-1097.3',
     '110.3',
     '127.4',
     '370.3',
     '119.2',
     '935.6',
     '-23.3',
     '364.1',
     '139.9',
     '-121.3',
     '-136.6',
     '340.9',
     '933.8',
     '907.7',
     '60.1',
     '56.9',
     '655.2',
     '490.2',
     '14.5',
     '-16.6',
     '152.8',
     '244.1',
     '282.9',
     '96.8',
     '-89.5',
     '321.1',
     '438.3',
     '277.3',
     '297.2',
     '219.5',
     '9274.2',
     '-83.2',
     '87.8',
     '889.8',
     '-96.4',
     '276.8',
     '38.5',
     '466.4',
     '32.4',
     '178.6',
     '29.2',
     '25.8',
     '613.7',
     '144.2',
     '305.2',
     '44.4',
     '-23.4',
     '95.2',
     '147.4',
     '-10.8',
     '-548.5',
     '582.4',
     '554.5',
     '-23.8',
     '151.9',
     '576.8',
     '134.4',
     '87.2',
     '-203.4',
     '539.1',
     '702.8',
     '539.7',
     '1233.3',
     '-86.4',
     '906.8',
     '457.7',
     '-315.1',
     '374.5',
     '84.6',
     '234.2',
     '472.3',
     '208.6',
     '933.9',
     '410.9',
     '397.3',
     '98.3',
     '42.5',
     '1253.1',
     '-85.5',
     '490.5',
     '658.5',
     '316.4',
     '-4.7',
     '91.6',
     '207.2',
     '102.9',
     '18.6',
     '-124.8',
     '254.5',
     '-2142.8',
     '-55.4',
     '386.5',
     '-59.9',
     '-115.6',
     '206.8',
     '611.8',
     '153.1',
     '-21.6',
     '262.8',
     '467.4',
     '110.4',
     '2474.3',
     '441.8',
     '663.7',
     '281.9',
     '430.1',
     '226.7',
     '-1222.7',
     '473.4',
     '484.9',
     '12.5',
     '688.1',
     '434.4',
     '121.3',
     '-475.9',
     '207.5',
     '917.5',
     '-345.1',
     '441.5',
     '297.6',
     '229.1',
     '198.8',
     '-55.2',
     '201.3',
     '23.2',
     '80.6',
     '54.6',
     '-20.7',
     '122.4',
     '-38.1',
     '-224.7',
     '300.4',
     '604.4',
     '295.6',
     '531.7',
     '193.4',
     '-43.8',
     '115.5',
     '44.7',
     '54.9',
     '-920.9',
     '520.2',
     '282.4',
     '171.6',
     '29.8',
     '675.7',
     '181.9',
     '370.8',
     '357.8',
     '1360.2',
     '-59.7',
     '177.7',
     '-510.6',
     '317.8',
     '32.5',
     '224.9',
     '-15.7',
     '217.8',
     '50.5',
     '330.9',
     '536.6',
     '143.3',
     '451.8',
     '-20.8',
     '-190.4',
     '792.6',
     '1031.8',
     '-92.1',
     '465.6',
     '325.8',
     '181.1',
     '184.3',
     '-14.6',
     '82.1',
     '-203.6',
     '191.7',
     '155.7',
     '5.7',
     '40.3',
     '148.5',
     '149.1',
     '500.5',
     '716.8',
     '-754.8',
     '-31.1',
     '2.5',
     '254.9',
     '135.4',
     '129.9',
     '869.5',
     '1189.1',
     '450.9',
     '92.1',
     '144.1',
     '232.9',
     '505.1',
     '609.7',
     '203.8',
     '169.2',
     '159.3',
     '182.8',
     '-567.3',
     '502.8',
     '2097.9',
     '-393.1',
     '200.1',
     '62.5',
     '1088.2',
     '-95.8',
     '639.5',
     '740.9',
     '274.9',
     '229.9',
     '309.3',
     '272.3',
     '419.6',
     '278.9',
     '172.5',
     '-119.7',
     '1634.7',
     '91.4',
     '-220.2',
     '138.6',
     '-22.9',
     '10.9',
     '382.4',
     '127.5',
     '446.2',
     '172.4',
     '-15.5',
     '167.3',
     '372.7',
     '7.8',
     '43.4',
     '363.1',
     '309.1',
     '885.1',
     '650.7',
     '626.4',
     '75.5',
     '50.6',
     '248.9',
     '1213.3',
     '304.6',
     '2259.5',
     '376.5',
     '-1849.9',
     '274.5',
     '168.2',
     '180.3',
     '-186.3',
     ...}




```python
len(df.profit[non_numeric_profits])
```




    19936




```python
bin_size, _, _ = plt.hist(df.year[non_numeric_profits], bins= range(1955, 2005) )
```


![png](output_11_0.png)



```python
df = df.loc[~non_numeric_profits]
df.profit = df.profit.apply(pd.to_numeric)
```


```python
len(df)
```




    5564




```python
df.dtypes
```




    year         int64
    rank         int64
    company     object
    revenue    float64
    profit       int64
    dtype: object




```python
group_by_year = df.loc[:, ['year', 'revenue', 'profit']].groupby('year')
avgs = group_by_year.mean()
x = avgs.index
y1 = avgs.profit
def plot(x, y, ax, title, y_label):
    ax.set_title(title)
    ax.set_ylabel(y_label)
    ax.plot(x, y)
    ax.margins(x = 0, y = 0)
```


```python
fig, ax = plt.subplots()
plot(x, y1, ax,'Increase in Fortune 500 company profits from 1955 to 2005', 'Profits(millions)')
```


![png](output_16_0.png)



```python
y2 = avgs.revenue
fig, ax = plt.subplots()
plot(x, y2, ax, 'Increase in mean fortune 500 company revenues from 1955 to 2005', 'Revenue (millions)')
```


![png](output_17_0.png)



```python
def plot_with_std(x, y, stds, ax, title, y_label):
    ax.fill_between(x, y -stds, alpha = 0.2)
    plot(x, y, ax, title, y_label)
fig, (ax1, ax2) = plt.subplots(ncols= 2)
title = 'Increase in mean and std fortune 500 company %s from 1955 to 2005'
stds1 = group_by_year.std().profit.values
stds2 = group_by_year.std().revenue.values
plot_with_std(x, y1.values, stds1, ax1, title % 'profits', 'Profit (millions)')
plot_with_std(x, y2.values, stds1, ax2, title % 'revenues', 'Revenue (millions)')
fig.set_size_inches(14,4)
fig.tight_layout()
```


![png](output_18_0.png)

# Python Fundementals 

```python
weight_kg = 60
```


```python
print(weight_kg)
```

    60



```python
weight_kg = 60.3
```


```python
patient_name = 'John Smith'
```


```python
patient_id = '001'
```


```python
weight_lb = 2.2 * weight_kg

print(weight_lb)
```

    132.66



```python
patient_id = 'inflam_' + patient_id

print(patient_id)
```

    inflam_001



```python
print(patient_id, 'weight in kilograms:', weight_kg)
```

    inflam_001 weight in kilograms: 60.3



```python
print(type(60.3))

print(type(patient_id))
```

    <class 'float'>
    <class 'str'>



```python
print('weight in lbs:', 2.2 * weight_kg)
```

    weight in lbs: 132.66



```python
print(weight_kg)
```

    60.3



```python
weight_kg = 65.0
print('weight in kilograms is now:', weight_kg)
```

    weight in kilograms is now: 65.0

## Analyzing Data
```python
import numpy
```


```python
numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')
```




    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])




```python
data = numpy.loadtxt(fname = 'inflammation-01.csv', delimiter = ',')
```


```python
print(data)
```

    [[0. 0. 1. ... 3. 0. 0.]
     [0. 1. 2. ... 1. 0. 1.]
     [0. 1. 1. ... 2. 1. 1.]
     ...
     [0. 1. 1. ... 1. 1. 1.]
     [0. 0. 0. ... 0. 2. 0.]
     [0. 0. 1. ... 1. 1. 0.]]



```python
print(type(data))
```

    <class 'numpy.ndarray'>



```python
print(data.shape)
```

    (60, 40)



```python
print('first value in data:', data[0,0])
```

    first value in data: 0.0



```python
print('middle value in data:', data[29, 19])
```

    middle value in data: 16.0



```python
print(data[0:4, 0:10])
```

    [[0. 0. 1. 3. 1. 2. 4. 7. 8. 3.]
     [0. 1. 2. 1. 2. 1. 3. 2. 2. 6.]
     [0. 1. 1. 3. 3. 2. 6. 2. 5. 9.]
     [0. 0. 2. 0. 4. 2. 2. 1. 6. 7.]]



```python
print(data[5:10, 0:10])
```

    [[0. 0. 1. 2. 2. 4. 2. 1. 6. 4.]
     [0. 0. 2. 2. 4. 2. 2. 5. 5. 8.]
     [0. 0. 1. 2. 3. 1. 2. 3. 5. 3.]
     [0. 0. 0. 3. 1. 5. 6. 5. 5. 8.]
     [0. 1. 1. 2. 1. 3. 5. 3. 5. 8.]]



```python
small = data [:3, 36:]
```


```python
print('small is:')
```

    small is:



```python
print(small)
```

    [[2. 3. 0. 0.]
     [1. 1. 0. 1.]
     [2. 2. 1. 1.]]



```python
print(numpy.mean(data))
```

    6.14875



```python
maxval, minval, stdval = numpy.amax(data), numpy.amin(data), numpy.std(data)
```


```python
print(maxval)
print(minval)
print(stdval)
```

    20.0
    0.0
    4.613833197118566



```python
maxval = numpy.amax(data)
minval = numpy.amin(data)
stdval = numpy.std(data)
```


```python
print(maxval)
print(minval)
print(stdval)
```

    20.0
    0.0
    4.613833197118566



```python
print('maximum inflammation:', maxval)
print('manimum inflammation:', minval)
print('standard deviation:', stdval)
```

    maximum inflammation: 20.0
    manimum inflammation: 0.0
    standard deviation: 4.613833197118566



```python
patient_0 = data[0, :]

print('maximum inflammation for patient 0:', numpy.amax(patient_0))
```

    maximum inflammation for patient 0: 18.0



```python
print('maximum inflammation for patient2:', numpy.amax(data[2, :]))
```

    maximum inflammation for patient2: 19.0



```python
print(numpy.mean(data, axis = 0))
```

    [ 0.          0.45        1.11666667  1.75        2.43333333  3.15
      3.8         3.88333333  5.23333333  5.51666667  5.95        5.9
      8.35        7.73333333  8.36666667  9.5         9.58333333 10.63333333
     11.56666667 12.35       13.25       11.96666667 11.03333333 10.16666667
     10.          8.66666667  9.15        7.25        7.33333333  6.58333333
      6.06666667  5.95        5.11666667  3.6         3.3         3.56666667
      2.48333333  1.5         1.13333333  0.56666667]



```python
print(numpy.mean(data, axis = 0).shape)
```

    (40,)



```python
print(numpy.mean(data, axis = 1))
```

    [5.45  5.425 6.1   5.9   5.55  6.225 5.975 6.65  6.625 6.525 6.775 5.8
     6.225 5.75  5.225 6.3   6.55  5.7   5.85  6.55  5.775 5.825 6.175 6.1
     5.8   6.425 6.05  6.025 6.175 6.55  6.175 6.35  6.725 6.125 7.075 5.725
     5.925 6.15  6.075 5.75  5.975 5.725 6.3   5.9   6.75  5.925 7.225 6.15
     5.95  6.275 5.7   6.1   6.825 5.975 6.725 5.7   6.25  6.4   7.05  5.9  ]

```python
import numpy
data = numpy.loadtxt(fname= 'inflammation-01.csv', delimiter = ',')
```


```python
import matplotlib.pyplot
image = matplotlib.pyplot.imshow(data)
matplotlib.pyplot.show()
```


![png](output_1_0.png)



```python
ave_inflammation = numpy.mean(data,axis = 0)
ave_plot = matplotlib.pyplot.plot(ave_inflammation)
matplotlib.pyplot.show()
```


![png](output_2_0.png)



```python
min_plot = matplotlib.pyplot.plot(numpy.amin(data, axis = 0))
matplotlib.pyplot.show()
```


![png](output_3_0.png)



```python
max_plot = matplotlib.pyplot.plot(numpy.amax(data, axis = 0))
matplotlib.pyplot.show()
```


![png](output_4_0.png)



```python
fig = matplotlib.pyplot.figure(figsize = (10.0,3.0))
    
axes1 = fig.add_subplot(1, 3, 1)
axes2 = fig.add_subplot(1, 3, 2)
axes3 = fig.add_subplot(1, 3, 3)
    
axes1.set_ylabel('average')
axes1.plot(numpy.mean(data,axis = 0))
    
axes2.set_ylabel('max')
axes2.plot(numpy.amax(data,axis = 0))
    
axes3.set_ylabel('min')
axes3.plot(numpy.amin(data,axis = 0))

fig.tight_layout()

matplotlib.pyplot.savefig('inflammation.png')
matplotlib.pyplot.show()
```


![png](output_5_0.png)

## Storing Values in Lists
```python
odds = [1, 3, 5, 7]
print('odds are:', odds)
```

    odds are: [1, 3, 5, 7]



```python
print('first element:', odds[0])
print('last element:', odds[3])
print('"-1" element:', odds[-1])
```

    first element: 1
    last element: 7
    "-1" element: 7



```python
names = ['Curtis', 'Darwing', 'Turing'] 

print('names is originally:', names)

names [1] = 'Darwin'

print ('final value of names:', names)
```

    names is originally: ['Curtis', 'Darwing', 'Turing']
    final value of names: ['Curtis', 'Darwin', 'Turing']



```python
odds.append(11)
print('odds after adding a value:', odds)
```

    odds after adding a value: [1, 3, 5, 7, 11]



```python
removed_element = odds.pop(0)
print('odds after removing the first element:', odds)
print ('removed_element:', removed_element)
```

    odds after removing the first element: [3, 5, 7, 11]
    removed_element: 1



```python
odds.reverse()
print('odds after reversing:', odds)
```

    odds after reversing: [11, 7, 5, 3]



```python
odds = [3, 5, 7]
primes = odds
primes.append(2)
print('primes:', primes)
print('odds:', odds)
```

    primes: [3, 5, 7, 2]
    odds: [3, 5, 7, 2]



```python
binomial_name = "Drosophila melonogaster"
group = binomial_name[0:10]
print('group:', group)

species = binomial_name[11:23]
print ('species:', species)

chromosomes = ['X', 'Y', '2', '3', '4']
autosomes = chromosomes [2:5]
print('autosomes:', autosomes)

last = chromosomes [-1]
print('last:', last)
```

    group: Drosophila
    species: melonogaster
    autosomes: ['2', '3', '4']
    last: 4



```python
date = 'Monday 4 January 2023'
day = date [0:6]
print('Using 0 to begin range:', day)
date = date[:6]
print('omitting beginning index:', day)
```

    Using 0 to begin range: Monday
    omitting beginning index: Monday



```python
months = ['jan', 'fed', 'mar', 'apr', 'may', 'jun', 'jul', 'aug', 'sep', 'oct', 'nov', 'dec']
sond = months [8:12]
print('With known last position:', sond)

sond = months[8:len(months)]
print('Uisng len() to get last entry', sond)

sond = months [8:]
print('Omitting ending index:', sond)

```

    With known last position: ['sep', 'oct', 'nov', 'dec']
    Uisng len() to get last entry ['sep', 'oct', 'nov', 'dec']
    Omitting ending index: ['sep', 'oct', 'nov', 'dec']


## Using Loops 
```python
odds = [1, 3, 5, 7]
```


```python
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```

    1
    3
    5
    7



```python
odds = [1, 3, 5]
print(odds[0])
print(odds[1])
print(odds[2])
print(odds[3])
```

    1
    3
    5



    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-3-b48c9fadc7bf> in <module>
          3 print(odds[1])
          4 print(odds[2])
    ----> 5 print(odds[3])
    

    IndexError: list index out of range



```python
odds = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]

for num in odds:
    print(num)
```

    1
    3
    5
    7
    9
    11
    13
    15
    17
    19



```python
length = 0
names = ['Curie', 'Darwin', 'Turing']
for values in names:
    length = length + 1
print('There are', length, 'names in the list')
```

    There are 3 names in the list



```python
name = 'Rosalind'
for name in ['Curie', 'Darwin', 'Turing']:
    print(name)
print('after the loop, name is', name)
```

    Curie
    Darwin
    Turing
    after the loop, name is Turing



```python
print(len([0,1,2,3]))
```

    4



```python
name = ['Curie', 'Darwin', 'Turing']

print (len(name))
```

    3

## Using Multiple Files
```python
import glob
```


```python
print(glob.glob('inflammation*.csv'))
```

    ['inflammation-10.csv', 'inflammation-09.csv', 'inflammation-11.csv', 'inflammation-06.csv', 'inflammation-05.csv', 'inflammation-08.csv', 'inflammation-01.csv', 'inflammation-07.csv', 'inflammation-04.csv', 'inflammation-03.csv', 'inflammation-02.csv', 'inflammation-12.csv']



```python
import glob
import numpy
import matplotlib.pyplot

filenames = sorted(glob.glob('inflammation*.csv'))
filenames = filenames[0:3]

for filename in filenames:
    print(filename)
    
    data = numpy.loadtxt(fname=filename, delimiter = ',')
    
    fig = matplotlib.pyplot.figure(figsize = (10.0,3.0))
    
    axes1 = fig.add_subplot(1, 3, 1)
    axes2 = fig.add_subplot(1, 3, 2)
    axes3 = fig.add_subplot(1, 3, 3)
    
    axes1.set_ylabel('average')
    axes1.plot(numpy.mean(data,axis = 0))
    
    axes2.set_ylabel('max')
    axes2.plot(numpy.amax(data,axis = 0))
    
    axes3.set_ylabel('min')
    axes3.plot(numpy.amin(data,axis = 0))
    
    fig.tight_layout()
    matplotlib.pyplot.show()
```

    inflammation-01.csv



![png](output_2_1.png)


    inflammation-02.csv



![png](output_2_3.png)


    inflammation-03.csv



![png](output_2_5.png)

## Making Choices
```python
import numpy
```


```python
data = numpy.loadtxt(fname='inflammation-01.csv', delimiter=',')
```


```python
max_inflammation_0 = numpy.amax(data, axis=0)[0]
```


```python
max_inflammation_20 = numpy.amax(data, axis = 0)[20]

if max_inflammation_0 == 0 and max_inflammation_20 == 20:
    print('Saspictious looking maxima!')
    
elif numpy.sum(numpy.amin(data,axis=0)) == 0:
    print('Minima add up to zero!')
    
else:
    print('Seems OK!')
```

    Saspictious looking maxima!



```python
Data = numpy.loadtxt(fname = 'inflammation-03.csv', delimiter=',')

max_inflammation_0 = numpy.amax(data, axis = 0)[0]

max_inflammation_20 = numpy.amax(data, axis = 0)[20]

if max_inflammation_0 == 0 and max_inflammation_20 ==20: 
    print('Saspictious looking maxima!')
elif numpy.sum(numpy.amin(data,axis=0)) == 0:
    print('Minima add up to zero!-> HEALTHY PARTICIPANT ALERT!')
else:
    print('Seems OK!')
```

    Saspictious looking maxima!

## Functions
```python
fahrenheit_val = 99
celsius_val = ((fahrenheit_val - 32) *(5/9))

print (celsius_val)
```

    37.22222222222222



```python
fahrenheit_val2 = 43
celsius_val2 = ((fahrenheit_val2 - 32) * (5/9))

print(celsius_val2)
```

    6.111111111111112



```python
def explicit_fahr_to_celsius(temp):
    converted = ((temp - 32) * (5/9))
    return converted
```


```python
def fahr_to_celsius(temp):
    return ((temp - 32)* (5/9))
```


```python
fahr_to_celsius(32)
```




    0.0




```python
explicit_fahr_to_celsius(32)
```




    0.0




```python
print('Freezing point of water:', fahr_to_celsius(32), 'C')
print('Boiling point of water:', fahr_to_celsius(212), 'C')
```

    Freezing point of water: 0.0 C
    Boiling point of water: 100.0 C



```python
def celsius_to_kelvin(temp_c):
    return temp_c + 273.15

print ('freezing point of water in Kelvin:', celsius_to_kelvin(0.))
```

    freezing point of water in Kelvin: 273.15



```python
def fahr_to_kelvin(temp_f):
    temp_c = fahr_to_celsius(temp_f)
    temp_k = celsius_to_kelvin(temp_c)
    return temp_k

print('boiling point of water in Kelvin was:', fahr_to_kelvin(212.0))
```

    boiling point of water in Kelvin was: 373.15



```python
print('Again, temperature in Kelvin was:', temp_k)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-15-eed2471d229b> in <module>
    ----> 1 print('Again, temperature in Kelvin was:', temp_k)
    

    NameError: name 'temp_k' is not defined



```python
temp_kelving = fahr_to_kelvin(212.0)
print('Temperature in Kelvin was:', temp_kelving)
```

    Temperature in Kelvin was: 373.15



```python
temp_kelving
```




    373.15




```python
def print_temperatures():
    print('Temperature in Fahrenheit was:', temp_fahr)
    print('Temperature in Kelvin was:', temp_kelvin)
    
temp_fahr = 212.0
temp_kelvin = fahr_to_kelvin(temp_fahr)

print_temperatures()
```

    Temperature in Fahrenheit was: 212.0
    Temperature in Kelvin was: 373.15

```python
import numpy
import matplotlib
import matplotlib.pyplot
import glob
```


```python
'freezing point of water in kelvin'
def visualize(filename):
    
    data = numpy.loadtxt(fname = filename, delimiter = ',')
    
    fig = matplotlib.pyplot.figure(figsize=(10.0, 3.0))
    
    axes1 = fig.add_subplot(1, 3, 1)
    axes2 = fig.add_subplot(1, 3, 2)
    axes3 = fig.add_subplot(1, 3, 3)
    
    axes1.set_ylabel('average')
    axes1.plot(numpy.mean(data,axis = 0))
    
    axes2.set_ylabel('max')
    axes2.plot(numpy.amax(data,axis = 0))
    
    axes3.set_ylabel('min')
    axes3.plot(numpy.amin(data,axis = 0))
    
    fig.tight_layout()
    matplotlib.pyplot.show()
```


```python
def detect_problems(filename):
    
    data = numpy.loadtxt(fname = filename, delimiter = ',')
    
    if numpy.amax(data, axis = 0)[0] ==0 and numpy.amax(data, axis=0)[20] == 20:
        print ("Suspicious looking maxima!")
    elif numpy.sum(numpy.amin(data, axis=0)) == 0:
        print('Minima add up to zero!')
    else:
        print('Seems ok!')
```


```python
filenames = sorted(glob.glob('inflammation*.csv'))

for filename in filenames:
    print(filename)
    visualize(filename)
    detect_problems(filename)
```

    inflammation-01.csv



![png](output_3_1.png)


    Suspicious looking maxima!
    inflammation-02.csv



![png](output_3_3.png)


    Suspicious looking maxima!
    inflammation-03.csv



![png](output_3_5.png)


    Minima add up to zero!
    inflammation-04.csv



![png](output_3_7.png)


    Suspicious looking maxima!
    inflammation-05.csv



![png](output_3_9.png)


    Suspicious looking maxima!
    inflammation-06.csv



![png](output_3_11.png)


    Suspicious looking maxima!
    inflammation-07.csv



![png](output_3_13.png)


    Suspicious looking maxima!
    inflammation-08.csv



![png](output_3_15.png)


    Minima add up to zero!
    inflammation-09.csv



![png](output_3_17.png)


    Suspicious looking maxima!
    inflammation-10.csv



![png](output_3_19.png)


    Suspicious looking maxima!
    inflammation-11.csv



![png](output_3_21.png)


    Minima add up to zero!
    inflammation-12.csv



![png](output_3_23.png)


    Suspicious looking maxima!



```python
def offset_mean(data, target_mean_value):
    return (data - numpy.mean(data)) + target_mean_value
```


```python
z = numpy.zeros((2,2))
print(offset_mean(z, 3))
```

    [[3. 3.]
     [3. 3.]]



```python
data = numpy.loadtxt(fname = 'inflammation-01.csv', delimiter=',')

print(offset_mean(data, 0))
```

    [[-6.14875 -6.14875 -5.14875 ... -3.14875 -6.14875 -6.14875]
     [-6.14875 -5.14875 -4.14875 ... -5.14875 -6.14875 -5.14875]
     [-6.14875 -5.14875 -5.14875 ... -4.14875 -5.14875 -5.14875]
     ...
     [-6.14875 -5.14875 -5.14875 ... -5.14875 -5.14875 -5.14875]
     [-6.14875 -6.14875 -6.14875 ... -6.14875 -4.14875 -6.14875]
     [-6.14875 -6.14875 -5.14875 ... -5.14875 -5.14875 -6.14875]]



```python
print('original min, mean and max are:', numpy.amin(data), numpy.mean(data), numpy.amax(data))
offset_data = offset_mean(data,0)
print('min, mean, and max of offset data are:',
     numpy.amin(offset_data), 
     numpy.mean(offset_data), 
     numpy.amax(offset_data))

```

    original min, mean and max are: 0.0 6.14875 20.0
    min, mean, and max of offset data are: -6.14875 2.842170943040401e-16 13.85125



```python
print('std dev before and after:', numpy.std(data), numpy.std(offset_data))
```

    std dev before and after: 4.613833197118566 4.613833197118566



```python
print('difference in standard deviation before and after:', 
     numpy.std(data) - numpy.std(offset_data))
```

    difference in standard deviation before and after: 0.0



```python
def offset_mean(data, target_mean_value):
    return (data - numpy.mean(data)) + target_mean_value
```


```python
def offset_mean(data, target_mean_value):
    """Return a new array comtianing the original datra with its mean offset to match the desired value"""
    return (data - numpy.mean(data)) + target_mean_value
```


```python
help(offset_mean)
```

    Help on function offset_mean in module __main__:
    
    offset_mean(data, target_mean_value)
        Return a new array comtianing the original datra with its mean offset to match the desired value
    



```python
def offset_mean(data, target_mean_value):
        """Return a new array comtianing the original datra with its mean offset to match the desired value
    
        Examples
        -----------
        
        >>> Offset_mean([1,2,3], 0)
        array([-1., 0., 1.])
        """
        return (data - numpy.mean(data)) + target_mean_value
```


```python
help(offset_mean)
```

    Help on function offset_mean in module __main__:
    
    offset_mean(data, target_mean_value)
        Return a new array comtianing the original datra with its mean offset to match the desired value
        
        Examples
        -----------
        
        >>> Offset_mean([1,2,3], 0)
        array([-1., 0., 1.])
    



```python
numpy.loadtxt('inflammation-01.csv', delimiter = ',')
```




    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])




```python
def offset_mean(data, target_mean_value = 0.0):
        """Return a new array comtianing the original datra with its mean offset to match the desired value, (0 by default).
    
        Examples
        -----------
        
        >>> Offset_mean([1,2,3])
        array([-1., 0., 1.])
        """
        return (data - numpy.mean(data)) + target_mean_value
```


```python
test_data = numpy.zeros((2,2))
print(offset_mean(test_data, 3))
```

    [[3. 3.]
     [3. 3.]]



```python
print(offset_mean(test_data))
```

    [[0. 0.]
     [0. 0.]]



```python
def display(a=1, b=2, c=3):
    print('a:', a, 'b:', b, 'c:', c)

print('no parameters:')
display()
print('one parameter:')
display(55)
print('two parameter:')
display(55,66)
```

    no parameters:
    a: 1 b: 2 c: 3
    one parameter:
    a: 55 b: 2 c: 3
    two parameter:
    a: 55 b: 66 c: 3



```python
print('only setting the value of c')
display(c = 77)
```

    only setting the value of c
    a: 1 b: 2 c: 77



```python
help(numpy.loadtxt)
```

    Help on function loadtxt in module numpy:
    
    loadtxt(fname, dtype=<class 'float'>, comments='#', delimiter=None, converters=None, skiprows=0, usecols=None, unpack=False, ndmin=0, encoding='bytes', max_rows=None)
        Load data from a text file.
        
        Each row in the text file must have the same number of values.
        
        Parameters
        ----------
        fname : file, str, or pathlib.Path
            File, filename, or generator to read.  If the filename extension is
            ``.gz`` or ``.bz2``, the file is first decompressed. Note that
            generators should return byte strings for Python 3k.
        dtype : data-type, optional
            Data-type of the resulting array; default: float.  If this is a
            structured data-type, the resulting array will be 1-dimensional, and
            each row will be interpreted as an element of the array.  In this
            case, the number of columns used must match the number of fields in
            the data-type.
        comments : str or sequence of str, optional
            The characters or list of characters used to indicate the start of a
            comment. None implies no comments. For backwards compatibility, byte
            strings will be decoded as 'latin1'. The default is '#'.
        delimiter : str, optional
            The string used to separate values. For backwards compatibility, byte
            strings will be decoded as 'latin1'. The default is whitespace.
        converters : dict, optional
            A dictionary mapping column number to a function that will parse the
            column string into the desired value.  E.g., if column 0 is a date
            string: ``converters = {0: datestr2num}``.  Converters can also be
            used to provide a default value for missing data (but see also
            `genfromtxt`): ``converters = {3: lambda s: float(s.strip() or 0)}``.
            Default: None.
        skiprows : int, optional
            Skip the first `skiprows` lines, including comments; default: 0.
        usecols : int or sequence, optional
            Which columns to read, with 0 being the first. For example,
            ``usecols = (1,4,5)`` will extract the 2nd, 5th and 6th columns.
            The default, None, results in all columns being read.
        
            .. versionchanged:: 1.11.0
                When a single column has to be read it is possible to use
                an integer instead of a tuple. E.g ``usecols = 3`` reads the
                fourth column the same way as ``usecols = (3,)`` would.
        unpack : bool, optional
            If True, the returned array is transposed, so that arguments may be
            unpacked using ``x, y, z = loadtxt(...)``.  When used with a structured
            data-type, arrays are returned for each field.  Default is False.
        ndmin : int, optional
            The returned array will have at least `ndmin` dimensions.
            Otherwise mono-dimensional axes will be squeezed.
            Legal values: 0 (default), 1 or 2.
        
            .. versionadded:: 1.6.0
        encoding : str, optional
            Encoding used to decode the inputfile. Does not apply to input streams.
            The special value 'bytes' enables backward compatibility workarounds
            that ensures you receive byte arrays as results if possible and passes
            'latin1' encoded strings to converters. Override this value to receive
            unicode arrays and pass strings as input to converters.  If set to None
            the system default is used. The default value is 'bytes'.
        
            .. versionadded:: 1.14.0
        max_rows : int, optional
            Read `max_rows` lines of content after `skiprows` lines. The default
            is to read all the lines.
        
            .. versionadded:: 1.16.0
        
        Returns
        -------
        out : ndarray
            Data read from the text file.
        
        See Also
        --------
        load, fromstring, fromregex
        genfromtxt : Load data with missing values handled as specified.
        scipy.io.loadmat : reads MATLAB data files
        
        Notes
        -----
        This function aims to be a fast reader for simply formatted files.  The
        `genfromtxt` function provides more sophisticated handling of, e.g.,
        lines with missing values.
        
        .. versionadded:: 1.10.0
        
        The strings produced by the Python float.hex method can be used as
        input for floats.
        
        Examples
        --------
        >>> from io import StringIO   # StringIO behaves like a file object
        >>> c = StringIO(u"0 1\n2 3")
        >>> np.loadtxt(c)
        array([[0., 1.],
               [2., 3.]])
        
        >>> d = StringIO(u"M 21 72\nF 35 58")
        >>> np.loadtxt(d, dtype={'names': ('gender', 'age', 'weight'),
        ...                      'formats': ('S1', 'i4', 'f4')})
        array([(b'M', 21, 72.), (b'F', 35, 58.)],
              dtype=[('gender', 'S1'), ('age', '<i4'), ('weight', '<f4')])
        
        >>> c = StringIO(u"1,0,2\n3,0,4")
        >>> x, y = np.loadtxt(c, delimiter=',', usecols=(0, 2), unpack=True)
        >>> x
        array([1., 3.])
        >>> y
        array([2., 4.])
    



```python
numpy.loadtxt('inflammation-01.csv', delimiter = ',')
```




    array([[0., 0., 1., ..., 3., 0., 0.],
           [0., 1., 2., ..., 1., 0., 1.],
           [0., 1., 1., ..., 2., 1., 1.],
           ...,
           [0., 1., 1., ..., 1., 1., 1.],
           [0., 0., 0., ..., 0., 2., 0.],
           [0., 0., 1., ..., 1., 1., 0.]])




```python
def s(p):
    a = 0
    for v in p:
        a += v
    m = a / len(p)
    d = 0
    for v in p:
        d += (v - m) * (v - m)
    return numpy.sqrt(d / (len(p) - 1))

def std_dev(sample):
    sample_sum = 0
    for value in sample: 
        sample_sum += value 
        
    sample_mean = sample_sum / len(sample)
    
    sum_squared_devs = 0
    for value in sample: 
        sum_squared_devs += (value - sample_mean) * (value - sample_mean)
        
    return numpy.sqrt(sum_squared_devs / (len(sample) - 1))
```
## Defensive Programming
```python
numbers = [1.5, 2.3, 0.7, -0.001, 4.4]
total = 0.0
for num in numbers:
    assert num > 0.0, 'Data should only contain positive values'
    total += num
print('total is:', total)
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-3-13c7d5640ddd> in <module>
          2 total = 0.0
          3 for num in numbers:
    ----> 4     assert num > 0.0, 'Data should only contain positive values'
          5     total += num
          6 print('total is:', total)


    AssertionError: Data should only contain positive values



```python
def normalize_rectangle(rect):
    """Normalize a rectangle so that it is at the origin and 1.0 units long on its longest axis. 
    input should be of the format (x0, y0, x1, y1).
    (x0, y0) and (x1, y1) define the lower left and upper right corners of teh rectangle respecively"""
    assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
    x0, y0, x1, y1 = rect 
    assert x0 < x1, 'Invalid X coordinates'
    assert y0 < y1, 'Invalid Y coordinates'
    
    dx = x1 - x0 
    dy = y1 - y0
    if dx > dy:
        scales = dx / dy
        upper_x, upper_y = 1.0, scaled
    else:
        scaled = dx / dy
        upper_x, upper_y = scaled, 1.0
        
    assert 0 < upper_x <= 1.0, 'Calculated upper x coordinate invalid'
    assert 0 < upper_y <= 1.0, 'Calculated upper y coordinate invalid'
    
    return (0, 0, upper_x, upper_y)
```


```python
print(normalize_rectangle( (4.0, 2.0, 1.0, 5.0) ))
```


    ---------------------------------------------------------------------------

    AssertionError                            Traceback (most recent call last)

    <ipython-input-6-f7e0d48bdfd0> in <module>
    ----> 1 print(normalize_rectangle( (4.0, 2.0, 1.0, 5.0) ))
    

    <ipython-input-5-9c83b7bd16fc> in normalize_rectangle(rect)
          5     assert len(rect) == 4, 'Rectangles must contain 4 coordinates'
          6     x0, y0, x1, y1 = rect
    ----> 7     assert x0 < x1, 'Invalid X coordinates'
          8     assert y0 < y1, 'Invalid Y coordinates'
          9 


    AssertionError: Invalid X coordinates



```python
print(normalize_rectangle( (0.0, 0.0, 1.0, 5.0)))
```

    (0, 0, 0.2, 1.0)


## Transcribing DNA into RNA 
```python
input_file_name = input ('Enter the name of the input RNA file:')
```


```python
with open(input_file_name, "r") as input_file: 
    rna_sequence = input_file.read().strip()
```


```python
codon_table = {
    "UUU": "F", "UUC": "F", "UUA": "L", "UUG": "L", 
    "CUU": "L", "CUC": "L", "CUA": "L", "CUG": "L", 
    "AUU": "I", "AUG": "I", "AUA": "I", "AUG": "M", 
    "GUU": "V", "GUC": "V", "GUA": "V", "GUG": "V", 
    "UCU": "S", "UCC": "S", "UCA": "S", "UCG": "S", 
    "CCU": "P", "CCC": "P", "CCA": "P", "CCG": "P",
    "ACU": "T", "ACC": "T", "ACA": "T", "ACG": "T", 
    "GCU": "A", "GCC": "A", "GCA": "A", "GCG": "A", 
    "UAU": "Y", "UAC": "Y", "UAA": "*", "UAG": "*",
    "CAU": "H", "CAC": "H", "CAA": "Q", "CAG": "Q",
    "AAU": "N", "AAC": "N", "AAA": "K", "AAG": "K", 
    "GAU": "D", "GAC": "D", "GAA": "E", "GAG": "E", 
    "UGU": "C", "UGC": "C", "UGA": "*", "UGG": "W", 
    "CGU": "R", "CGC": "R", "CGA": "R", "CGG": "R",
    "AUG": "S", "AGC": "S", "AGA": "R", "AGG": "R", 
    "GGU": "G", "GGC": "G", "GGA": "G", "GGG": "G"}
```


```python
protein_sequence = - -
for i in range (0, len(rna_sequence), 3):
    codon = rna_sequence [i+i+3]
    if len(codon) == 3:
        amino_acid = codon_table [codon]
        if amino_acid == "*":
            break 
        protein_sequence += amino_acid
```


```python
output_file_name = input ('Enter the name of yhe output file: ')
```


```python
with open(output_file_name, "w") as output_file: 
    output_file.write(protein_sequence)
    print(f"The protein sequence has been saved to (outputa_file_name)")
```


```python
print(protein_sequence)
```

## Transcribing RNA into Portein 
```python
import numpy
data = numpy.loadtxt(fname= 'inflammation-01.csv', delimiter = ',')
```


```python
import matplotlib.pyplot
image = matplotlib.pyplot.imshow(data)
matplotlib.pyplot.show()
```


![png](output_1_0.png)



```python
ave_inflammation = numpy.mean(data,axis = 0)
ave_plot = matplotlib.pyplot.plot(ave_inflammation)
matplotlib.pyplot.show()
```


![png](output_2_0.png)



```python
min_plot = matplotlib.pyplot.plot(numpy.amin(data, axis = 0))
matplotlib.pyplot.show()
```


![png](output_3_0.png)



```python
max_plot = matplotlib.pyplot.plot(numpy.amax(data, axis = 0))
matplotlib.pyplot.show()
```


![png](output_4_0.png)



```python
fig = matplotlib.pyplot.figure(figsize = (10.0,3.0))
    
axes1 = fig.add_subplot(1, 3, 1)
axes2 = fig.add_subplot(1, 3, 2)
axes3 = fig.add_subplot(1, 3, 3)
    
axes1.set_ylabel('average')
axes1.plot(numpy.mean(data,axis = 0))
    
axes2.set_ylabel('max')
axes2.plot(numpy.amax(data,axis = 0))
    
axes3.set_ylabel('min')
axes3.plot(numpy.amin(data,axis = 0))

fig.tight_layout()

matplotlib.pyplot.savefig('inflammation.png')
matplotlib.pyplot.show()
```


![png](output_5_0.png)
