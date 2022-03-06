---
title: "2부 Hugo Docs 활용을 위한 문법 정리"
date: 2022-03-04
image: "images/home/hugo1.jpg"
image_webp: "images/home/hugo.webp"
Tags: ['Hugo Documentation','Do It Yourself','공식 문서 활용하기','Hugo 문법']     
draft: false
Description: '휴고 공식 문서(Hugo Documentation)를 활용하기 위해 필요한 문법과 용어를 설명한다. Hugo 문법은 HTML과 Hugo에 익숙하지 않는 사용자라면 어느 구문이 오류인지도 모를정도로 이해하기 어렵다. 그렇다고 공식 문서를 보더라도 이해가 쉽게 되지는 않는다. 이 글은 Hugo에 익숙하지 않는 사용자가 공식 문서를 읽기 위해 필요한 수준의 지식을 갖추도록 돕기 위해 작성했다. '
Summary: '휴고 공식 문서를 활용하기 위해 필요한 문법과 용어를 설명한다. Hugo 문법은 HTML과 Hugo에 익숙하지 않는 사용자라면 어느 구문이 오류인지도 모를정도로 이해하기 어렵다.'
---
<br>

**HTML과 CSS**

<!-- 본인이 현재 HTML과 CSS를 전혀 모르는 상태라면 행운이 찾아왔다고 생각하자. Hugo는 HTML과 CSS를 배울 수 있는 좋은 기회이기 때문이다. 나도 Hugo로 블로그를 만들면서 처음 HTML과 CSS를 알게 됐다. 나만의 블로그를 만들면서 정말 많은 연습이 됐다. -->

Hugo는 사용자가 HTML을 쉽게 사용할 수 있도록 돕는 도구이다. Hugo로 블로그를 만들기 위해서는 HTML에 대해 기본적인 이해가 필요하다. 반면 Hugo와 CSS는 관련이 없다. 이해할 필요 없다는 말은 아니고 CSS를 위한 Hugo 문법이 존재하지 않는다는 말이다. 하지만 블로그를 꾸미기 위해서는 CSS가 필수이므로 당연히 알아야한다. 다행이 Hugo와 같이 사용자가 CSS를 쓰기 쉽게 돕는 도구가 있다. Bootstrap, Primer가 대표적이다.



2부에서는 Hugo 문법에 대해 설명한다. Hugo를 처음 사용하거나 폴더 별 기능을 모른다면 1부를 먼저 읽은 뒤 이 글을 읽자.  

<br>

**[1부 폴더구조](/hugo/documentation/documentation)**

<br><br>

## 연습환경 구축하기
Hugo를 처음 설치하고 나면 어디서부터 해야할지 막막하다. 특히 어디서 문법을 테스트 해야할지부터 의문이다. 그렇다고 무작정 파일을 하나씩 열어본다 한들 답이 없다.  알 수 없는 용어에 사용된 언어도 직관적이지 않아 모르고 보면 무슨 말인지 감도 안잡힌다. 뜯어보면서 배우겠다고 코드 한 줄 지웠을 뿐인데 주황색 배경에 빨간 글씨로 오류가 뜬다. 어디가 어떻게 오류인지 모르니까 무엇을 수정해야할지도 모른다. 어디서부터 시작해야할지 정말 막막하다. 

Hugo가 익숙하지 않은 사람이라면 연습용으로 사용중인 Theme을 설치한 뒤 이 글에 있는 코드를 활용해 문법을 알아가는 것이 가장 좋은 선택이라 생각한다. 작업 환경이 같으니 원인 모를 에러가 발생할 가능성도 낮고 에러가 나더라도 어디서 문제가 발생했는지 대략 알 수 있기 때문이다. 

 연습용으로 사용하고 있는 Theme은 [Apollo Hugo](https://github.com/gethugothemes/apollo-hugo)이다. 지금 이 글을 보고 있다면 Theme 정도는 설치할 수준은 된다고 본다. Apollo theme을 설치했다면 `examplesite`를 로컬 서버에 불러오자. `examplesite`를 불러오는 방법을 모르거나 서버 실행 시 에러가 발생할 경우 [이 글을 읽고](/hugo/documentation/documentation/#themes) 해결하자.

<br>

### 연습장 만들기

- **Laoyouts 폴더 복사하기**
    
    apollo-hugo에 있는 layouts 폴더를 블로그 설치 폴더(new_blog)로 붙여넣자. 
    ![Untitled](hugo/documentation/docu_2/Untitled%2028.png)
    
<br>
 
- **Index.html 정리하기**
    
   모든 코드는 index.html에서 실행했다. layouts 폴더에 있는 index.html에 들어가 `{{ define "title" }} {{ end }}`를 제외하고 모두 지우자. 코드 수정은 `vscode`에서 이뤄졌다. `vscode`를 사용하지 않는다면 이번 기회에 사용해보자. 
   ![Untitled](hugo/documentation/docu_2/Untitled%201.png)

    <br>

   {{< warning title="Warning" content=" 게시글에 있는 코드를 list.html이나 single.html에서 실행한다면 오류가 발생할 수도 있다. 익숙하지 않은 사용자라면 index.html에서 예시 코드를 실행시킬 것을 권장한다. " >}}

<br>

- **Content 폴더 구조**
  
  연습용 블로그에는 총 12개 md 파일이 있다. 5개는 Content 폴더에, 7개는 Content/post 폴더에 있다. Hugo에서는 경로가 곧 URL 주소가 되니 content 폴더 구조를 꼭 확인하고 넘어가자
    
    ```html
    Content 
    |   about.md   
    |   contact.md
    |   elements.md
    |   FolderList.txt
    |   terms-conditions.md
    |
    ---post
            post-1.md
            post-2.md
            post-3.md
            post-4.md
            post-5.md
            post-6.md
            post-7.md
            post-8.md
            _index.md
    ```

<br>

- **변경사항 실시간으로 확인하기**
  
    코드 변경사항을 편리하게 보기 위한 팁이다. `윈도우키` + `방향키`를 누르면 아래 그림과 같이 화면을 구분해서 사용할 수 있다. 예시 코드를 붙여넣은 뒤 코드를 수정해가면서 구조를 이해하자.
    
    ![Untitled](hugo/documentation/docu_2/Untitled%2022.png)

<br><br>

## Hugo 기본문법 

공식 문서를 이해하고 활용할 수 있도록 기본적인 문법을 정리했다.  관련 내용을 다룬 공식문서를 제목에 링크 걸어놨으니 더 많은 내용을 알고 싶다면 공식 문서를 읽어보자.

<br>

### 변수 설정 및 불러오기 


- **[사용자 변수 설정하기](**https://gohugo.io/about/**) | `Custom Variable`**
    
    사용자 변수는 `{{ $var := “text” }}` 로 정의한 후 `{{ $var }}`로 불러온다.
    
    ```html
    {{ define "main" }}
    <div style="text-align: center;">
        <div  style="margin: 200px auto; font-size: 1.5em;">
        <!--String 변수 설정-->
        {{ $drink := "a coffee" }}
        Your drink is {{ $drink }}
        <br><br>
    
        <!--함수 또는 Hugo 기본 변수를 활용하여 변수를 설정할 수 있다.-->
        {{ $title := .Title }}
        your title is {{ $title }}
        </div>
    </div>
    {{ end }}
    ```
    
    ![Untitled](hugo/documentation/docu_2/Untitled%202.png)

<br>

- **[함수 및 기본 변수 불러오기](https://gohugo.io/templates/introduction/#access-a-predefined-variable) | `Predefined Variables`** 
    
    `{{ .명령어 }}`로 함수 및 기본 변수를 불러온다.
    
    ```html
    {{ define "main" }}
    <div style="text-align: center;">
        <div  style="margin: 200px auto; font-size: 1.5em;">
        {{ .Title }}
        </div>
    </div>
    {{ end }}
    ```
    
    ![Untitled](hugo/documentation/docu_2/Untitled%203.png)
    

<br>


### 조건절

조건절은 `{{ 조건절 }} 내용 {{ end }}` 으로 사용한다.

- **[If 조건절](https://gohugo.io/templates/introduction/#example-3-if) | `Conditional`**
    - .IsPage | .IsSection | .IsNode | .IsHome
        
        Hugo는 페이지를 `Home`, `Page`, `Section`, `Taxonomy`, `Term` 으로 구분한다. 관련 내용은 1부 layouts과 2부 Section 및 Taxonomy 항목을 참고바란다. | [1부 layouts 항목](http://localhost:1313/hugo/documentation/documentation/#layouts) 
        
        > `{{ .Kind }}` 변수를 활용하면 페이지 종류를 확인할 수 있다.
        
        <br>

        `.IsPage` | `.IsSection` | `.IsNode` | `.IsHome`은 페이지 종류에 따라 Boolean(True or False)를 반환한다. 주로 `Baseof.html`에서 페이지 종류별로 원하는 기능을 실행 또는 중지하기 위해 사용한다.

        ```html
        {{ define "main" }}
        <div style="text-align: center;">
            <div  style="margin: 200px auto; font-size: 1.5em;">
            <!-- {{ .Kind }} 함수를 사용하면 현재 페이지가 어떤 종류인지 알 수 있다.  -->
            현재 페이지 종류 : {{ .Kind }}
            <br><br>
            
            <!--Home page인 경우 True 반환-->
            {{ if .IsHome }}
            This Page is home page
            <br><br>
            {{ end }}
        
            <!--single page가 아닌 경우 True 반환-->
            {{ if .IsNode }}
            This Page is not a single page
            <br><br>
            {{ end }}
        
            <!--single page인 경우 True 반환-->
            {{ if .IsPage }}
            This Page is a single page
            <br><br>
            {{ end }}
        
            <!--section page인 경우 True 반환-->
            {{ if .IsSection }}
            This Page is a Section page
            {{ end }}
        </div>
        </div>
        {{ end }}
        ```
        
        ![Untitled](hugo/documentation/docu_2/Untitled%204.png)
        
        <br>

    - and / or
        
        and와 or을 사용하는 방법에는 두 가지가 있다.
        
        ```html
        {{ define "main" }}
        <div style="text-align: center;">
            <div  style="margin: 200px auto; font-size: 1.5em;">
                <!-- {{ .Kind }} 함수를 사용하면 현재 페이지가 어떤 종류인지 알 수 있다.  -->
                현재 페이지 종류 : {{ .Kind }}
                <br><br>
            
            1번 방법 :
            {{ if .IsPage | or .IsHome }}
                Hello_1
                <br><br>
            {{ end }}
        
            2번 방법 :
            {{ if or (.IsPage) (.IsHome) }}
                Hello_2
                <br><br>
            {{ end }}
        </div>
        {{ end }}
        ```
        
        ![Untitled](hugo/documentation/docu_2/Untitled%205.png)
        
    - 비교 연산자
        
        `{{ if eq arg 1 arg 2 }} 내용 {{ end }}`으로 비교 연산자를 사용한다.
        
        | 명령어 | 의미 | 명령어 | 의미 |
        | --- | --- | --- | --- |
        | eq | arg1 == arg2 | le | arg1 <= arg2 |
        | ge | arg1 >= arg2 | lt | arg1 < arg2 |
        | gt | arg1 > arg2 | ne | arg1 != arg2 |
        
        ```html
        {{ define "main" }}
        <div style="text-align: center;">
            <div  style="margin: 200px auto; font-size: 1.5em;">
            <!-- 변수 설정-->
            {{ $drink := "coffee" }}
            
            {{ if eq "coffee" $drink }}
                커피 마시는 중
            {{ end }}
        
            {{ if eq "tea" $drink }}
        		차 마시는 중
            {{ end }}
            
            </div>
        </div>
        {{ end }}
        ```
        
        ![Untitled](hugo/documentation/docu_2/Untitled%206.png)

<br>

- **[with 조건절](https://gohugo.io/templates/introduction/#example-1-with) | `Conditional`**
  
    조건에 만족하는 대상이 있다면 그 대상을 전부 불러온다. if와 range를 함께 쓴다고 생각하면 이해하기 쉽다. 원하는 페이지나 원하는 Parameter를 불러올 때 주로 활용한다.

    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <h1>결과</h1>
        <br>
        {{range .Pages}}
        {{range .Pages}}
        <!--Single Page 모든 title 불러오기-->
        {{with .Params.title}}
        {{.}}
        <br>
        {{end}}{{end}}{{end}}

    </div>
    {{ end }}
    ```
    ![Untitled](hugo/documentation/docu_2/Untitled%2029.png)


<br>

### Page 불러오기

- **하위 페이지 불러오기**
  
  `{{ range .Pages }} {{ . }} {{ end }}` 명령어를 사용하면 현재 페이지 기준, 바로 아래 계층에 속하는 페이지를 불러온다. 말단 페이지까지 불러오려면 폴더 계층에 따라 `{{.range .Pages}}`명령어를 추가해야한다. 지금 블로그의 최대 경로가 `content/post/post-1.md`이기 때문에 2단계에서 끝났지만 만약 `content/post/sub/post-1.md`라면 3단계 결과도 나온다.

  > 설명이 이해되지 않는다면 폴더 경로를 여러 계층으로 만들어서 테스트해보자. 
  > 
  > ex) `content/post/subpost/subpost-1/post1.md`

  <br>

  ```html
        {{ define "main" }}
        <div style="text-align: center; height: 1000px;">
            <div  style="margin: 200px auto; font-size: 1.1em;">
            <br>
            {{ range .Pages }}
            <br>
            1단계 --- 경로 : {{ .RelPermalink }} &nbsp; &nbsp;<br> 
            {{ range .Pages }}
            2단계 --- 경로 : {{ .RelPermalink }} &nbsp; &nbsp;<br>
            {{ range .Pages }}
            3단계 --- 경로 : {{ .RelPermalink }}
            {{ end }}{{ end }}{{ end }}
        </div>
        {{ end }}
  ```
  ![Untitled](hugo/documentation/docu_2/Untitled%2021.png)

- **페이지 한번에 불러오기**
    
    앞에서 설명한 `{{ .Pages }}`는 현재 페이지의 하위 항목만을 불러왔다. 지금 설명하는 명령어들은 페이지 전체를 불러온다.

     `{{ .Site.RegularPages }}`는 전체 페이지 중 Single page만 불러온다. content 폴더에 있는 markdown 파일 중 _index.md만 제외하고 모두 불러오는 것과 같다.

     `{{ .Site.Pages }}`는 블로그가 가지고 있는 모든 페이지를 불러온다. 


     `{{ with .Getpage arg1 arg2 }}{{ . }}{{ end }}`는 조건에 맞는 페이지만 불러온다. | [with .Getpage 사용법 더보기](https://gohugo.io/functions/getpage/)
    
        
    ```html
        {{ define "main" }}
        <div style="text-align: center; height: 1000px;">
            <div  style="margin: 200px auto; font-size: 1.1em;">
            <h1>결과</h1>
        
            <br>
            <!-- 왼편-->
            <div style="margin: 0 100px;">
                <div style =" float:left; ">
                    <!--_index.md 제외한 모든 markdown 파일 불러오기-->
                    <h3>.Site.RegularPages</h3>
                    <br><br>
                    {{ .Site.RegularPages }}
                </div>
        
                <!-- 가운데-->
                <div style ="float:left; margin: 0 20px;">
                    <!--모든 페이지 불러오기-->
                    <h3>.Pages</h3>
                    <br><br>
                    {{ .Site.Pages }}
                </div>
        
                <!-- 오른쪽-->
                <div style ="float:left; margin: 0 20px;">
                    <h3>with .Site.GetPage</h3>
                    <br><br>
                    <!-- 원하는 페이지 불러오기-->
                    <!--with .Getpage arg 1 arg 2-->
                    {{ with .Site.GetPage "section" "post" }}
                    {{ . }}
                    {{ end }}
                </div>
            </div>
        </div>
        {{ end }}
    ```
        
    ![Untitled](hugo/documentation/docu_2/Untitled%207.png)
    
    <br>

  - Page 불러오기
  
    위에서 사용된 명령어처럼 결과값으로 Pages()을 반환하는 경우 `{{ range .Pages }}{{ . }}{{ end }}` 명령어를 활용해 개별 페이지를 불러올 수 있다.

    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <h1>결과</h1>
    
        <br>
        <!-- 왼편-->
        <div style="margin: 0 auto;">
            <div style =" float:left; ">
                <!--_index.md 제외한 모든 markdown 파일 불러오기-->
                <h3>.Site.RegularPages</h3>
                <br><br>
                {{ range .Site.RegularPages }}
                {{ .File }} <!-- 파일경로-->
                <a href="{{ .Permalink }}">site</a> <!-- 페이지 주소-->
                <br>
                {{ end }}
            </div>
    
            <!-- 가운데-->
            <div style ="float:left">
                <!--모든 페이지 불러오기-->
                <h3>.Pages</h3>
                <br><br>
                {{ range .Site.Pages }}
                {{ .File }} <!-- 파일경로-->
                <a href="{{ .Permalink }}">site</a> <!-- 페이지 주소-->
                <br>
                {{ end }}
            </div>
    
            <!-- 오른쪽-->
            <div style ="float:left">
                <h3>with .Site.GetPage</h3>
                <br><br>
                <!-- Section이 post인 페이지 전부 불러오기>
                {{ with .Site.GetPage "section" "post" }}
                {{ . }}
                <br>
                <!-- 개별 post Page 불러오기 -->
                {{ range .Pages }} 
                {{ .File }} <!-- 파일경로-->
                <a href="{{ .Permalink }}">site</a> <!-- 페이지 주소-->
                <br>        
                {{ end }}
                {{ end }}
            </div>
        </div>
    
    </div>
    {{ end }}
    ```
        
    ![Untitled](hugo/documentation/docu_2/Untitled%208.png)
    
    <br>
    
  - First와 Last
  
      모든 Page를 불러올 필요는 없다. range 함수에 First 또는 Last 명령어를 사용하면 원하는 Page 범위를 정할 수 있다. first n 처음부터 n번째까지 내용을 불러온다. last n 마지막에서 시작해 n번째까지 내용을 불러온다.
        
    ```html
        {{ define "main" }}
        <div style="text-align: center; height: 1000px;">
            <div  style="margin: 200px auto; font-size: 1.1em;">
            <div>
                <!--모든 페이지 불러오기-->
                <h3>.Pages</h3>
                <br>
                {{ range first 3 .Site.Pages }}
                {{ .File }} <!-- 파일경로-->
                <a href="{{ .Permalink }}">site</a> <!-- 페이지 주소-->
                <br>
                {{ end }}
            </div>


        </div>
        {{ end }}
    ```
    
    ![Untitled](hugo/documentation/docu_2/Untitled%2024.png)
        

<br>

### Hugo 기본 변수

- **[Site 변수](https://gohugo.io/variables/site/) | `Site Variables`**
    
    Site 변수는 `Config`에 저장한 변수를 불러오거나 전역 변수를 불러올 때 사용한다. 자주 사용되는 변수만 예시로 작성했으니 다른 변수는 공식문서에서 확인하자.
    
    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <!-- Local Server일 경우 True 아닐 경우 False 반환-->
        <h4>.Site.IsServer</h4>
        {{ .Site.IsServer }}
        <br><br>

        <!-- 블로그에 있는 모든 Taxonomy 불러오기 -->
        <h4>.Site.Taxonomies</h4>
        {{ .Site.Taxonomies }}
        <br><br>

        <!-- 블로그에 있는 모든 Page 불러오기 -->
        <h4>.Site.Pages</h4>{{ .Site.Pages }}
        <br><br>

        <!-- 블로그에 있는 모든 single Page 불러오기 -->
        <h4>.Site.RegularPages</h4>
        {{ .Site.RegularPages }}
        <br><br>

        <!--Config 내 Paramter 불러오기-->
        <h4>.Site.Params.logo</h4>
        {{ .Site.Params.logo }}
        <br><br>

        <h4>.Site.Params.favicon</h4>
        {{ .Site.Params.favicon }}
        <br><br>

        <h4>.Site.Params.variables.primary_color</h4>
        {{ .Site.Params.variables.primary_color }}
        <br><br>
      
    </div>
    {{ end }}
    ```
    
    ![Untitled](hugo/documentation/docu_2/Untitled%2010.png)

<br>

- **[Page 변수](https://gohugo.io/variables/page/) | `Page Variables`**
    
    Page 변수는 페이지가 Markdown 파일에 기반한 경우에만 사용 가능하다. 그러므로 Single page 또는 _index.md 파일이 있는 list page에서 사용 가능하다. 물론 Home page에서 `{{ range .Pages }}`로 single page를 불러와서도 사용 할 수 있다. 
    
    Page 변수 중 많은 변수들이 Front matter와 연동해 사용된다. Front matter와 연동된 page 변수를 알고 싶으면 공식문서를 참고하자.
    
    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
    
            <!-- 하나의 페이지만 불러오는 코드-->
            {{ range first 1 .Site.RegularPages }}
    
            <!--Markdown 본문 가져오기-->
            <h4>.Content </h4>
            페이지 본문
            <br><br>
    
            <!-- Type 또는 Section 이름 불러오기-->
            <h4>.Type</h4>
            {{ .Type }}
            <br><br>        
    
            <!--상대주소-->
            <h4>.RelPermalink</h4>
            {{ .RelPermalink }}
            <br><br>
    
            <!--절대주소-->
            <h4>.Permalink</h4>
            {{ .Permalink }}
            <br><br>
    
            <!--본문 단어 개수-->
            <h4>.WordCount</h4>
            {{ .WordCount }}
            <br><br>
    
            <!--Front matter에 있는 title 불러오기-->
            <h4>.Title</h4>
            {{ .Title }}
            <br><br>
    
            <!--Front matter에 있는 date 불러오기-->
            <h4>.Date</h4>
            {{ .Date }}
            <br><br>
    
            <!--Front matter에 있는 description 불러오기-->
            <h4>.Description </h4>
            {{ .Description }}
            <br><br>
    
            <!--Page 종류 확인(home,page,section,taxonomy,term)-->
            <h4>.Kind</h4>
            {{ .Kind }}
            <br><br>
    
            <!--읽는 시간 예상-->
            <h4>.ReadingTime</h4>
            {{ .ReadingTime }}
            <br><br>
    
            <!--첫 문단 요약-->
            <h4>.Summary</h4>
            첫문단 요약
            <br><br>
            {{ end }}
    </div>
    {{ end }}
    ```
    
    ![Untitled](hugo/documentation/docu_2/Untitled%2011.png)

    
    <br>
    

- **[File 변수](https://gohugo.io/variables/files/) | `File Variables`**
  
    content 폴더와 static 폴더는 경로가 곧 URL주소이다. File 변수는 원하는 URL 주소를 불러오기 위해 주로 사용된다. 

    URL 변환 시 자주 사용되는 함수로는 print와 replace 함수가 있다. 자주 사용되는 File 변수를 알아본 후 함께 사용되는 함수를 알아보자.

    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
    
            {{ range first 1 .Site.RegularPages }}
            <!--Content Folder 이후 경로 및 파일-->
            <h4>.File.Path</h4>
            {{ .File.Path }}
            <br><br>      
    
            <!-- 파일경로 -->
            <h4>.File.Dir</h4>
            {{ .File.Dir }}
            <br><br>        
    
            <!--파일명 (확장자 포함)-->
            <h4>.File.LogicalName</h4>
            {{ .File.LogicalName }}
            <br><br>        
    
            <!-- 파일명(확장자 미포함)-->
            <h4>.File.BaseFileName</h4>
            {{ .File.BaseFileName }}
            <br><br> 
            {{ end }}
    
    </div>
    {{ end }}
    ```

    ![Untitled](hugo/documentation/docu_2/Untitled%2012.png)
    

    - File 변수와 함께 자주 사용되는 함수(print, replace)

        Hugo에서는 단어를 이어붙이는 방법이 까다롭다. 이때 print 함수를 활용하면 단어들을 쉽게 이어붙일 수 있다.
        
        Windows에서 File variables를 사용하면 경로가 Back-slash( \ )로 표현된다. replace는 Back-slash( \ )를 Slash( / )로 변환하기 위해 자주 사용된다.

        ```html
            {{  define "main" }} 
            <div style="text-align: center; height: 1000px;">
                <div  style="margin: 200px auto; font-size: 1.1em;">
                <h1>결과</h1>

                
                <!-- Print 함수 이후 변수를 선언하는 절차이므로 총 2번의 과정을 거친다. 
                먼저 실행 되는 함수에 괄호를 쳐야한다..  -->
                <!-- print 함수 사용법 : print 문장1 문장2 문장3 문장4... -->
                {{  $sentence := (print "단어를 " "이렇게 " "조합해도 " "됩니다." ) }}
                {{  $sentence }}

                {{ range .Pages }}
                <br>
                {{ range first 3 .Pages }}
                {{ $site := ( print "/drink/Ice Americano/" .File ) }}
                <br>
                변경 전 : {{ $site }}
                <br>
                <!-- 두 번 연속으로 바꾸고 싶다면 아래 예시처럼 괄호를 추가해서 사용하자 -->
                <!-- Back-slash를 다른 단어로 바꾸고 싶다면 "//"로 써야한다. -->
                <!-- replace 함수 사용법 : replace 바꾸고 싶은 문장 "바뀔 단어" "바꿀 단어" -->
                변경 후 : {{ replace ( replace $site "Ice Americano" "Ice Latte" ) "\\" "/" }}<br>
                {{ end }}
                {{ end }}
                
            </div>
            {{ end }}
        ```
        ![Untitled](hugo/documentation/docu_2/Untitled%2023.png)

<br>


### 자료 불러오기
Hugo에서 자료를 저장하는 공간은 assets 폴더와 static 폴더다. 두 폴더 모두 자료를 저장한다는 공통점이 있지만 assets 폴더는 hugo-pipe라는 기능을 위해 사용된다. 따라서 Hugo-pipe 기능을 필요로 하지 않는 이상 assets 폴더를 활용하지 않는다. [1부 assets 설명 바로가기](http://localhost:1313/hugo/documentation/documentation/#assets)
  
  - **HTML에서 이미지 불러오기**
   
    이미지 경로 기본 위치는 static 폴더이다. 그러므로 static 이후 경로만 적어도 이미지를 불러올 수 있다.

    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <h1>결과</h1>
        <br>
            <div style="width: 200px ; height : 200px; margin: 0 auto;">
                <img src="images/blog/blog-1.jpg">
            </div>
        </div>
    </div>
    {{ end }}
    ``` 
    <br>

  - **게시글에서 이미지 불러오기**
   
    게시글에서 이미지를 불러오려면 markdown 문법을 따라야한다. `![제목](폴더 경로)`를 사용하면 해당 경로에 맞는 이미지를 불러온다. 

    <br>
    
  - **HTML에서 CSS, Javascript 불러오기**

    누군가가 만든 기능을 똑같이 활용하기 위해서는 CSS와 Javascript도 함께 불러와야한다. 다운 받은 CSS와 JS파일은 static 폴더에 저장한 뒤 html 명령어로 불러오면 된다.
    보통 CSS와 JS는 Head 또는 Footer에서 불러온다. partial 폴더에 들어가 Head.html과 Footer.html 중 아래와 비슷한 코드가 모여있는 파일을 찾고 아래 코드를 통해 파일들을 붙여넣자. 예시 코드의 경우 static 폴더 내 css와 JS폴더를 만들어 다운받은 자료를 넣었다. 만약 경로가 다르다면 CSS와 JS가 저장된 디렉토리로 수정하자.

    ```html
    <!--CSS 불러오기 | css/bootstrap.css를 CSS가 저장된 주소로 바꾸자.-->
      <link rel="stylesheet" href="{{ `css/bootstrap.css` | relURL }}">   
         
    <!--JS 불러오기 | /js/medium-zoom.js를 js가 저장된 주소로 바꾸자.-->
      <script defer language="javascript" type="text/javascript"  src="{{ "/js/medium-zoom.js" | urlize | relURL }}"></script>
    ```

    <br>

    {{< warning title="assets 폴더에서 자료 불러오기" content=" Hugo 공식 문서에서는 종종 assets 폴더를 활용해 자료를 불러오는 방법을 소개한다. assets 폴더는 Hugo-pipe 기능을 사용할 때 활용되는 공간이다. Hugo-pipe는 minify, fingerprint, sass를 사용할 수 있는 기능인데 필수적인 기능은 아니다. Hugo-pipe에 대해 더 알고 싶다면 [관련 설명글](https://www.regisphilibert.com/blog/2018/07/hugo-pipes-and-asset-processing-pipeline/)을 읽어보자. " >}}


<br>


### Front matter

Front matter은 게시글의 metadata를 관리하는 영역이다. matadata는 날짜, 제목, 태그 등 게시글의 기본정보를 말한다.

  - **[기본 변수](https://gohugo.io/content-management/front-matter#front-matter-variables) | `Predefined variables`**
   
      Front matter에 관한 기본 변수가 많은데, 몇가지 변수를 제외하고는 많이 쓰이지 않는다. 

        ---
        title: "제목"
        date: 날짜
        Tags: ['태그1','태그2']     
        draft: true
        Description: 'description은 검색엔진이 페이지를 참조할 때 사용한다. 블로그 완성 후 검색엔진 최적화(SEO)에 대해 찾아보자 '
        ---

  - **사용자 변수**
   
    사용자는 Front matter에서 변수를 정의해 활용할 수 있다. html에서 변수를 불러오는 방법은 `{{.Params.변수명}}`이다.

    ```html
        {{ define "main" }}
        <div style="text-align: center; height: 1000px;">
            <div  style="margin: 200px auto; font-size: 1.1em;">
            <h1>결과</h1>
            <br>
                    {{ range first 1 .Site.RegularPages }}
                    <h4>.Title</h4>
                    {{ .Title }}
                    <br><br>        
                    
                    <h4>drink</h4>
                    {{ .Params.drink }}
                    <br><br>  
                    <h4>bread</h4>
                    {{ .Params.bread }}
                    <br><br>  
                    {{ end }}    
            </div>
        </div>
        {{ end }}
    ```

    ![Untitled](hugo/documentation/docu_2/Untitled%2026.png)


<br>


### Section과 Taxonomy

게시글을 분류하는 방법에는 Section과 Taxoomy가 있다. 대부분 블로그는 두 방법 모두 사용해 게시글을 분류한다. Section은 파일 경로대로 항목을 분류하는 방법이다. 하위 폴더에 있는 파일들은 모두 같은 주제로 분류 된다. Taxonomy는 게시글에 포함된 태그를 기반으로 분류하는 방법이다. 인스타그램 # 태그처럼 게시글에 원하는 키워드 포함시키면 같은 태그를 가진 게시글을 한번에 모아 볼 수 있다. 

<br>

- **[Section 구조](https://gohugo.io/templates/lists/#what-is-a-list-page-template)**
    
    Section은 파일이 저장된 경로와 관련있다. 같은 폴더에 분류된 자료들은 같은 주제에 속한다. Section의 폴더구조는 아래 그림과 같이 Homepage, Section, Conetnt Page로 구성된다. 

    ![Untitled](hugo/documentation/docu_2/Untitled%2013.png)

    content 폴더 구조를 애플 제품에 대입해보자. 애플/아이폰/프로/에 속한 11과 12는 모두 아이폰 프로라고 불려도 무방하다. 하지만 아이폰 프로 11과 아이폰 맥스 11은 구분된다. 개별 게시글은 하나의 경로만 가지고 있다.

    ![Untitled](hugo/documentation/docu_2/Untitled%2014.png)


  - _index.md
      
    애플 제품 구조를 보면 총 4단계이다. 이를 위에서 설명한 그림에 대입하면 중간 경로 하나가 애매해진다. 애플/아이폰/프로/11 구조에서 프로를 어떤 페이지로 간주해야할지 모르겠다. 상식적으로 생각해보면 프로는 하위 Section이 되어야 한다. 하지만 Hugo는 그렇게 인식하지 않는다. 실제로 애플/아이폰/프로 경로를 들어가면 빈 화면만 뜨며 크롬 개발자 도구로 보더라도 내용이 들어있지 않다. 그렇다고 오류는 아니다. 프로 페이지가 없다고 할지라도 애플/아이폰/프로/11 경로는 정상적으로 작동한다. Hugo는 홈페이지와 바로 붙어있는 경로 만을 Section으로 여기고 나머지 경로는 section으로 여기지도 않고 심지어 Page도 존재하지 않는다. 

    하위 section을 만들고 싶다면 하위 section에 해당하는 폴더 내에 _index.md 파일을 생성하면 된다. Hugo는 _index.md가 포함된 폴더를 Section으로 인식하기 때문이다. 

    _index.md를 추가하고 다시 /애플/아이폰/프로 경로를 들어가면 정상적으로 프로 페이지가 생긴다. _index.md는 front matter을 사용할 수 있으므로 이를 활용하면 편리하게 list page를 관리할 수 있다.


      
  - Section 내 게시글 불러오기
      
    Section을 둘 이상 활용하다보면 겪게되는 문제가 있다. 내가 원하는건 항목에 포함된 모든 게시글을 불러오는 건데 실제로는  하위 항목으로 연결하는 경로만 생성되는 경우가 그렇다. 아이폰 페이지에 들어가면 아이폰 프로 11, 아이폰 맥스 11 등 아이폰 항목에 있는 모든 게시글이 나오도록 구성하고 싶은데, 실제로 아이폰 페이지에 들어가면 프로, 맥스만 표시되고 게시글은 존재하지 상황이다. 

    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <h1>{{.Title}}</h1>
        <br><br>

        {{range .Pages}}
        <h2><a href="{{.Permalink}}"> {{.Title}} </a></h2>
        <br>
        {{end}}

    </div>
    {{ end }}
    ```
    ![Untitled](Documentation_2/Untitled%2030.png)


    현재 이런 상황이라면 아마 `{{range .Pages}}`를 활용해서 페이지가 구성되어 있을거다. 이 명령어는 바로 아래 게층에 있는 페이지만 불러오기 때문에 프로, 맥스와 같은 하위 section만 불러온다. 이때 `{{range .Pages}}`를 한번 더 사용한다면 하위 section에 있는 게시글 모두 불러오게 되므로 아이폰으로 분류된 모든 게시글을 불러올 수 있다.

    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <h1>{{ .Title }}</h1>
        <br><br>

        {{ range .Pages }}
        <h2><a href="{{.Permalink}}"> {{ .Title }} </a></h2>
        <br>
        {{ range .Pages }}
        <h4>{{ .Title }}</h4> &nbsp;
        {{ end }}{{ end }}

    </div>
    {{ end }}
    ```
    ![Untitled](Documentation_2/Untitled%2031.png)


<br>

        
- **[Taxonmy 구조](https://gohugo.io/templates/taxonomy-templates/#example-list-all-taxonomies-terms-and-assigned-content)**
    
    Taxonomy는 태그를 활용해 게시글을 분류하는 방법이다. Taxonomy 계층은 Taxonomy - Term - Value이다. Section과 다른 점은 하나의 게시글이 여러 Term에 포함 될 수 있다는 것이다. 
    
    ![Untitled](Documentation_2/Untitled%2015.png)
    

  - Front matter에 categories 추가하기
   
    기본 Taxonomy로 제공되는 변수로는 tags와 categories가 있다. Front matter에 tags 또는 cetogories를 입력한 뒤 원하는 태그를 작성하면 taxonomy 페이지가 자동 생성 된다.

      ![Untitled](Documentation_2/Untitled%2032_1.png)

      ![Untitled](Documentation_2/Untitled%2033.png)

  - Taxonomy 불러오기
  
    front matter에 설정한 태그 별로 페이지를 불러오자.

    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <h1>{{.Title}}</h1>
        <br><br>

        <section>
            <ul id="all-taxonomies">
                {{ range $taxonomy_term, $taxonomy := .Site.Taxonomies }}
                    {{ with $.Site.GetPage (printf "/%s" $taxonomy_term) }}
                        <li><a href="{{ .Permalink }}">Taxonomy : {{ $taxonomy_term }}</a><br><br> <!--Taxonomy 이름-->
                            <ul>
                                {{ range $key, $value := $taxonomy }}
                                    <li>Term : {{ $key }}</li> <!--Terms-->
                                    <ul>
                                        {{ range $value.Pages }}
                                            <li hugo-nav="{{ .RelPermalink}}">
                                                <a href="{{ .Permalink}}">Page : {{ .LinkTitle }}</a> <!--Pages-->
                                            </li>
                                        {{ end }}
                                    </ul><br><br>
                                {{ end }}
                            </ul>
                        </li>
                    {{ end }}
                {{ end }}
            </ul>
        </section>
    </div>
    {{ end }}
    ```
    ![Untitled](Documentation_2/Untitled%2034.png)


  - 게시글에 태그 표현하기

    현재 게시글에 포함된 taxonomy를 표시하고 링크로 연결하는 방법이다. 

    ![Untitled](Documentation_2/Untitled%2016.png)

    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <h1>{{ .Title }}</h1>
        <br><br>
        {{ range .Pages }}
        <!--테스트용 페이지 하나 불러오기 -->
        {{ range last 1 .Pages }}
        {{.Title}}
        <br>
        <!--Single page에 사용하려면 여기서부터 -->
        <!--.frontmatter에서 categories 대신 tags를 썼다면 Params.tags와 /tags/로 변경-->
        {{ with .Params.categories }}
        {{ range . }}
            <a href='{{ "/categories/" | relLangURL }}{{. | urlize }}'>
            <span >{{. | upper }}</span>
            </a>
            <br>
        {{ end }}{{ end }}
        <!-- 여기까지 복사-->

        {{ end }}{{ end }}

    </div>
    {{end }}
    ```

<br>


### 기타 유용한 함수

- **페이지 개수 세기 | len()**
    
     페이지 개수를 표시하고 싶을 때 사용한다.
    
    ![Untitled](Documentation_2/Untitled%2019.png)
    
    ```html
    <!--하위 페이지 별 페이지 개수 불러오기-->
    <h5>전체보기 {{ len .Site.RegularPages }}개</h5>
    
    <!--Section 별 페이지 개수 불러오기-->
    <ul>
        {{ range .Site.Sections }} 
        <li>
          <h5> {{ .Title }} --- {{ len .Pages }}개 </h5> 
        </li>
        <ul>
            {{ range .Pages }}
          <li>
            {{ .File }} --- {{ .Title }} --- {{ len .Pages }}개
          </li>
            {{ end }}
        </ul>
        {{ end }}
    </ul>
    ```
<br>    

- **[날짜 표현 방법 변경하기](https://gohugo.io/functions/dateformat/#datetime-formatting-layouts) | `date fortmat`**

    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <h1>결과</h1>
        <br>
            <!-- 페이지 불러오기-->
            {{ range first 1 .Site.RegularPages }}
            <h4>.Date</h4>
            {{ .Date }}
            <br><br>
            {{ .Date | time.Format ":date_long" }}
            <br><br>
            {{ .Date | time.Format ":date_short" }}
            <br><br>      
            {{ end }}
    </div>
    {{ end }}
    ```

    ![Untitled](Documentation_2/Untitled%2020.png)

<br><br><br><br><br><br>