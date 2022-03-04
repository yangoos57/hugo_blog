---
title: "1부 Hugo Docs 활용을 위한 폴더 구조 이해"
date: 2022-03-04
image: "images/home/hugo1.jpg"
image_webp: "images/home/hugo.webp"
Tags: ['Hugo Documentation','Do It Yourself','공식 문서 활용하기','폴더 구조']     
draft: false
Description: 'Hugo로 나만의 블로그를 만들기 위해서는 휴고 공식 문서(Hugo Documentation)를 활용해야 한다. Hugo 설치와 테마 설치에 관해서는 한글로된 자료가 많지만 내 입맛에 맞게 블로그를 꾸미기 위한 기본적인 자료들은 거의 찾아보기 힘들다. 설령 있다해도 프론트 앤드 개발자 또는 HTML, CSS에 익숙한 사용자들을 대상으로 작성된 글이다보니 Hugo를 통해 처음 관련 문법을 접하는 개인에게는 Hugo가 어떤 방식으로 작동되는지 이해하기도 쉽지 않다.'
Summary: 'Hugo로 나만의 블로그를 만들기 위해서는 휴고 공식 문서(Hugo Documentation)를 활용해야 한다. Hugo 설치와 테마 설치에 관해서는 한글로된 자료가 많지만 내 입맛에 맞게 블로그를 꾸미기 위한 기본적인 자료들은 거의 찾아보기 힘들다.'
---
<br>

Hugo 공식 문서는 친절한 듯 친절하지 않다. 예시 코드를 제공하나 해당 코드가 어떤 역할을 하는지 적용해보지 않고선 알 방법이 없다. 그리고 Hugo 언어인 Go template은 직관적이지 않다. 나같이 Python으로 프로그래밍 언어를 처음 배운 사람에게는 더더욱 그렇다. 그러다보니 공식문서에서 제공하는 예시코드를 보고도 내가 찾고자 하는 기능인지 분간하기 쉽지않다. 

<br>

그렇다고 공식 문서를 보지 않을 수는 없다. 초보자가 Hugo를 이해하기 위한 자료는 턱없이 부족하기 때문이다. 특히 한국어로 된 자료는 더 그렇다. 대부분 글들은 기본으로 웹 지식이 있는 사람이 이해할만한 수준이다. 나같이 HTML, CSS가 뭔지도 모르는 초보에게는 공식 문서나 다른 글이나 이해 못하기는 마찬가지다.

<br>

어찌됐건 Hugo를 활용해 블로그를 만들기로 한 이상, 공식 문서를 활용하는 것 말고는 뾰족한 수가 없다. 하지만 공식 문서를 읽기위한 기본 수준과 초보자가 가진 기본 수준에는 큰 격차가 있다. 그렇다고 이를 보완할 문서는 거의 없다고 보면 된다. 한글로 된 파일은 더욱이 없다. 따라서 이 글은 초보자가 공식문서를 읽을 정도의 수준을 끌어올리기 위한 목적으로 작성했다. 1부와 2부를 읽고 나면 초보자들도 어느정도 공식 문서를 이해하고 필요한 기능을 찾을 수 있는 수준이 될거라 생각한다.

<br>

아무것도 모르고 블로그 하나 만들어보겠다는 생각으로 처음 Hugo를 접했다. HTML, CSS이 뭔지조차 모른체로 구글 검색과 몇몇 한글자료, 공식 문서에 있는 유튜브를 보면서 하나하나 알아갔다. 지금 이 글을 쓰는 이유는 이렇게 깨지면서 배웠던 시간이 너무 아까워서다. 누군가에게 도움을 준다면 시간 낭비를 조금이나마 보상 받을 거라는 생각으로 글을 썼다. 이런 오기로 작성된 글이 누군가에게는 도움이 됐으면 좋겠다. 



<br><br><br>

## 폴더 구조 이해하기
Hugo 문법을 배우기 전 폴더 구조를 우선적으로 이해해야한다. 내가 수정하고 싶은 페이지가 어떤 폴더, 어떤 파일인지 알아야 배운 문법을 적절하게 사용할 수 있기 때문이다. 

이 글을 읽는 중이라면 Hugo 설치와 Theme까지 적용했으리라 생각한다. 설치와 관련한 게시글은 한글로 된 것도 많으니 본인이 이해하기 쉬운 글을 찾아서 Theme까지 설치해보자. 

Hugo를 설치하면 아래와 같은 구조의 폴더가 생성된다. 기본 생성된 폴더들은 홈페이지를 만들기 위한 제각기 역할이 있다. 사용중인 Theme에 따라 폴더 구조나 포함된 파일들이 조금씩 다를 수 있지만 기본 구조는 모두 같다. 1부에서는 블로그를 만들면 생성되는 폴더와 파일들이 홈페이지 생성에 어떤 기능을 하는지 설명한다. 

<br>


![Untitled](docu_1/Untitled.png)

### archetypes

- default.md
    
    Markdown을 새로 만들 때 기본으로 포함되는 Front matter 변수를 설정하기 위해 사용된다. CMD에 hugo new Test/Test.md를 입력하면 `content\Test` 경로에 `Test.md`가 생성된다. `default.md`에 있는 기본 세팅값이 `test.md` 에 자동으로 포함된 것을 알 수 있다. 
    
    Dash( - )로 둘러 쌓인 내용을  `Front Matter`라 부른다. `Fornt Matter`는 Hugo 문법에서 다양하게 활용된다. 관련 내용은 2부에서 자세히 설명한다.
    
    ![Untitled](docu_1/Untitled%201.png)
    
    ![Untitled](docu_1/Untitled%202.png)
    

<br><br><br>

### content

markdown 양식의 게시글이 저장되는 공간이다. 게시글에 사용되는 사진 및 각종 파일들은 `content` 폴더에서는 불러올 수 없다. 대신 `static`폴더에 저장하여 불러와야한다.  

> Hugo에는 content 폴더에 사진과 markdown을 관리할 수 있는 `leaf bundle` 기능이 있다. 이 기능은 한정된 용도로 사용되고 부가적인 용도이므로 이 글에서는 다루지 않는다. 폴더 구조와 기본 문법을 이해하고 나면 `leaf bundle` 문서를 이해하는데는 어렵지 않으니 사용해보고 싶다면 [공식 문서](https://gohugo.io/content-management/page-bundles/#leaf-bundles)를 참고하자. 

<br>

content 폴더의 경로는 곧 URL 주소이다. content 폴더 내 test폴더에 위치한 `test.md`는  `웹주소\test\test` URL을 자동으로 가진다. 

{{< warning title="폴더 생성시 주의사항" content="폴더 경로는 다양한 용도로 활용되므로 폴더명을 소문자로 사용하고 띄어쓰기는 언더바( _ )로 하는 것을 권장한다." >}}


<br><br><br>

### data

`.yml`, `.yaml`, `.json`, `.xml`, `.toml` 확장자인 파일을 불러오기 위한 저장 공간이다. 이러한 확장자를 가진 파일을 딱히 사용할 일이 없다보니 해당 폴더도 거의 활용하되 않는다.  이런 용도로 활용된다는 사실만 이해하고 넘어가자.

<br><br><br>

### layouts

`layouts` 폴더는 블로그 뼈대가 되는 html 파일들이 저장되는 공간이다. Hugo 구조를 이해할 때 가장 중요한 공간이라 블로그를 만들면서 자주 들여다 보는 폴더이다. 

<br>


layouts 폴더를 이해하기 위해서는 Hugo가 페이지를 어떻게 구분하는지 부터 알아야한다. Hugo는 페이지를 `Home page`, `List page`, `Single page` 총 세 가지로 구분한다. `home page`는 페이지 접속시 바로 보이는 페이지를 의미하며 `List page`는 분류별로 게시글을 모아서 보여주는 페이지를, `Single page`는 게시글이 담긴 페이지를 의미한다. 

<br>


`Home page`를 수정하고 싶다면 Index.html를, `Single page`를 수정하고 싶다면 _default 폴더에 있는 Single.html을,  `List page`를 수정하고 싶다면 _default 폴더에 있는 list.html을 건드려야 한다.

<br>


본인이 설치한 theme 폴더 내 `layouts` 폴더에 들어가보자. 기본적으로 `_default` ,  `partials`,  `shortcodes` 폴더와 `index.html`,  `404.html` 파일이 보일 것이다. 사용하고 있는 Theme마다 구성이 다르지만 앞에 나열한 자료들은 기본으로 포함되어 있다. `_default` 폴더는 홈페이지 구조와 관련 있는 html 파일이 들어있다. 

<br>

`partial` 폴더는 페이지 구성을 위한 큰 부품을 저장하는 공간이라고 보면된다. partial에 포함된 html 파일들은 독립적으로 사용 불가능하고 `_default` 폴더에 있는 html 파일에서 불러와야만 사용 가능하다. `shortcodes`는 markdown에서 특수한 기능을 사용하기 위한 파일들이 저장된 공간이다. contents에 있는 경고 박스가 shortcode를 활용해 만든 것이다.

<br>


- Index.html
    
    파란색으로 네모 박스 쳐져있는 영역이 index_html을 수정하면 반영되는 공간이다. 앞에서 분명 `Home page`를 수정하기 위해서는 index.html를 건드려야 한다고 설명했는데 `Home page`에서 index.html이 차지하는 비중이 적어 의아할 것이다. 
    
    Hugo는 Baseof.html를 바탕으로 다른 html 파일을 불러온 뒤 이를 조합해 최종적으로 페이지를 구성한다. 쉽게 말해 Baseof.html은 일종의 메인보드 역할을 수행한다. 메인보드에 램이나 하드, cpu 등을 연결하듯 네모 박스쳐져있는 여러 html 파일들이 baseof.html에 포함되어 페이지가 만들어진다.

    ![Untitled](docu_1/Untitled%203.png)
    
    

<br>

- _default/list.html
    
     파란색 영역만 제외하고 index.html과 동일하다. 아직 게시글이 하나 밖에 없어서 얼핏 보면 `home page`와 같은 페이지처럼 보이지만 자세히 보면 타이틀이 다르다... 

     `list page`는 게시글을 보여주는 방식에 따라 `section`과 `taxonomy`로 세분화 된다. 대부분 블로그는 두 방법 모두 사용해 게시글을 분류한다. `Section`은 파일 경로대로 항목을 분류하는 방법이다. 하위 폴더에 있는 파일들은 모두 같은 주제로 분류 된다.
     
     `Taxonomy`는 게시글에 포함된 태그를 기반으로 분류하는 방법이다. 인스타그램 # 태그처럼 게시글에 원하는 키워드 포함시키면 같은 태그를 가진 게시글을 한번에 모아 볼수 있다. 
  
    
    ![Untitled](docu_1/Untitled%204.png)
    

<br>

- _default/single.html
    
    `single page`도 파란색 영역을 제외하고는 이전 페이지와 크게 달라진게 없다. 게시글은 모두 Single page로 간주된다. Single page를 수정하기 위해서는 `Single.html`을 건드리자.
    
    ![Untitled](docu_1/Untitled%205.png)
    
    <br>
    
- _default/baseof.html
    
    앞에서 설명하였듯 baseof.html은 메인보드 역할을 한다. 아래 코드는 현재 블로그의 baseof.html이다. 여러 html들을 이곳에 불러온 다음 하나의 html로 완성된다. `home page`, `list page`, `single page` 모두 예외없이 baseof를 거쳐 page가 완성된다.
    
    <br>

    > 하얀색으로 블럭쳐져있는 영역을 보자.  이 공간에 index.html, list.html, single.html를 불러온다. 
    
    ![Untitled](docu_1/Untitled%206.png)
    

<br>

- partials/
    
    Partials 내 저장된 html 파일은 특정 기능을 수행하는 부품이다. baseof에서 partial 폴더 내 파일을 불러오면 해당 기능을 사용할 수 있다. partial의 장점은 누군가 사용하고 있는 기능을 쉽게 가져와 사용 할 수 있다는 점이다. 
    
    예로들어 좌측 상단 메뉴버튼을 누르면 나오는 메뉴바는(PC 버전인 경우 왼편에 있는 화살표`>`)  만들어 놓은 기능을 그대로 가지고와 내 입맛에 맞춰 약간 수정하여 만들어졌다. 
    
    이 기능을 쓰고싶다면 내 Github에 있는 offcanvas_menu.html 파일을 다운받아 partial 폴더에 넣은 뒤, baseof.html에서 `{{ partial ‘offcanvas_menu.html’ .}}` 명령어로 불러오면 바로 사용할 수 있다. 단 bootstrap을 바탕으로 동작하므로 관련 파일이 기본으로 설치되어있어야한다.  이와 같은 방법으로 다른 Hugo 테마의 마음에 드는 기능을 내 블로그에 이식할 수도 있다. 
    

<br><br><br>

### Static

홈페이지 제작에 필요한 각종 이미지,사운드, css, js 등이 저장되는 공간이다. Static 공간에 있는 파일들은 **모두** URL주소`https://{server-url}/image.jpg` 로 변환된다. 
  <br>

> 아래 그림처럼 static 폴더에 있는 hugo1.jpg는 자동으로 url주소를 갖는다.

![Untitled](docu_1/Untitled%207.png)

<br><br><br>

### Themes

이 글을 읽는 분들이라면 Theme 설치까지는 완료 했으리라 생각한다. Theme을 설치했음에도 여전히 하얀화면이거나 Theme 사이트에서 본 것과 같이 화면이 뜨지 않는다면 아래 내용을 읽고 해결해보자.

> Theme 폴더 내에서 직접적으로 파일을 수정하지 말자. 수정이 필요한 자료가 있다면 복사해 블로그 설치 폴더에 붙여넣은 뒤 수정하자. 이렇게하는 이유는 원본 데이터를 보존하기 위함이기도하고 Theme 제작자를 존중하는 의미라고 한다. 

<br>

**Theme 사이트에서 본 예시 화면 띄어보기.**

theme 폴더에는 데모버전을 운영할 수 있는 자료들이 있다. 해당 자료들을 활용하면 사이트에서 봤던 화면을 똑같이 띄울 수 있다. 자료들은 설치한 theme 내 `exampleSite`폴더에 위치해있다. 폴더 안에 있는 자료를 모두를 복사해 블로그가 설치된 폴더에 붙여넣기 하자. 중복된다고 아무 일도 일어나지 않으니 `대상 폴더의 파일 덮어쓰기(R)`를 누르자.  

![Untitled](docu_1/Untitled%208.png)

<br>

**로컬 서버 실행 시 에러 발생**

`Examplesite`를 붙여넣은 뒤 로컬 서버가 작동하지 않는다면 원인은 둘 중 하나다. 

- module does not exist.
    
    이런 에러 코드가 발생하면  `Config` 내 Theme 이름과 Theme의 폴더 이름이 매칭되는지 확인해보자.
    대소문자, 띄어쓰기도 구분하니 똑같은 제목이 들어가도록 신경쓰자.
    
    ```bash
    Error: module "hugo-primer-master" not found; either add it as a Hugo Module or store 
    it in "D:\\git_local_repository\\new_blog\\themes".: module does not exist
    ```
    ![Untitled](docu_1/Untitled%209.png)
    
    <br>
    
- SCSS/SASS 에러
    
    일부 Theme은 CSS대신 SCSS 또는 SASS를 사용한다. 2부 문법을 설명할 때 설치한 apollo Theme도 이런 오류를 발생시킨다.
    
    이 문제를 해결하기 위해서는 두 가지 방법이 있다. 우리는 데모버전을 실행시키는게 목적이므로 대부분 첫번째 방법으로 해결된다. Apollo Theme에서 발생하는 오류도 첫번째 방법으로 해결된다. 
    
    다른 Theme을 사용중이라면 첫번째 방법으로 해결되지 않을 수 있다. 첫번째 방법을 적용했음에도 **같은 내용의 오류**가 발생한다면 2번 방법인 hugo extension 버전을 설치해야한다.
    
    ```bash
    Error: Error building site: TOCSS: failed to transform "style.scss" (text/x-scss). 
    Check your Hugo installation; you need the extended version to build SCSS/SASS.: 
    this feature is not available in your current Hugo version,
    see https://goo.gl/YMrWcn for more information
    ```
    
    1번 방법 : 블로그 폴더에 있는 config 파일에 아래 명령어 추가하기. theme 폴더 config와 착각하지 말자.
        
    ```markdown
    config.toml 일 경우
    relativeURLs = true
    canonifyURLs = true
    
    config.yaml일 경우
    relativeURLs: true
    canonifyURLs: true
    ```
        
    2번 방법 : 그럼에도 여전히 같은 오류가 발생한다면 Hugo Extension을 설치하자. 일반버전에는 SCSS를 변환하는 기능이 없기 때문에 이런 오류가 발생한다고 한다. | [다운로드 링크](https://github.com/gohugoio/hugo/releases)
        
    ![Untitled](docu_1/Untitled%2010.png)

<br>

- md 파일 오류  
  데모 버전을 테스트하기 위해서는 거의 발생하지 않는 오류이긴 한데, 업데이트가 오랫동안 되지 않은 Theme을 쓰다보면 간혹 이런 문제가 발생한다. [primer css template](https://github.com/qqhann/hugo-primer)가 그 예시다. 

  에러 내용을 읽어보면`rich-content.md`가 문제라는 것을 알 수 있다. 아래와 같은 문제가 발생한다면 해당 파일을 지우고 다시 실행하면 정상적으로 작동된다.

  ```bash
  ignoreErrors = ["error-missing-instagram-accesstoken"]

  WARN 2022/02/27 00:11:09 The "twitter_simple" shortcode will soon require two named parameters: 
  
  user and id. See "D:\git_local_repository\new_blog\content\blog\rich-content.md:35:1"

  Error: Error building site: logged 1 error(s)
  ```

<br><br><br>

### Assets

블로그 설치시 기본으로 포함된 폴더는 아니지만 다운받아 사용중인 테마에 종종 보인다. 역할은 `static` 폴더와 동일하다. 하지만 `static` 폴더는 모든 자료들이 자동으로 업로드 되고 각자의 URL주소도 가지고 있지만 `assets`폴더 내 파일은 `{{resources.Get }`} 명령어를 사용해야만 불러올 수 있다. 다운받은 theme에 `assets` 폴더가 있다면 그 안에 SCSS파일이 들어있을 것이다. SCSS 또는 SASS 파일을 CSS로 변환하기 위해서는 `assets` 폴더를 사용해야 하기 때문이다. 

굳이 `assets`폴더없이도 Static으로 충분히 블로그를 제작할 수 있으니 사실상 사용할 일이 없을 것이다. `assets`  기능에 대해 자세히 알고싶다면 [이곳](https://www.regisphilibert.com/blog/2018/07/hugo-pipes-and-asset-processing-pipeline/)을 참고하자.

<br><br><br>

### Config.toml(or yaml)

Config는 Hugo에서 기본으로 제공하는 기능을 On/Off하거나 사용자 변수를 설정하기 위한 용도로 사용된다. config 자체에 기능이 있다기 보다는 필요한 변수를 적어놓는 일종의 메모장이라고 이해하면 편하다. Config 내 변수는 `{{ .Site ~~~ }}`문법으로 어디든 불러올 수 있다.

Hugo가 제공하는 기본 Template(Google Analytics, pagination 등)들도 config로 통제된다. 
> 기본 Template에는 무엇이 있는지는 <a href="https://gohugo.io/templates/internal/#readout" target="_blank">공식 문서</a> 에서 확인할 수 있다.


config를 어떻게 사용하는지 이해해보자. 아래 그림은 disqus.html이 config를 사용하는 방법을 보여준다. disqus가 무엇인지, 어떻게 구동되는지는 신경쓰지 않아도 된다. 

작동 원리는 간단하다. Html 파일에서 `{{.Site. 변수명(DisqusShortname) }}` 명령어를 작성하면 config 내 변수(name)를 불러온다. 이처럼 html을 직접 건드리지 않아도 config를 통해 아이디를 간단하게 변경 할 수 있다.  이런 방식으로 config 사용하니 블로그 제작 시 config를 종종 활용해보자.

![Untitled](docu_1/Untitled%2011.png)

<br><br><br><br>



&nbsp; &nbsp; **[2부 Hugo 문법정리](hugo/documentation/documentation_2/)**