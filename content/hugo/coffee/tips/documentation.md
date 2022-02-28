---
title: "공식 Docs 활용을 위한 기본 문법 및 용어정리 1부"
date: 2022-02-26
image: "images/home/hugo1.jpg"
image_webp: "images/home/hugo.webp"
Tags: ['Hugo Documentation','Do It Yourself']     
draft: true
Description: 'Hugo로 나만의 블로그를 만들기 위해서 가장 많이 참고해야하는 자료는 공식 문서다. Hugo 설치와 테마 설치에 관해서는 한글로된 자료가 많지만 내 입맛에 맞게 블로그를 꾸미기 위한 기본적인 자료들은 거의 찾아보기 힘들다. 설령 있다해도 프론트 앤드 개발자 또는 HTML, CSS에 익숙한 사용자들을 대상으로 작성된 글이다보니 Hugo를 통해 처음 관련 문법을 접하는 개인에게는 Hugo가 어떤 방식으로 작동되는지 이해하기도 쉽지 않다.'
---
<br>

Hugo 공식 문서는 친절한 듯 친절하지 않다. 예시 코드는 제공하나 구현 결과는 없다. Hugo 언어인 Go template이 직관적이지 않기도 하다. 그러다보니 예시코드를 보고 내가 만들고자 하는 기능을 위한건지 분간하기가 쉽지않다. 그렇다고 공식 문서를 안볼 수는 없다.

초심자가 Hugo를 이해위한 자료는 턱없이 부족하고 특히 한국어로 된 자료는 더 그렇다. 대부분 글들은 이미 기본적인 웹 지식이 있는 사람이 이해할 수준이다. 그러다보니 초보자에게는 공식 문서나 블로그 글, 관련  질문들도 이해가 되지 않는다. 

Hugo를 활용해 블로그를 만들기로 다짐한 이상, 공식 문서를 읽는 것 말고는 뾰족한 방법이 없다. 이 글은 공식 문서의 수준과 초보자들의 수준을 맞추기 위한 목적으로 작성했다.  초보자들이 공식 문서를 이해하고 필요한 기능을 찾을 수 있을 정도의 글이다. 

나처럼 Hugo를 이해하는데 어려움을 겪는 사람들에게 조금이라도 도움이 됐으면 좋겠다. 



<br><br><br>

## 폴더 구조 이해하기

Hugo를 설치하면 아래와 같은 구조의 폴더가 생성된다. 기본으로 생성된 폴더들은 홈페이지를 만들기 위한 역할이 있다.  Hugo를 이해하기 위해서 먼저, 생성된 폴더가 각각 어떤 기능을 하는지 그리고 하위 항목에 있는 파일들은 어떤 기능을 하는지에 알아야한다. 물론 사용중인 테마에 따라 폴더 구조나 포함된 파일들이 조금씩 다르지만 기본 구조는 같다. 폴더 별 기능과 기본 문법만 이해한다면 테마에서 원하는 기능을 내 블로그에 쉽게 이식할 수 있다. 

<br>

hugo new site 명령어를 실행한 뒤 생성된 6개 폴더와 개별 폴더의 하위항목에 있는 파일의 기능을 설명한 뒤  추가적으로 Assets 폴더를 설명하겠다. Assets 폴더는 기본 6개 폴더에 포함되지는 않으나 대부분 테마에서 Assets 폴더를 활용하므로 알아두면 나쁠 것 없다. 

![Untitled](documentation/Untitled.png)

### archetypes

- default.md
    
    초기 Markdown 세팅값을 설정하기 위해 사용된다. cmd에 hugo new Test/Test.md를 입력하면 `content\Test` 경로에 `Test.md`가 생성된다. `default.md`에 있는 기본 세팅값이 `test.md` 에 기본으로 포함된 것을 알 수 있다. 
    
    - Dash( - )로 둘러 쌓인 내용을  `Front Matter`라 부른다.
    - Fornt Matter는 Hugo 문법에서 다양한 역할을 수행한다. 추후 문법 파트에서 자세히 다룰 예정이다.
    
    ![Untitled](documentation/Untitled%201.png)
    
    ![Untitled](documentation/Untitled%202.png)
    

<br><br><br>

### content

markdown 양식의 게시글이 저장되는 공간이다. 게시글에 사용되는 사진 및 파일들은 `content` 폴더에서는 불러올 수 없고 `static`폴더에 저장한 뒤 불러와야한다.  

> Hugo에는 content 폴더에 사진과 markdown을 한번에 관리하는 `leaf bundle` 기능이 있지만 한정된 용도로 사용되고 부가적인 기능이다보니 이 글에서는 다루지 않는다. 기본 문법과 용어를 이해하고 나면 `leaf bundle` 문서를 이해하는데는 어렵지 않으니 사용해보고 싶다면 [공식 문서](https://gohugo.io/content-management/page-bundles/#leaf-bundles)를 참고하자.

<br>

content 폴더에 파일을 넣으면 폴더명이 곧 URL 주소가 된다. 폴더 경로는 다양한 용도로 활용되기 때문에 소문자로 폴더명을 쓰고 띄어쓰기는 언더바( _ )로 하는 것을 권장한다.  
> content 폴더 내 test폴더에 위치한 `test.md`는  `웹주소\test\test` URL을  갖는다.

<br><br><br>

### data

`.yml`, `.yaml`, `.json`, `.xml`, `.toml` 확장자인 파일을 불러오기 위한 저장 공간이다.  딱히 이러한 확장자를 가진 파일을 사용할 일이 없다보니 해당 폴더도 거의 활용하되 않는다. 

<br>

### layouts

`layouts` 폴더는 블로그 뼈대가 되는 html 파일들이 저장되는 공간이므로 Hugo 구조를 이해할 때 가장 중요하다. 본인이 설치한 theme 폴더 내 `layouts` 폴더에 들어가보자. 기본적으로 `_default` ,  `partials`,  `shortcodes` 폴더와 `index.html`,  `404.html` 파일이 있다. 사용하고 있는 Theme마다 구성이 다르지만 앞에 나열한 자료들은 기본적으로 포함되어 있다. 

<br>

layouts 폴더를 이해하기 위해서는 Hugo가 페이지를 어떻게 구분하는지 부터 알아야한다. Hugo는 페이지를 `Home page`, `List page`, `Single page` 총 세 가지로 구분한다. `List page`는 분류별로 게시글을 모아서 보여주는 페이지고 `Single page`는 게시글이 담긴 페이지다.

 `Home page`를 수정하고 싶다면 Index.html를, `Single page`를 수정하고 싶다면 _default 폴더에 있는 Single.html을,  `List page`를 수정하고 싶다면 _default 폴더에 있는 list.html을 건드려야 한다.


<br>

> Theme 폴더 내에서 직접적으로 파일을 수정하지 말자. 수정이 필요한 자료가 있다면 복사해 블로그 설치 폴더에 붙여넣은 뒤 수정하자. 이렇게 하는 이유는 원본 데이터를 백업하기 위함이기도하고 Theme 제작자를 존중하는 의미라고 한다. 

<br>

- Index.html
    
    파란색으로 네모 박스 쳐져있는 영역이 index_html이 보여지는 공간이다. 

    앞에서 분명 `Home page`를 수정하기 위해서는 index.html를 건드려야 한다고 설명했는데 `Home page`에서 index.html이 화면에 차지하는 비중이 적어 의아할 것이다. 
    
    Hugo는 Baseof.html를 바탕으로 해서 다른 html 파일들을 불러오는 방식으로 페이지를 구성한다. 쉽게 말해 Baseof.html은 일종의 메인보드 역할을 한다고 보면 된다. 메인보드에 램이나 하드, cpu 등을 연결하듯 Baseof를 기본 공간으로 하여 네모 박스쳐져있는 html 파일들을 불러와 페이지 전체를 구성한다. Baseof.html 설명은 뒤 나온다. 
    
    ![Untitled](documentation/Untitled%203.png)
    *Home page 구성*
    

<br>

- _default/list.html
    
     나머지 영역은 동일하고 파란색 영역만 list.html로 대체 됐다. 아직 게시글이 하나 밖에 없어서 얼핏 보면 `home page`와 같은 페이지처럼 보이지만 타이틀이 다르다. list page는 분류에 맞는 게시글만 보여준다. 

     `list page`는 `section`과 `taxonomy`로 세분화 된다.  `section`과 `taxonomy`는 게시글을 모으는 방식에 차이가 있다. `section`은 폴더 구조에 따라 게시글을 보여주고, `taxonomy`는 게시글에 붙어있는 태그에 따라 보여준다. 하나의 게시글에 여러 태그를 달 수 있으니 태그끼리 게시글이 중복되는게 일반적이다.  
 

     > `{{.Kind}}`명령어를 `list page`에서 사용하면  수정하고 있는 페이지가 section인지 taxomomy인지 알수 있다. `section`과 `taxonmoy`에 대한 자세한 내용은 문법에서 다룬다.
  
    
    ![Untitled](documentation/Untitled%204.png)
    

<br>

- _default/single.html
    
    `single page`도 파란색 영역을 제외하고는 이전 페이지와 다른게 없다. Single page를 수정하기 위해서는 Single.html을 건드리자.
    
    ![Untitled](documentation/Untitled%205.png)
    
    <br>
    
- _default/baseof.html
    
    앞서 설명했듯 baseof.html은 메인보드 역할이다. 아래 코드는 이 블로그의 baseof.html이다. 여러 html들이 이곳에 불러와진 뒤 하나의 html로 완성된다. 이처럼 모든 page는 baseof를 통해 완전한 page가 된다.
    
    <br>

    > 하얀색으로 블럭쳐져있는 영역을 보자.  이 공간에 index.html, list.html, single.html등이 불러와 진다. 그리고 index.html, list.html, single.html 파일을 열어보면 모두 {{ define "main" }}으로 시작된다. 
    > 
    
    ![Untitled](documentation/Untitled%206.png)
    

<br>

- partials/*
    
    Partials 내 html 파일들은 기능적으로 구분된 html 조각이다. 누군가가 쓰고있는 조각을 가지고와 본인의 baseof.html에 불러오면 해당 기능을 사용할 수 있다. 
    
    모바일 버전인 경우 좌측 상단 메뉴버튼을 누르면(PC 버전인 경우 왼편에 있는 화살표`>`) 나오는 메뉴바는 offcanvas_menu.html로 구성됐다. 이 html은 bootstrap에 있는 offcanvas 기능을 단순히 복사하여 내 입맛대로 수정하여 만들었다. 
    
    이 기능을 쓰고싶다면 누그든 내 Github에 있는 offcanvas_menu.html 파일을 다운받아 partial 폴더에 넣은 뒤 baseof에서 `{{ partial ‘offcanvas_menu.html’ .}}` 명령어로 불러오면 사용할 수 있다. (단 bootstrap을 바탕으로 동작하므로 관련 파일이 설치되어있어야한다.)  
    
    이 방법과 동일하게 다른 Hugo 테마의 마음에 드는 기능을 내 블로그에 이식할 수도 있다. 
    

    
<br><br><br>

### Static

홈페이지 제작에 필요한 각종 이미지,사운드, css, js 등이 저장되는 공간이다. Static 공간에 있는 파일들은 **모두** URL주소`http://{server-url}/image.jpg` 로 변환된다. 만약 업로드를 원하지 않는 파일이 있다면 static 폴더에서 지우자. 

  <br>

> 아래 그림처럼 static 폴더에 있는 hugo1.jpg는 자동으로 url주소를 갖는다.

![Untitled](documentation/Untitled%207.png)

<br><br><br>

### Themes

이 글을 읽는 분들이라면 Theme 설치까지는 완료 했으리라 생각한다. Theme을 설치한 뒤 예상한 화면이 뜨지않아 헤메는 분들을 위해 데모 사용법을 작성했다. Theme을 설치했음에도 여전히 하얀화면이거나 Theme 사이트에서 본 것과 같이 화면이 뜨지 않는다면 아래 내용을 읽고 해결해보자.

<br>

**Theme 사이트에서 본 예시 화면 띄어보기.**

theme 폴더에는 데모버전을 운영할 수 있는 자료들이 있다.  해당 자료들을 활용하면 예시 화면을 똑같이 띄울 수 있다. 자료들은 설치한 theme 내 `exampleSite`폴더에 위치해있다. 폴더 안에 있는 자료를 모두를 복사해 블로그가 설치된 폴더에  붙여넣기 하자. 중복된다고 아무 일도 안일어나니 `대상 폴더의 파일 덮어쓰기(R)`를 과감히 누르자.  

![Untitled](documentation/Untitled%208.png)

<br>

**Hugo server 명령어 입력 시 에러 발생**

Examplesite를 붙여넣기 한 뒤 로컬 서버가 잘 작동하는가? 혹시 에러가 발생했다면 두 가지 이유 중 하나다.

- module does not exist.
    
    CMD에서 Hugo server를 입력한 뒤 아래와 비슷한 코드가 뜬다면 `Config` 내 Theme 이름과 Theme의 폴더 이름이 매칭되는지 확인해보자.
    대소문자, 띄어쓰기도 구분하니 똑같은 제목이 들어가도록 신경쓰자.
    
    ```bash
    Error: module "hugo-primer-master" not found; either add it as a Hugo Module or store 
    it in "D:\\git_local_repository\\new_blog\\themes".: module does not exist
    ```
    <br>

    ![Untitled](documentation/Untitled%209.png)
    
    <br>
    
- SCSS/SASS 에러
    
    일부 Theme은 CSS대신 SCSS 또는 SASS를 사용한다. CSS와 SCSS의 차이가 궁금하다면 구글에 검색하자.  
    
    이 문제를 해결하기 위해서는 두 가지 방법이 있다. 우리는 데모버전을 실행시키는게 목적이므로 대부분 1번 방법으로 해결된다. 만약 1번을 적용했음에도 **같은 내용의 오류**가 발생한다면 2번 방법인 hugo extension 버전을 설치해야한다.
    
    ```bash
    Error: Error building site: TOCSS: failed to transform "style.scss" (text/x-scss). 
    Check your Hugo installation; you need the extended version to build SCSS/SASS.: 
    this feature is not available in your current Hugo version,
    see https://goo.gl/YMrWcn for more information
    ```
    
    1번 방법 : 블로그 폴더(예시의 경우 new_hugo폴더)에 있는 config 파일에 아래 명령어 추가하기
        
        ```markdown
        config.toml 일 경우
        relativeURLs = true
        canonifyURLs = true
        
        config.yaml일 경우
        relativeURLs: true
        canonifyURLs: true
        ```
        
    2번 방법 : 그럼에도 여전히 같은 오류가 발생한다면 Hugo Extension을 설치하자. 일반버전에는 SCSS를 변환하는 기능이 없다. | [다운로드 링크](https://github.com/gohugoio/hugo/releases)
        
    ![Untitled](documentation/Untitled%2010.png)

<br>

- md 파일 오류  
  업데이트가 오랫동안 되지 않은 Theme을 쓰다보면 간혹 이런 문제가 발생한다. [primer css template](https://github.com/qqhann/hugo-primer)가 그 예시다. `Examplesite`을 실행시키면 아래와 같은 에러가 발생한다. 

  에러 내용을 읽어보면`rich-content.md`가 문제라는 것을 알 수 있다. 아래와 같은 문제가 발생한다면 해당 파일을 지우고 다시 실행하면 정상적으로 작동된다.

  ```bash
  ignoreErrors = ["error-missing-instagram-accesstoken"]

  WARN 2022/02/27 00:11:09 The "twitter_simple" shortcode will soon require two named parameters: 
  
  user and id. See "D:\git_local_repository\new_blog\content\blog\rich-content.md:35:1"

  Error: Error building site: logged 1 error(s)
  ```

<br><br><br>

### Assets

블로그 설치시 기본으로 포함된 폴더는 아니지만 다운받아 사용중인 테마에 종종 보인다. 역할은 `static` 폴더와 동일하다. 하지만 `static` 폴더는 모든 자료들이 자동으로  업로드 되어 각자의 URL주소를 가지고 있지만 `assets`폴더 내 파일은 {{resources.Get }} 명령어를 사용해야만 불러올 수 있다. 이 외에도 SCSS 또는 SASS 파일을 CSS로 변환하기 위해서는 `assets` 폴더를 활용해야한다. 여러분들이 다운받은 theme에 `assets` 폴더가 있다면 그 안에 SCSS파일이 들어있을 것이다.   굳이 `assets`폴더없이도 Static으로 충분히 블로그 운영이 가능하니 거의 사용할 일이 없을 것이다. `assets` 폴더의 기능에 대해 자세히 알고싶다면 링크[[https://www.regisphilibert.com/blog/2018/07/hugo-pipes-and-asset-processing-pipeline/](https://www.regisphilibert.com/blog/2018/07/hugo-pipes-and-asset-processing-pipeline/)]를 참고하기 바란다.

<br><br><br>

### Config

일종의 홈페이지 제어장치이다. Hugo에서 기본으로 제공하는 기능을 On/Off하거나 변수를 설정 용도로 사용된다. config 자체에 기능이 있다기 보다는 홈페이지 작성에 필요한 변수를 적어놓는 일종의 메모장이라고 이해하면 편하다. Config 내 변수는 `{{ .Site ~~~ }}`문법으로 어디든 불러올 수 있다.

Hugo가 제공하는 기본 Template(Google Analytics, pagination 등)들도 config로 통제된다. 기본 Template에 무엇이 있는지는 <a href="https://gohugo.io/templates/internal/#readout" target="_blank">공식 문서</a> 에서 확인할 수 있다.


아래 그림은 disqus.html이 config를 사용하는 방법이다. Config가 어떻게 활용되고 있는지 보여주는 예시이므로 disqus가 무엇인지, 어떻게 구동되는지는 신경쓰지 않아도 된다. 작동 원리는 간단하다. 

Html 파일에서 `{{.Site. 변수명(DisqusShortname) }}` 명령어를 작성하면 config 내 변수(name)를 불러온다. 이처럼 html을 직접 건드리지 않아도 config를 통해 간단하게 변경 가능하다. 활용도가 높으니 원하는 기능을 만들때 config를 활용해보자.

![Untitled](documentation/Untitled%2011.png)

<br><br><br><br>


<!-- &nbsp; &nbsp; **[2부 Hugo 문법 및 용어 설명]()** -->