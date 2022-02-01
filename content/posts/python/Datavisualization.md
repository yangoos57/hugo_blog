---
title: "Seaborn test"
date: 2022-02-01
Tags: '123'
---
##### Markdown 단축키 M
##### 함수 단축키 A


#### Goal
* the course is aimed at those with no prior programming experience.
* each chart uses short and simple code, making seaborn much faster and easier to use than many other data visualization tools (such as Excel, for instance).


```python
import pandas as pd
pd.plotting.register_matplotlib_converters() ## 뭐지?
import matplotlib.pyplot as plt  ## %가 뭐지
%matplotlib inline 
import seaborn as sns
```


```python
filepath = 'D:/git_local_repository/yangoos57/kaggle/courses/Data Visualization/Data_set/'

fifa_data = pd.read_csv(filepath+'fifa.csv', index_col='Date', parse_dates= True)
```


```python
fifa_data.head()
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
      <th>ARG</th>
      <th>BRA</th>
      <th>ESP</th>
      <th>FRA</th>
      <th>GER</th>
      <th>ITA</th>
    </tr>
    <tr>
      <th>Date</th>
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
      <th>1993-08-08</th>
      <td>5.0</td>
      <td>8.0</td>
      <td>13.0</td>
      <td>12.0</td>
      <td>1.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>1993-09-23</th>
      <td>12.0</td>
      <td>1.0</td>
      <td>14.0</td>
      <td>7.0</td>
      <td>5.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>1993-10-22</th>
      <td>9.0</td>
      <td>1.0</td>
      <td>7.0</td>
      <td>14.0</td>
      <td>4.0</td>
      <td>3.0</td>
    </tr>
    <tr>
      <th>1993-11-19</th>
      <td>9.0</td>
      <td>4.0</td>
      <td>7.0</td>
      <td>15.0</td>
      <td>3.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>1993-12-23</th>
      <td>8.0</td>
      <td>3.0</td>
      <td>5.0</td>
      <td>15.0</td>
      <td>1.0</td>
      <td>2.0</td>
    </tr>
  </tbody>
</table>
</div>



index_col = 'Data' = columm 중 index를 Data로 쓰겠다.

perse_dates = True = row label을 Data로서 활용 할 수 있게 기능 on


```python
plt.figure(figsize=(16,6))
sns.lineplot(data=fifa_data)
```




    <AxesSubplot:xlabel='Date'>




    
![png](/Datavisualization_files/Datavisualization_6_1.png)
    


### Practice


```python
spotify_data = pd.read_csv(filepath+'spotify.csv', index_col = 'Date', parse_dates=True)
spotify_data.head()
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
      <th>Shape of You</th>
      <th>Despacito</th>
      <th>Something Just Like This</th>
      <th>HUMBLE.</th>
      <th>Unforgettable</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2017-01-06</th>
      <td>12287078</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2017-01-07</th>
      <td>13190270</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2017-01-08</th>
      <td>13099919</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2017-01-09</th>
      <td>14506351</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2017-01-10</th>
      <td>14275628</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
spotify_data.tail()
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
      <th>Shape of You</th>
      <th>Despacito</th>
      <th>Something Just Like This</th>
      <th>HUMBLE.</th>
      <th>Unforgettable</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2018-01-05</th>
      <td>4492978</td>
      <td>3450315.0</td>
      <td>2408365.0</td>
      <td>2685857.0</td>
      <td>2869783.0</td>
    </tr>
    <tr>
      <th>2018-01-06</th>
      <td>4416476</td>
      <td>3394284.0</td>
      <td>2188035.0</td>
      <td>2559044.0</td>
      <td>2743748.0</td>
    </tr>
    <tr>
      <th>2018-01-07</th>
      <td>4009104</td>
      <td>3020789.0</td>
      <td>1908129.0</td>
      <td>2350985.0</td>
      <td>2441045.0</td>
    </tr>
    <tr>
      <th>2018-01-08</th>
      <td>4135505</td>
      <td>2755266.0</td>
      <td>2023251.0</td>
      <td>2523265.0</td>
      <td>2622693.0</td>
    </tr>
    <tr>
      <th>2018-01-09</th>
      <td>4168506</td>
      <td>2791601.0</td>
      <td>2058016.0</td>
      <td>2727678.0</td>
      <td>2627334.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
sns.lineplot(data=spotify_data)
```




    <AxesSubplot:xlabel='Date'>




    
![png](/Datavisualization_files/Datavisualization_10_1.png)
    



```python
## 분석결과 사이즈 설정(W,H)
plt.figure(figsize=(14,6)) 

 #분석결과 제목
plt.title("Daily Global Streams of Popular Songs in 2017-2018")

sns.lineplot(data=spotify_data)
```




    <AxesSubplot:title={'center':'Daily Global Streams of Popular Songs in 2017-2018'}, xlabel='Date'>




    
![png](/Datavisualization_files/Datavisualization_11_1.png)
    



```python
list(spotify_data.columns)
```




    ['Shape of You',
     'Despacito',
     'Something Just Like This',
     'HUMBLE.',
     'Unforgettable']




```python
plt.figure(figsize=(14,6))
plt.title("Daily Global Streams of Popular Songs in 2017-2018")

# line chart showing stream of a specific music
sns.lineplot(data=spotify_data['Shape of You'], label="Shape of You")
sns.lineplot(data=spotify_data['Despacito'], label="Despacito")
plt.xlabel("Date")
```




    Text(0.5, 0, 'Date')




    
![png](/Datavisualization_files/Datavisualization_13_1.png)
    



```python
flight_data = pd.read_csv(filepath+'flight_delays.csv', index_col='Month')

```


```python
flight_data
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
      <th>AA</th>
      <th>AS</th>
      <th>B6</th>
      <th>DL</th>
      <th>EV</th>
      <th>F9</th>
      <th>HA</th>
      <th>MQ</th>
      <th>NK</th>
      <th>OO</th>
      <th>UA</th>
      <th>US</th>
      <th>VX</th>
      <th>WN</th>
    </tr>
    <tr>
      <th>Month</th>
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
      <th>1</th>
      <td>6.955843</td>
      <td>-0.320888</td>
      <td>7.347281</td>
      <td>-2.043847</td>
      <td>8.537497</td>
      <td>18.357238</td>
      <td>3.512640</td>
      <td>18.164974</td>
      <td>11.398054</td>
      <td>10.889894</td>
      <td>6.352729</td>
      <td>3.107457</td>
      <td>1.420702</td>
      <td>3.389466</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7.530204</td>
      <td>-0.782923</td>
      <td>18.657673</td>
      <td>5.614745</td>
      <td>10.417236</td>
      <td>27.424179</td>
      <td>6.029967</td>
      <td>21.301627</td>
      <td>16.474466</td>
      <td>9.588895</td>
      <td>7.260662</td>
      <td>7.114455</td>
      <td>7.784410</td>
      <td>3.501363</td>
    </tr>
    <tr>
      <th>3</th>
      <td>6.693587</td>
      <td>-0.544731</td>
      <td>10.741317</td>
      <td>2.077965</td>
      <td>6.730101</td>
      <td>20.074855</td>
      <td>3.468383</td>
      <td>11.018418</td>
      <td>10.039118</td>
      <td>3.181693</td>
      <td>4.892212</td>
      <td>3.330787</td>
      <td>5.348207</td>
      <td>3.263341</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4.931778</td>
      <td>-3.009003</td>
      <td>2.780105</td>
      <td>0.083343</td>
      <td>4.821253</td>
      <td>12.640440</td>
      <td>0.011022</td>
      <td>5.131228</td>
      <td>8.766224</td>
      <td>3.223796</td>
      <td>4.376092</td>
      <td>2.660290</td>
      <td>0.995507</td>
      <td>2.996399</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5.173878</td>
      <td>-1.716398</td>
      <td>-0.709019</td>
      <td>0.149333</td>
      <td>7.724290</td>
      <td>13.007554</td>
      <td>0.826426</td>
      <td>5.466790</td>
      <td>22.397347</td>
      <td>4.141162</td>
      <td>6.827695</td>
      <td>0.681605</td>
      <td>7.102021</td>
      <td>5.680777</td>
    </tr>
    <tr>
      <th>6</th>
      <td>8.191017</td>
      <td>-0.220621</td>
      <td>5.047155</td>
      <td>4.419594</td>
      <td>13.952793</td>
      <td>19.712951</td>
      <td>0.882786</td>
      <td>9.639323</td>
      <td>35.561501</td>
      <td>8.338477</td>
      <td>16.932663</td>
      <td>5.766296</td>
      <td>5.779415</td>
      <td>10.743462</td>
    </tr>
    <tr>
      <th>7</th>
      <td>3.870440</td>
      <td>0.377408</td>
      <td>5.841454</td>
      <td>1.204862</td>
      <td>6.926421</td>
      <td>14.464543</td>
      <td>2.001586</td>
      <td>3.980289</td>
      <td>14.352382</td>
      <td>6.790333</td>
      <td>10.262551</td>
      <td>NaN</td>
      <td>7.135773</td>
      <td>10.504942</td>
    </tr>
    <tr>
      <th>8</th>
      <td>3.193907</td>
      <td>2.503899</td>
      <td>9.280950</td>
      <td>0.653114</td>
      <td>5.154422</td>
      <td>9.175737</td>
      <td>7.448029</td>
      <td>1.896565</td>
      <td>20.519018</td>
      <td>5.606689</td>
      <td>5.014041</td>
      <td>NaN</td>
      <td>5.106221</td>
      <td>5.532108</td>
    </tr>
    <tr>
      <th>9</th>
      <td>-1.432732</td>
      <td>-1.813800</td>
      <td>3.539154</td>
      <td>-3.703377</td>
      <td>0.851062</td>
      <td>0.978460</td>
      <td>3.696915</td>
      <td>-2.167268</td>
      <td>8.000101</td>
      <td>1.530896</td>
      <td>-1.794265</td>
      <td>NaN</td>
      <td>0.070998</td>
      <td>-1.336260</td>
    </tr>
    <tr>
      <th>10</th>
      <td>-0.580930</td>
      <td>-2.993617</td>
      <td>3.676787</td>
      <td>-5.011516</td>
      <td>2.303760</td>
      <td>0.082127</td>
      <td>0.467074</td>
      <td>-3.735054</td>
      <td>6.810736</td>
      <td>1.750897</td>
      <td>-2.456542</td>
      <td>NaN</td>
      <td>2.254278</td>
      <td>-0.688851</td>
    </tr>
    <tr>
      <th>11</th>
      <td>0.772630</td>
      <td>-1.916516</td>
      <td>1.418299</td>
      <td>-3.175414</td>
      <td>4.415930</td>
      <td>11.164527</td>
      <td>-2.719894</td>
      <td>0.220061</td>
      <td>7.543881</td>
      <td>4.925548</td>
      <td>0.281064</td>
      <td>NaN</td>
      <td>0.116370</td>
      <td>0.995684</td>
    </tr>
    <tr>
      <th>12</th>
      <td>4.149684</td>
      <td>-1.846681</td>
      <td>13.839290</td>
      <td>2.504595</td>
      <td>6.685176</td>
      <td>9.346221</td>
      <td>-1.706475</td>
      <td>0.662486</td>
      <td>12.733123</td>
      <td>10.947612</td>
      <td>7.012079</td>
      <td>NaN</td>
      <td>13.498720</td>
      <td>6.720893</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.figure(figsize=(10,6))
plt.title("Average Arrival Delay for spirit Airlines Flights, by Month")
sns.barplot(x=flight_data.index, y=flight_data['NK'])
plt.ylabel("Arrival delay (in minutes)")
```




    Text(0, 0.5, 'Arrival delay (in minutes)')




    
![png](/Datavisualization_files/Datavisualization_16_1.png)
    



```python
plt.figure(figsize=(14,7))
plt.title("Average Arrival Delay for Each Airline, by Month")

sns.heatmap(data=flight_data,annot=True)
plt.xlabel("Airline")

```




    Text(0.5, 42.0, 'Airline')




    
![png](/Datavisualization_files/Datavisualization_17_1.png)
    



```python
iris_data = pd.read_csv(filepath+'iris.csv')

iris_data.head()
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
      <th>Id</th>
      <th>Sepal Length (cm)</th>
      <th>Sepal Width (cm)</th>
      <th>Petal Length (cm)</th>
      <th>Petal Width (cm)</th>
      <th>Species</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>5.1</td>
      <td>3.5</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>4.9</td>
      <td>3.0</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.7</td>
      <td>3.2</td>
      <td>1.3</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>4.6</td>
      <td>3.1</td>
      <td>1.5</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>5.0</td>
      <td>3.6</td>
      <td>1.4</td>
      <td>0.2</td>
      <td>Iris-setosa</td>
    </tr>
  </tbody>
</table>
</div>




```python
sns.distplot(a=iris_data['Petal Length (cm)'], kde=False)
```

    C:/Users/679oo/anaconda3/lib/site-packages/seaborn/distributions.py:2551: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    




    <AxesSubplot:xlabel='Petal Length (cm)'>




    
![png](/Datavisualization_files/Datavisualization_19_2.png)
    



```python
sns.distplot(a=iris_data['Petal Length (cm)'], kde=True)
```




    <AxesSubplot:xlabel='Petal Length (cm)', ylabel='Density'>




    
![png](/Datavisualization_files/Datavisualization_20_1.png)
    



```python
sns.kdeplot(data=iris_data['Petal Length (cm)'], shade=True)
```




    <AxesSubplot:xlabel='Petal Length (cm)', ylabel='Density'>




    
![png](/Datavisualization_files/Datavisualization_21_1.png)
    



```python
sns.jointplot(x=iris_data['Petal Length (cm)'], y=iris_data['Sepal Width (cm)'], kind='kde')
```




    <seaborn.axisgrid.JointGrid at 0x1fc48b64fa0>




    
![png](/Datavisualization_files/Datavisualization_22_1.png)
    


![스크린샷](https://imgur.com/2VmgDnF.png)


