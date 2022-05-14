---
title: "상황에 맞는 row filtering 사용하기"
date: 2022-05-11T13:47:07+09:00
image: "images/home/statistic.png"
Tags: ['query','isin','boolean masking']
draft: true
---
<br>

## 배경 
데이터를 다루면 filtering은 일상이다. 그러다보니 pandas 라이브러리에도 필터링 관련 함수가 여럿 존재한다. 많은 사람들은 그중에서 2~3개정도 사용할줄 알고 그중 하나를 주로 사용해 필터링을 한다. 

한번 정도 필터링 하는 경우야 어떤 방법이든 오래 걸리지 않고 오히려 새로운 방법을 써봤자 익숙해지는데 시간을 써야하고 머리만 복잡해지므로 굳이 새로운 함수를 배워야 할 필요성을 느끼지 못한다.


하지만 조금이라도 큰 데이터를 다룰 때 하나의 방법으로만 필터링을 하면 이곳 저곳에서 비효율이 발생하게 된다. 여러 비효율 중에서 가독성과 처리 효율을 중심으로 세 종류의 함수를 추천하고자 한다. 상황별 적절한 함수를 쓴다면 코드 가독성도 좋아지고 필터링에서 발생하는 비효율을 줄일 수 있다. 
<br><br><br>

## DataFrame.query()      
 query 함수는 row filtering 하기에 너무 좋은 기능인데 비해 많이 쓰이지 않는 것 같다. 100,000개 이상 row를 다룰 때 성능이 좋다고 하는데, 성능면보다는 필터링을 직관적으로 알 수 있고 코드를 짧게 쓸 수 있어 가독성이 좋아지는 장점에 초점을 맞추고 싶다. 
 <br><br>


> ### 장점

  * **필터링을 단순하게 표현할 수 있다.**
      
     ```python
        import pandas as pd
        import numpy as np

        df = pd.DataFrame(10+60.5*np.random.randn(1000000,3)) # row 100만개, column 3개 df 생성
        df.columns = ['num','num2','num3']
        pd.set_option('float_format', '{:f}'.format)
        df.describe()
        
        # +-------+-------------+-------------+-------------+
        # |       |         num |        num2 |        num3 |
        # +-------+-------------+-------------+-------------+
        # | count |   1000000   |   1000000   |   1000000   |
        # +-------+-------------+-------------+-------------+
        # |  min  | -282.352587 | -287.677283 | -300.389316 |
        # +-------+-------------+-------------+-------------+
        # |  50%  |   9.997371  |  10.014887  |   9.953583  |
        # +-------+-------------+-------------+-------------+
        # |  max  |  308.740897 |  292.197571 |  294.566926 |
        # +-------+-------------+-------------+-------------+
        
    
        '''
        필터링 조건 
        10 < num < 100
        0.5 < num2 < 10
        255 < num3 < 50
        '''

        # query
        result = df.query('10 < num < 100 & 0.5 < num2 < 10 & 25< num3 < 50')

        len(result)   >>>  3982


        #boolean mask
        BM = (df['num'] > 10) & (df['num'] < 100)
        BM2 = (df['num2'] > 0.5) & (df['num2'] < 10)
        BM3 = (df['num3'] > 25) & (df['num3'] < 50)
        result = df[BM & BM2 & BM3]

        len(result)  >>>  3982 
        
    ```

    <br><br>

  * **검색용으로 훌륭하다.** 
      
    아마 원하는 값을 찾는데 가장 빠른 방법이지 않을까 싶다.
    <br>

    ```python
    sub_station = pd.read_csv('\sub_station.csv',encoding='CP949') # 서울 공공데이터 지하철정보

    sub_station.query('역사명 == "김포공항"')

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
          <th>역사_ID</th>
          <th>역사명</th>
          <th>호선</th>
          <th>경도</th>
          <th>위도</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>2</th>
          <td>4929</td>
          <td>김포공항</td>
          <td>김포골드라인</td>
          <td>126.801868</td>
          <td>37.562360</td>
        </tr>
        <tr>
          <th>88</th>
          <td>4207</td>
          <td>김포공항</td>
          <td>공항철도1호선</td>
          <td>126.801904</td>
          <td>37.561842</td>
        </tr>
        <tr>
          <th>130</th>
          <td>4102</td>
          <td>김포공항</td>
          <td>9호선</td>
          <td>126.802152</td>
          <td>37.561916</td>
        </tr>
        <tr>
          <th>352</th>
          <td>2513</td>
          <td>김포공항</td>
          <td>5호선</td>
          <td>126.801292</td>
          <td>37.562384</td>
        </tr>
      </tbody>
    </table>
    </div>

    <br>


  * **한번에 여러 values를 검색할 수 있다.**
  
    Boolean mask는 하나의 조건문에 하나의  value만 검색 가능하다. 그러다보니 코드가 한도없이 길어질 수 있다. query는 column에서 찾고자 하는 value를 list나 array 등으로 묶어주기만 하면 간단하게 검색할 수 있다.

    ```python
    stations = ['김포공항', '신논현']
    sub_station.query('역사명 == @stations').sort_values(by='역사명',ascending=False)
      # @를 붙이면 변수 취급
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
          <th>역사_ID</th>
          <th>역사명</th>
          <th>호선</th>
          <th>경도</th>
          <th>위도</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>107</th>
          <td>4125</td>
          <td>신논현</td>
          <td>9호선</td>
          <td>127.025060</td>
          <td>37.504598</td>
        </tr>
        <tr>
          <th>2</th>
          <td>4929</td>
          <td>김포공항</td>
          <td>김포골드라인</td>
          <td>126.801868</td>
          <td>37.562360</td>
        </tr>
        <tr>
          <th>88</th>
          <td>4207</td>
          <td>김포공항</td>
          <td>공항철도1호선</td>
          <td>126.801904</td>
          <td>37.561842</td>
        </tr>
        <tr>
          <th>130</th>
          <td>4102</td>
          <td>김포공항</td>
          <td>9호선</td>
          <td>126.802152</td>
          <td>37.561916</td>
        </tr>
        <tr>
          <th>352</th>
          <td>2513</td>
          <td>김포공항</td>
          <td>5호선</td>
          <td>126.801292</td>
          <td>37.562384</td>
        </tr>
      </tbody>
    </table>
    </div>
    

    <br>

  <!-- * **직관적으로 좋고 대용량 자료라도 느리지 않다.** 
  
    pandas 공식문서에서도 처리속도를 빠르게 하는 방법중 하나로 query를 추천하고 있다.
    <br><br><br> -->



> ### 단점
*  **for문을 써야하는 경우 처리속도가 느리다.**

   직관적이고 쉽게 코드를 짠다는 점이 장점이자 단점이다. 그러다보니 사용할 수 있는 문법이 제한적이다. 물론 제한적이라고 하나 써보면 왠만한 filtering은 query로 처리할 수 있다.
    
    <br>

* **사용가능한 문법이 제한된다.**

    사실 사용가능한 문법이 적을뿐이지 필요한 기능은 전부 갖추고 있다. 필터링이 필요한 대부분 상황은 query 하나로 해결된다. query 함수가 문법이 제한적인 이유는 처리절차 내에 eval() 함수를 사용하기 때문이다.
    
    <br>

    **These operations are supported by pandas.eval():**
  >
  >  - Arithmetic operations except for the left shift (`<<`) and right shift (`>>`) operators, e.g., `df + 2 * pi / s ** 4 % 42 - the_golden_ratio`
  >
  > - Comparison operations, including chained comparisons, e.g., `2 < df < df2`
  > - Boolean operations, e.g., `df < df2 and df3 < df4 or not df_bool`
  > - `list` and `tuple` literals, e.g., `[1, 2]` or `(1, 2)`
  > - Attribute access, e.g., `df.a`
  > - Subscript expressions, e.g., `df[0]`
  > - Simple variable evaluation, e.g., `pd.eval("df")` (this is not very useful)
  > - Math functions: `sin`, `cos`, `exp`, `log`, `expm1`, `log1p`, `sqrt`, `sinh`, `cosh`, `tanh`, `arcsin`, `arccos`, `arctan`, `arccosh`, `arcsinh`, `arctanh`, `abs`, `arctan2` and `log10`.

    <br>

    **This Python syntax is not allowed:**
  >
  > Expressions
  >       
  > - Function calls other than math functions.
  > 
  > - `is/is not` operations
  > 
  > - `if` expressionslambda expressions
  > 
  > - `list/set/dict`comprehensions
  > 
  > - Literal `dict` and `set` expressions
  > 
  > - `yield` expressions
  > 
  > Generator expressions
  > 
  > - Boolean expressions consisting of only scalar values
  > 
  > - Statements
  > 
  > - Neither simple nor compound statements are allowed. 
  > 
  > - This includes things like `for, while, and if`.

  출처 : [Pandas 공식홈페이지](https://pandas.pydata.org/docs/user_guide/enhancingperf.html#supported-syntax)
    
<br><br><br><br>
    
## boolean masking

    
> ### 장점 

* **처리속도가 빠르다.**

  한번 사용한다면 세가지 중 어떠한 함수를 사용해도 체감상 차이가 없다. 하지만 데이터 분석을 하다보면 flitering 함수와 loop를 함께 사용하는 경우가 많다. 

  그럴때 boolean masking이 빛을 발휘한다. 아래 그래프는 row가 1200만개인 데이터를 가지고, 300번 반복처리한 결과이다. 단위는 초당 loop를 처리한 횟수이다.  boolean masking은 초당 10회의 loop를 수행한 반면 query는 초당 5회로 연산속도가 2배나 차이난다. 

  ![png](Python/Pandas/output_1.png)

  <br>

> ### 단점

* **필터링이 직관적이지 않다.**
  
  boolean mask가 많아질수록 가독성이 떨어진다. 
  조건이 많아질수록 변수도 늘어나고 잦은 실수가 발생한다.  
<br><br> 

* **한 번에 하나의 필터링만 가능하다**
  
  query나 isin은 같은 column 내에 있는 여러 value를 처리할 수 있다. 하지만 boolean masking은 values별로 일일히 변수를 만들어야한다.
  <br><br> <br><br> 

## Dataframe.isin(list())

> ### 장점
* **여러 value를 한 번에 처리할 수 있다.**
  
  isin은 query와 boolean mask의 중간 위치에있다. boolean mask가 가지고 있는 단점을 보완하며 query와 마찬가지로 하나의 column의 여러 value에 대한 처리가 가능하다.  뿐만아니라 boolean mask보다는 연산속도가 느리지만 query보다는 빠르다. 
  <br><br> 

> ### 단점

* **가독성이 떨어진다.**
  
  isin 역시 boolean mask와 마찬가지로 필터링이 직관적이지 않다는 단점이 있다. 그래도 변수를 줄이는 장점이 있어서 boolean mask보다는 상대적 가독성이 좋다. 
<br><br><br><br>


## 정리

빠른 속도가 필요하거나 query로 할 수 없는 경우를 제외하고는 query함수를 추천한다. 반복문을 써야하는 경우엔 하나의 column에서 찾아야하는 value가 2개 이상일 경우 isin을 추천한다. 빠른속도를 중요시하거나 하나의 value만 찾는 경우 boolean mask를 추천한다.


|함수             | 반복문 x | 반복문 0, 값 =1 | 반복문 0 , 값 > 1|
|:---------------:|:-------:|:---------------:|:-----------------:|
|**query**        |   O    |                  |         △        | 
|**boolean_mask** |        |         O        |                   |  
|**isin**         |        |                  |         O         |

