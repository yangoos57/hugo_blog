---
title: "게시글에 사진 확대기능 추가하기"
date: 2022-02-21
image: "images/home/hugo1.jpg"
image_webp: "images/home/hugo.webp"
HUGO: "DIY"
draft: true
Description: 'Hugo 게시글에 포함된 이미지 파일을 확대 할 수 있는 기능을 추가한다. HTML, CSS, Hugo에 익숙하지 않은 사용자들도 쉽게 따라할 수 있도록 작성하였다.  '
---

<br>

## 구현하고자 하는 기능

![Honeycam 2022-02-21 13-50-00.gif](zoom-image/Honeycam_2022-02-21_13-50-00.gif)

<br><br>

## 들어가기에 앞서

해당 게시글은 Hugo를 활용해 블로그를 개설하던 중 겪었던 시행착오를 정리하기 위한 목적으로 작성했다.  

Hugo를 접하기 전만해도 HTML과 CSS에 대해 전혀 몰랐기에 원하는 기능을 구현하기 위해 상당히 많은 시간을 투자했다. 특히 Hugo 관련 한글 자료를 찾기가 매우 어려워 기능을 어떤 방식으로 구현해야하는지 방법을 이해하는데 오랜 시간이 걸렸다. 

나처럼 HTML과 CSS에 대한 사전 지식 없이 Hugo 블로그를 개설하고자 하는 사람은 많이 없겠지만 나와 비슷한 상황에 처해있는 소수의 사람들을 위해 자그마한 실마리를 제공하고자 글을 작성했다. 

여담으로 나처럼 HTML과 CSS에 대한 사전 지식없이 무작정 Hugo 블로그를 개설하고자 하는 분들이 있다면 HTML과 CSS를 배울 수 있는 좋은 기회이니 포기하지말고 끝까지 만드는 것을 권장한다.

<br><br>

## 설치 절차

### 1. medium-zoom.js 파일 다운로드
   
-   [다운로드 경로](https://github.com/francoischalifour/medium-zoom#installation)
    

- **Normal** → 마우스 우클릭 다른 이름으로 링크 저장 → medium-zoom.js 다운
    
    ![Untitled](zoom-image/Untitled.png)
    

<br><br>

### 2. medium-zoom.js 파일을 Static폴더로 이동

- `Static` 폴더는 Hugo에서 파일을 불러오기 위한 기본 저장소이다.  js파일 외 css파일 image파일 등 홈페이지 작성에 필요한 파일들을 저장한 뒤, HTML에서 사용되는 명령어 또는 Hugo 명령어를 활용해 해당 폴더 내  파일을 불러온다.

- 다운로드 받은 파일을 `D:\블로그 설치된 폴더\static\js` 에 붙여 넣는다.  js 폴더가 없으면 폴더를 만들어 넣으면 된다.
    
    *내가 설치한 블로그 폴더명은 `hugo_blog` 이다. 파일을 어디에 넣어야 할지 모르겠다면 아래 그림 경로를 보고 저장하자. 만약 폴더가 없다면 만들어서 저장하면 된다.* 
    
    ![Untitled](zoom-image/Untitled%201.png)
    

<br><br>

### 3. zoom_custom.js 생성

- `zoom_custom.js`는 `medium-zoom.js`을 실행하기 위한 명령어다.

- `medium-zoom.js`파일 복사본을 만든 뒤 파일명을 `zoom_custom.js`로 바꾼다.

- `vscode` 에서  `zoom_custom.js`를 열어 내용을 지우고 아래 그림 처럼 코드를 붙여넣고 저장한다.
    
    ![Untitled](zoom-image/Untitled%202.png)
    
    아래 코드를 그대로 붙여 넣으면 된다.
    
    ```css
    mediumZoom('img', {
      margin: 0, /* The space outside the zoomed image */
      scrollOffset: 40, /* The number of pixels to scroll to close the zoom */
      container: null, /* The viewport to render the zoom in */
      template: null, /* The template element to display on zoom */
      background: 'rgba(0, 0, 0, 0.5)' /* 확대 시 배경 색상 조정*/
    });
    ```
    

<br><br>

### 4. medium-zoom.js와 medium-zoom.js 불러오기

- 사용하고 있는 Theme이 있는 경우 Theme폴더로 (나 같은 경우 apollo-hugo)에 들어가  layouts폴더에 있는 `head.html`을 복사해 `D:\블로그 설치 폴더\layouts\partials` 에 붙여넣는다.
    
    *블로그가 설치된 폴더에 layouts 폴더 또는 partials 폴더가 없다면 만든다.*
    
    ![Untitled](zoom-image/Untitled%203.png)
    
- Theme 안에 있는 html 파일을 굳이 밖으로 끌고와 새로 붙여 넣는 이유는 hugo의 관습 때문이다. 사용하고 있는 template 원본을 훼손하지 않기 위한 목적이기도 하고 제작자를 존중한다는 의미라고 한다.
    
    *theme 내 layouts 폴더와 블로그 설치 폴더의 layouts에 같은 파일이 있다면 블로그 설치 폴더의 파일을 우선순위로 불러온다.* 
    
- `vscode`에서 `Head.html`을  불러온 뒤 아래 코드를 맨 하단에 붙여넣는다.
    
    ![Untitled](zoom-image/Untitled%204.png)
    
    ```html
    {{if .IsPage}}  <!-- Single Page에만 작동하도록 설정하는 Hugo 명령어 -->
        <script defer language="javascript" type="text/javascript"  src="{{ "/js/medium-zoom.js" | urlize | relURL }}"></script>
        <!-- js 파일을 js폴더에 넣지 않았다면 src를 파일이 들어간 위치로 경로로 수정해야한다. -->
        <script defer language="javascript" type="text/javascript"  src="{{ "/js/zoom_custom.js" | urlize | relURL }}"></script>
        <!-- js 파일을 js폴더에 넣지 않았다면 src를 파일이 들어간 위치로 경로로 수정해야한다. -->
    {{end}}
    ```
    

<br><br>

### 5. 작동 여부 확인

![Honeycam 2022-02-21 16-16-32.gif](zoom-image/Honeycam_2022-02-21_16-16-32.gif)