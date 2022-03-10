---
title: "Hugo 게시글 내 코드 박스(syntax highlighter) 사용하기 "
date: 2022-03-10
image: "images/home/hugo1.jpg"
Tags: ['코드 박스', 'syntax highlighter','prism']
draft: false
Description: 'Hugo 게시글 내 syntax highlighter를 변경하는 글이다. HTML, CSS, Hugo에 익숙하지 않은 사용자들도 이 글을 보고 설치할 수 있도록 작성했다. syntax highlighter로 prism을 활용한다.'
Summary: 'Hugo 게시글 내 syntax highlighter를 변경하는 글이다. HTML, CSS, Hugo에 익숙하지 않은 사용자들도 이 글을 보고 설치할 수 있도록 작성했다. syntax highlighter로 prism을 활용한다.'
---
<br>

## 구현하고자 하는 기능

**Syntax highlighter 예시**
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import os

### 현재 경로
os.getcwd()

### 변수 불러오기
continent_poss = country_df.Continent.unique()
bycontinentyear_df = country_df.groupby(['Continent', 'year'])['Perceptions_of_corruption'].mean()
print(bycontinentyear_df.loc['Asia',[2010,2019]])

### 옵션
markers_options = ['o','^','p','8','s','p','*']

### lineplot 구현
for i, c in enumerate(continent_poss):
    plt.plot([2010,2019], bycontinentyear_df.loc[c,[2010,2019]], label=c, marker = markers_options[i])

### plot 수정
plt.xticks([2010,2019])
plt.legend(bbox_to_anchor=(1.05, 1.0))
plt.title('Perceptions_of_corruption')


plt.show()
```

<br><br>

## 설치 절차

### 1. prism.js와 prism.css 다운로드
- prism[(링크)](https://prismjs.com/download.html#themes=prism&languages=markup+css+clike+javascript)은 syntax highlighter를 원하는 스타일로 만들 수 있도록 도와주는 사이트이다. 
  
- 해당 사이트에 들어가 마음에 드는 Themes, 언어, 추가 기능(plug-ins)을 선택한 뒤 페이지 맨 아래로 내려가 js와 css를 다운 받는다.

![Untitled](hugo/tips/prism/prism1.png)

    

<br>

### 2. 다운받은 prism.js, prism.css를 static폴더로 이동

- `Static` 폴더는 홈페이지를 꾸미는데 필요한 파일을 불러오는 용도로 활용된다. 해당 폴더에 필요한 파일을 저장한 뒤 HTML 명령어 또는 Hugo 명령어를 사용하면 불러올 수 있다.

- 다운로드 받은 파일을 `D:\블로그 설치된 폴더\static\js`와 `\css`에 각각 붙여넣는다. 만약 static 폴더에 js 폴더와 css 폴더가 없으면 폴더를 만든 뒤 붙여넣는다.
    
    <br>


    > *현재 설치 중인 폴더 이름은 `hugo_blog` 이다. 다운받은 파일을 어디에 저장해야 할지 모르겠다면 아래 그림에 나와있는 경로를 참고하자.*

    
    ![Untitled](hugo/tips/prism/prism2.png)
    

<br><br>

### 3. html에서 js파일과 css파일 불러오기
- 사용중인 Theme이 있고 layout 폴더를 건드려본적 없다면, 우선 `Theme` 폴더에 들어가 `head.html` 를 가지고 와야한다.
 
- `Themes/사용중인 Theme 제목/layouts/partial`에 있는 `head.html`을 복사한 뒤 `D:\블로그 설치 폴더\layouts\partials` 에 붙여넣자.
    
    ![Untitled](hugo/tips/zooming/Untitled%205.png)
        
<br>

- `head.html`을 vscode와 같은 에디터에서 불러온 뒤 맨 하단에 아래 코드를 붙여 넣는다. 
    
    ```html
    {{if .IsPage}}  <!-- Single Page에만 작동하도록 설정하는 Hugo 명령어 -->
    <!--Prism-->
    <link rel="stylesheet" href="{{ "css/prism.css" | relURL }}" media="none" onload="this.media='all';">
    <!-- 저장된 경로가 static/css/prism.css이 아니라면 src 경로를 수정해야한다. -->
    <script defer language="javascript" type="text/javascript"  src="{{ "/js/prism.js" | urlize | relURL }}"></script>
    <!-- 저장된 경로가 static/js/prism.js이 아니라면 src 경로를 수정해야한다. -->
    {{end}}
    ```
    ![Untitled](hugo/tips/prism/prism3.png)

<br><br>

### 4. 작동여부 확인
- syntax highlighter 설치를 완료했다. 정상 작동하는지, 원하는 기능이 포함됐는지 확인해보자.
- 로컬 서버를 실행한 체로 설치했다면 서버 종료 후 다시 실행하자.
