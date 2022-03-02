---
title: "공식 Docs 활용을 위한 기본 문법및 용어정리 2부"
date: 2022-03-01
image: "images/home/hugo1.jpg"
image_webp: "images/home/hugo.webp"
Tags: ['Hugo Documentation','Do It Yourself']     
draft: true
Description: 'Description'
---
<br>

**[1부 보러가기](/hugo/documentation/documentation)**

<br>

### Hugo와 HTML

Hugo는 HTML 구조를 쉽게 만들기 위해 활용된다. go template 문법을 활용해 페이지를 구성한다. 

<br>


### 사람마다 원하는 기능이 다르다. 이 글과 Documentation을 활용해 본인이 직접 기능을 만드는 것도 좋은 경험이 될 것이다.

<br><br>

## 연습환경 구축하기

<br>

### 연습장 만들기

- **Laoyouts 폴더 복사하기**
    
    ![Untitled](Documentation_2/Untitled.png)
    
<br>
 
- **Index.html 정리하기**
  
   VScode활용 할것임. 
   모든 문법은 Homepage(=index.html)에서 작성됐다.  Hugo 폴더 구조를 모른다면 1부를 먼저 읽는 것을 추천한다.
    

    ![Untitled](Documentation_2/Untitled%201.png)
    
<br>

- **Content 폴더 구조**
  
  연습용 블로그에는 총 12개 md 파일이 있다. 5개는 Content 폴더에 7개는 Content/post 폴더에 있다. Hugo에서 경로가 곧 URL이 되니 연습용으로 활용하는 폴더 구조를 확인하고 넘어가자
    
    ```html
    Content 
    |   about.md   
    |   contact.md
    |   elements.md
    |   FolderList.txt
    |   terms-conditions.md
    |
    \---post
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
  
    변경 사항을 보다 편리하게 보기 위한 팁이다.    `윈도우키` + `방향키`를 누르면 아래 그림과 같이 페이지를 구분해서 사용할 수 있다. 글에서 제공하는 예시 코드를 붙여넣고 결과와 코드를 비교하면서 구조를 이해하자.
    
    ![Untitled](Documentation_2/Untitled%2022.png)

<br><br>

## Hugo 기본문법 
이 게시글은 Hugo Documentation을 활용하기 위한 만큼 다루고 있는 항목에 맞는 공식 문서 링크를 걸어놓았다. 관련 내용을 더 알고 싶다면 링크 걸어놓은 공식 문서를 활용하자. 
Hugo 공식문서를 이해하기 위해서는 자주 사용하는 용어에 익숙해져야 한다. 항목 우측에는 `코드형식`으로 관련 용어를 포함했으니 -활용바란다.-
<br>

### 변수 설정 및 함수 불러오기 


- **[변수 정의하기](**https://gohugo.io/about/**) | `Custom Variable`**
    
    변수를 정의하기 위해서는 `{{$var := “text”}}` 로 작성하고 `{{$var}}`로 불러온다.
    
    ```html
    {{ define "main" }}
    <div style="text-align: center;">
        <div  style="margin: 200px auto; font-size: 1.5em;">
        <!--String 변수 설정-->
        {{$drink := "a coffee"}}
        Your drink is {{$drink}}
        <br><br>
    
        <!--함수 또는 페이지 변수를 활용하여 변수 설정-->
        {{$title := .Title}}
        your title is {{$title}}
        </div>
    </div>
    {{ end }}
    ```
    
    ![Untitled](Documentation_2/Untitled%202.png)

<br>

- **[함수 또는 페이지 변수 불러오기](https://gohugo.io/templates/introduction/#access-a-predefined-variable) | `Predefined Variable`** 
    
    `{{.명령어}}`로 함수 또는 페이지 변수를 불러온다.
    
    ```html
    {{ define "main" }}
    <div style="text-align: center;">
        <div  style="margin: 200px auto; font-size: 1.5em;">
        {{.Title}}
        </div>
    </div>
    {{ end }}
    ```
    
    ![Untitled](Documentation_2/Untitled%203.png)
    

<br>


### 조건절

조건절은 `{{ 조건절 }} 내용 {{ end }}` 으로 사용한다.

- **[If 조건절](https://gohugo.io/templates/introduction/#example-3-if) | `Conditional`**
    - .IsPage | .IsSection | .IsNode | .IsHome
        
        Hugo는 페이지를 기능적으로 구분한다. 1부 layouts 항목에서 기능에 대해 간략히 설명했으니 기억나지 않는다면 다시 확인하자.[1부 layouts 설명](http://localhost:1313/hugo/documentation/documentation/#layouts) 
        
        페이지 종류에 따라 수정해야 하는 파일이 다르고 사용하는 페이지 변수도 약간 다르니 내가 어느 페이지를 수정하고 있는지 인지해야한다. 
        > `{{.Kind}}`를 활용하면 페이지 종류를 확인할 수 있다.
        
        <br>

        `.IsPage` | `.IsSection` | `.IsNode` | `.IsHome`은 페이지 요소에 따라 Boolean(True or False)를 반환한다. 주로 Baseof.html에서 페이지 종류별로 원하는 기능을 실행 또는 숨기기 위해 사용한다.

        ```html
        {{ define "main" }}
        <div style="text-align: center;">
            <div  style="margin: 200px auto; font-size: 1.5em;">
            <!-- {{.Kind}} 함수를 사용하면 현재 페이지가 어떤 요소인지 알 수 있다.  -->
            현재 페이지 요소 : {{.Kind}}
            <br><br>
            
            <!--Home page인 경우 True 반환-->
            {{if .IsHome}}
            This Page is home page
            <br><br>
            {{end}}
        
            <!--single page가 아닌 경우 True 반환-->
            {{if .IsNode}}
            This Page is not a single page
            <br><br>
            {{end}}
        
            <!--single page인 경우 True 반환-->
            {{if .IsPage}}
            This Page is a single page
            <br><br>
            {{end}}
        
            <!--section page인 경우 True 반환-->
            {{if .IsSection}}
            This Page is a Section page
            {{end}}
        </div>
        </div>
        {{ end }}
        ```
        
        ![Untitled](Documentation_2/Untitled%204.png)
        
    - and / or
        
        and와 or은 두 가지 방법으로 사용가능하다.
        
        ```html
        {{ define "main" }}
        <div style="text-align: center;">
            <div  style="margin: 200px auto; font-size: 1.5em;">
                <!-- {{.Kind}} 함수를 사용하면 현재 페이지가 어떤 요소인지 알 수 있다.  -->
                현재 페이지 요소 : {{.Kind}}
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
        
        ![Untitled](Documentation_2/Untitled%205.png)
        
    - 비교 연산자
        
        `{{ if eq arg 1 arg 2}} 내용 {{end}}`으로 비교 연산자를 사용한다.
        
        | eq | arg1 == arg2 | le | arg1 <= arg2 |
        | --- | --- | --- | --- |
        | ge | arg1 >= arg2 | lt | arg1 < arg2 |
        | gt | arg1 > arg2 | ne | arg1 != arg2 |
        
        ```html
        {{ define "main" }}
        <div style="text-align: center;">
            <div  style="margin: 200px auto; font-size: 1.5em;">
            {{$drink := "coffee"}}
            
            {{if eq "coffee" $drink}}
                커피 마시는 중
            {{end}}
        
            {{if eq "tea" $drink}}
        		차 마시는 중
            {{end}}
            
            </div>
        </div>
        {{ end }}
        ```
        
        ![Untitled](Documentation_2/Untitled%206.png)
        
- **[with 조건절](https://gohugo.io/templates/introduction/#iteration) | `Conditional`**
    
    If와 range가 함께 사용되는 조건절이다. 
    
- Where 모르겠다..

<br>

### Page 불러오기

- **하위 페이지 불러오기**
  
  `{{range .Pages}} {{.}} {{end}}` 명령어를 사용하면 현재 페이지 기준 하위 계층 페이지를 불러온다. 말단 페이지까지 불러오려면 폴더 계층에 따라 명령어를 추가해야한다. 현재 예시는 `content/post/post-1.md`이기 때문에 2단계에서 끝났지만, `content/post/subpost/post-1.md`라면 3단계 결과도 나올 것이다.
  > 설명이 이해되지 않는다면 폴더 경로를 여러 겹으로 만들어서 테스트해보자. 
  > 
  > ex) `content/post/subpost/subpost-1/post1.md`


  ```html
        {{ define "main" }}
        <div style="text-align: center; height: 1000px;">
            <div  style="margin: 200px auto; font-size: 1.1em;">
            <br>
            {{range .Pages}}
            <br>
            1단계 --- 경로 : {{.RelPermalink}} &nbsp; &nbsp;<br> 
            {{range .Pages}}
            2단계 --- 경로 : {{.RelPermalink}} &nbsp; &nbsp;<br>
            {{range .Pages}}
            3단계 --- 경로 : {{.RelPermalink}}
            {{end}}{{end}}{{end}}
        </div>
        {{ end }}
  ```
  ![Untitled](Documentation_2/Untitled%2021.png)

- **페이지 한번에 불러오기**
    
    앞에서 설명한 `{{.Pages}}`는 현재 페이지의 하위 항목을 불러왔다면 지금 설명하는 명령어는 페이지에 상관없이 페이지 전체를 불러오는 방법이다. 

     `{{ .Site.Pages }}`는 해당 홈페이지가 가지고 있는 모든 페이지를 불러온다. 

     `{{ .Site.RegularPages }}`는 Single page만 불러온다. content 폴더에 있는 markdown 파일 중 _index.md만 제외하고 모두 불러오는 것과 같다.

     `{{whth .Getpage arg1 arg2}}{{.}}{{ end }}`는 조건에 맞는 페이지만 불러온다. 주로 list page(Section과 Taxonomy 모두 해당)를 생성할 때 사용한다. | [with .Getpage 사용법 더보기](https://gohugo.io/functions/getpage/)
    
    <br>

  - .Site.RegularPages | .Site.Pages  | with .Getpage arg 1 arg 2
        
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
                    {{.Site.RegularPages}}
                </div>
        
                <!-- 가운데-->
                <div style ="float:left; margin: 0 20px;">
                    <!--모든 페이지 불러오기-->
                    <h3>.Pages</h3>
                    <br><br>
                    {{.Site.Pages}}
                </div>
        
                <!-- 오른쪽-->
                <div style ="float:left; margin: 0 20px;">
                    <h3>with .Site.GetPage</h3>
                    <br><br>
                    <!--Section이 post인 페이지 불러오기-->
                    <!--with .Getpage arg 1 arg 2-->
                    {{with .Site.GetPage "section" "post"}}
                    {{.}}
                    {{end}}
                </div>
            </div>
        </div>
        {{ end }}
    ```
        
    ![Untitled](Documentation_2/Untitled%207.png)
    
    <br>

  - Page 불러오기
  
    위에서 사용된 명령어와 같이 결과값으로 Pages()을 반환하는 경우 `{{range .Pages}}{{.}}{{end}}` 명령어를 이용해 개별 페이지를 불러올 수 있다.

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
                {{range .Site.RegularPages}}
                {{.File}} <!-- 파일경로-->
                <a href="{{.Permalink}}">site</a> <!-- 사이트-->
                <br>
                {{end}}
            </div>
    
            <!-- 가운데-->
            <div style ="float:left">
                <!--모든 페이지 불러오기-->
                <h3>.Pages</h3>
                <br><br>
                {{range .Site.Pages}}
                {{.File}} <!-- 파일경로-->
                <a href="{{.Permalink}}">site</a> <!-- 사이트-->
                <br>
                {{end}}
            </div>
    
            <!-- 오른쪽-->
            <div style ="float:left">
                <!--모든 페이지 불러오기-->
                <h3>with .Site.GetPage</h3>
                <br><br>
                {{with .Site.GetPage "section" "post"}}
                {{.}}
                <br>
                <!-- 개별 post Page 불러오기 -->
                {{range .Pages}} 
                {{.File}} <!-- 파일경로-->
                <a href="{{.Permalink}}">site</a> <!-- 사이트-->
                <br>        
                {{end}}
                {{end}}
            </div>
        </div>
    
    </div>
    {{ end }}
    ```
        
    ![Untitled](Documentation_2/Untitled%208.png)
    
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
                {{range first 3 .Site.Pages}}
                {{.File}} <!-- 파일경로-->
                <a href="{{.Permalink}}">site</a> <!-- 사이트-->
                <br>
                {{end}}
            </div>


        </div>
        {{ end }}
    ```
    
    ![Untitled](Documentation_2/Untitled%2024.png)
        

<br>

### Hugo 변수

페이지 변수가 무엇인지 소개

- **[Site 변수](https://gohugo.io/variables/site/) | `Site Variables`**
    
    Config에 저장한 변수를 불러오거나 블로그 전역 변수를 불러올 때 사용한다.
    여러 변수 중 자주 사용되는 변수만 예시로 작성했다.
    
    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <!-- Local Server일 경우 True 아닐 경우 False-->
        <h4>.Site.IsServer</h4> : {{.Site.IsServer}}
        <br><br>
        <!-- 블로그에 있는 모든 Taxonomy 불러오기 -->
        <h4>.Site.Taxonomies</h4> :  {{.Site.Taxonomies}}
        <br><br>
        <!-- 블로그에 있는 모든 Page 불러오기 -->
        <h4>.Site.Pages</h4>{{.Site.Pages}}
        <br><br>
        <!-- 블로그에 있는 모든 single Page 불러오기 -->
        <h4>.Site.RegularPages</h4>{{.Site.RegularPages}}
        <br><br>
        <!--Config 내 Paramter 불러오기-->
        <h4>.Site.Params.logo</h4>{{.Site.Params.logo}}
        <br><br>
        <h4>.Site.Params.favicon</h4>{{.Site.Params.favicon}}
        <br><br>
        <h4>.Site.Params.variables.primary_color</h4>
        {{.Site.Params.variables.primary_color}}
        <br><br>
      
    </div>
    {{ end }}
    ```
    
    ![Untitled](Documentation_2/Untitled%2010.png)
    
- **[Page 변수](https://gohugo.io/variables/page/) | `Page Variables`**
    
    페이지가 Markdown 파일에 기반한 경우 사용 가능한 변수이다. Single page 또는 _index.md 파일이 있는 list page에서 사용가능하다. `{{range .Pages}}`로 single page를 불러와서도 사용 할 수 있다. 많은 변수들이 Front matter에 적힌 내용을 불러오는데 사용가능하다. Front matter를 적절히 활용하면 원하는 기능을 쉽게 구현할 수 있다.
    
    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
    
            <!-- 페이지 하나만 불러오는 Range 함수-->
            {{range first 1 .Site.RegularPages}}
    
            <!--Markdown 본문 가져오기-->
            <h4>.Content </h4>
            페이지 본문
            <br><br>
    
            <!-- Type 또는 Section 이름 불러오기-->
            <h4>.Type</h4>
            {{.Type}}
            <br><br>        
    
            <!--상대주소-->
            <h4>.RelPermalink</h4>
            {{.RelPermalink}}
            <br><br>
    
            <!--절대주소-->
            <h4>.Permalink</h4>
            {{.Permalink}}
            <br><br>
    
            <!--본문 단어 개수-->
            <h4>.WordCount</h4>
            {{.WordCount}}
            <br><br>
    
            <!--Front matter에 있는 title 불러오기-->
            <h4>.Title</h4>
            {{.Title}}
            <br><br>
    
            <!--Front matter에 있는 date 불러오기-->
            <h4>.Date</h4>
            {{.Date}}
            <br><br>
    
            <!--Front matter에 있는 description 불러오기-->
            <h4>.Description </h4>
            {{.Description}}
            <br><br>
    
            <!--Page 종류 확인(home,page,section,taxonomy,term)-->
            <h4>.Kind</h4>
            {{.Kind}}
            <br><br>
    
            <!--읽는 시간 예측-->
            <h4>.ReadingTime</h4>
            {{.ReadingTime}}
            <br><br>
    
            <!--첫 문단 요약-->
            <h4>.Summary</h4>
            첫문단 요약
            <br><br>
            {{end}}
    </div>
    {{ end }}
    ```
    
    ![Untitled](Documentation_2/Untitled%2011.png)
    
- **[File 변수](https://gohugo.io/variables/files/) | `File Variables`**
  
    폴더가 URL주소가 되는 만큼 원하는 URL 주소를 불러오기 위해 주로 사용한다.
    URL 변환 시 자주 사용되는 함수로는 print와 replace 함수가 있다. 먼저 자주 사용되는 File 변수를 알아본 뒤 두 함수를 마저 알아보자.
    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
    
            {{range first 1 .Site.RegularPages}}
            <!--Content Folder 이후 경로 및 파일-->
            <h4>.File.Path</h4>
            {{.File.Path}}
            <br><br>      
    
            <!-- 파일경로 -->
            <h4>.File.Dir</h4>
            {{.File.Dir}}
            <br><br>        
    
            <!--파일명 (확장자 포함)-->
            <h4>.File.LogicalName</h4>
            {{.File.LogicalName}}
            <br><br>        
    
            <!-- 파일명(확장자 미포함)-->
            <h4>.File.BaseFileName</h4>
            {{.File.BaseFileName}}
            <br><br> 
            {{end}}
    
    </div>
    {{ end }}
    ```
    
    ![Untitled](Documentation_2/Untitled%2012.png)
    

    -File 변수와 자주 사용되는 함수

    Hugo는 언어를 이어붙이는 방법이 까다로운데, print 함수를 활용하면 쉽게 붙일 수 있다.
    
     Window에서 File variables를 사용하면 경로가 Back-slash( \ )로 표현된다. Back-slash( \ )를 Slash( / )로 변환하기 위해 replace를 사용한다. 

    ```html
        {{ define "main" }} 
        <div style="text-align: center; height: 1000px;">
            <div  style="margin: 200px auto; font-size: 1.1em;">
            <h1>결과</h1>

            
            <!-- Print 함수를 사용하고 변수를 선언하므로 총 2번의 과정을 거친다. 
            먼저 실행 되는 함수에 괄호를 쳐야 오류가 발생하지 않는다.  -->
            <!-- 사용법 : print 문장1 문장2 문장3 문장4... -->
            {{ $sentence := (print "단어를 " "이렇게 " "조합해도 " "됩니다." ) }}
            {{ $sentence }}

            {{range .Pages}}
            <br>
            {{ range first 3 .Pages }}
            {{ $site := ( print "/drink/Ice Americano/" .File ) }}
            <br>
            변경 전 : {{ $site }}
            <br>
            <!-- 두 번 연속으로 바꾸고 싶다면 아래 예시처럼 괄호를 추가해서 사용하자 -->
            <!-- Back-slash를 다른 단어로 바꾸고 싶다면 아래 예시와 같이 두 번 사용해야 한다. -->
            <!-- 사용법 : replace 바꾸고 싶은 문장 "바뀔 단어" "바꿀 단어" -->
            변경 후 : {{ replace ( replace $site "Ice Americano" "Ice Latte" ) "\\" "/" }}<br>
            {{ end }}
            {{ end }}
            
        </div>
        {{ end }}
    ```
    ![Untitled](Documentation_2/Untitled%2023.png)

<br>


### 자료 불러오기

- Assets 폴더에서 자료 불러오기
- Static 폴더에서 자료 불러오기
    - Image 불러오기
    - CSS, Javascript 불러오기

### Front matter
[[https://gohugo.io/content-management/front-matter#front-matter-variables](https://gohugo.io/content-management/front-matter#front-matter-variables)]

- 기본 변수
- 사용자 정의 변수

<br>


### Section과 Taxonomy

Section과 Taxonomy는 List page를 만들기 위해 사용한다.  메뉴바를 보면 주제별로 분류되어 있어 원하는 주제의 게시글을쉽게 찾아 볼 수 있다. Section은 이러한 방식을 지원한다. 한편으로 Instagram # 태그처럼 원하는 키워드를 가진 게시글을 찾을 수 있다. Taxonomy는 이러한 방식이다.

- Section 구성원리
    
    Section은 파일이 저장된 경로와 관련있다. 같은폴더에 분류된 파일(또는 폴더)는 같은 주제에 속한다. Section의 폴더구조는 아래 그림과 같이 Homepage, Section, Conetnt Page로구성된다. 
    
    ![Untitled](Documentation_2/Untitled%2013.png)
    
    content폴더 구조를 애플 제품에 대입해보자. 애플/아이폰/프로/ 에 해당하는 버전은 모두 아이폰 프로라고 불려도 무방하다. 지금 지극히 상식적인 이야기를 하고 있는 중이다.
    
    ![Untitled](Documentation_2/Untitled%2014.png)
    
    - _index.md
        
        B_index.md는 Section을 추가할 때 사용된다. Hugo는 Homepage-section-content page  세 단계만 페이지가 형성된다.  물론 세 단계 이상으로 폴더를 세분화 한다고오류가 발생하지는 않는다. 다만 Section과 Page 사이에 있는 경로는 아무런 내용이 들어있지 않는다. 즉 애플/아이폰/프로/11 경로를 만들어도 정상적으로 작동하나, 애플/아이폰/프로 경로로 들어가면 아무 내용이 표시되지 않는 빈 화면만 나온다. 
        
        section 추가가 필요하지 않다면 굳이 설정하지 않아도 되지만 프로에 포함된 항목을 보여주는 페이지를 만들고 싶다면 Section을 추가해야한다. 
        
        _index.md는 Hugo가 Section 폴더를 Homepage로 생각할 수 있도록 하는 기능이다. Bundle Page를 추가한다면 애플/아이폰/프로/11 경로에서 아이폰은 애플의 Section이기도하고 프로와 맥스의 Homepage이기도 하다. 그렇게 되면 프로는 아이폰 Homepage의 Section으로 기능하게 된다.
        
        _index.md가 되기 위해서는 Homepage로 만들고 싶은 폴더에 _index.md 파일을 추가하면 된다. 그러면 자동으로 프로와 맥스는 Section이 된다.  _index.md 파일은 {{.Site.RegularPages}} 명령어에서 검색되지 않는다. Single page를 구성하는게 아닌List page를 구성하기 위한 요소이기 때문이다. _index.md도 Markdown 파일인 만큼 Frontmatter를 사용할 수 있고 Homepage에서 불러올 수 있다.
        
    - 하위 Section 불러오기
        
        하위 Section을 불러오기 위한 두 가지 방법이 있다. 
        
        하나는 {{.Type}}명령어를 이용하는 방법이다. _index.md에 front matter을 사용하면 List page에서 관련 요소를 불러올 수 있다고 설명했다. front matter 요소 중 type을 추가해 해당 페이지가 어떤 section인지 명시할 수 있다.  
        
        다른 하나는 `{{ .Site.GetPage "section" "하위 섹션 이름" }}` 이다. 

    <br>


        
- **Taxonmy 구성원리**
    
    Taxonomy는 자료를 분류하는 또다른 기준이다. Section과 다른점은 경로를 활용하지 않고 태그를 활용해 게시글을 분류한다.  따라서 같은 게시글이 다른 Term에 포함된다. Taxonomy - Term - Value으로 계층을 구분한다.   
    
    ![Untitled](Documentation_2/Untitled%2015.png)
    

    <br>


- **게시글에 Taxonomy 활용하기**
  - Config에 아래 코드 붙여넣기
      
      ```html
      taxonomies:
        tags : Tags
      ```
      
      <br>


  - Front matter에 Tags 추가하기
      
      ```html
      ---
      title: "공식 Docs 활용을 위한 기본 문법 및 용어정리 1부"
      date: 2022-02-26
      Tags: ['Hugo Documentation','Do It Yourself']
      ---
      ```
      
      ![Untitled](Documentation_2/Untitled%2016.png)
      
      <br>


      ```html
      ---
      title: "게시글에 사진 확대기능 추가하기"
      date: 2022-02-21
      Tags: ['medium-zoom', 'post','Do It Yourself']
      ---

      <br>

      ```
      
      ![Untitled](Documentation_2/Untitled%2017.png)
      
      Section이 다른 게시글이 DO IT YOURSELF 태그에 분류 됐다.
      
      > url 주소는 Taxonomy/term/ 으로 만들어진다. ([/tags/do-it-yourself/](http://localhost:1313/tags/do-it-yourself/))
      > 
      
      ![Untitled](Documentation_2/Untitled%2018.png)
      

<br>


### 기타 유용한 함수

- 하위 항목 페이지 개수 세기
    
    아래 와 같이 유형별 페이지 개수를  나타낼 때 사용한다.
    
    ![Untitled](Documentation_2/Untitled%2019.png)
    
    ```html
    <!--하위 페이지 별 페이지 개수 불러오기-->
    <h5>전체보기 {{ len .Site.RegularPages }}개</h5>
    
    <!--Section 별 페이지 개수 불러오기-->
    <ul>
        {{ range .Site.Sections }} 
        <li>
          <h5> {{.Title}} --- {{ len .Pages}}개 </h5> 
        </li>
        <ul>
            {{ range .Pages }}
          <li>
            {{.File}} --- {{.Title}} --- {{len .Pages}}개
          </li>
            {{ end }}
        </ul>
        {{ end }}
    </ul>
    ```
<br>    

- 날짜 표현 방법 변경하기[[https://gohugo.io/functions/dateformat/#datetime-formatting-layouts](https://gohugo.io/functions/dateformat/#datetime-formatting-layouts)]

    ```html
    {{ define "main" }}
    <div style="text-align: center; height: 1000px;">
        <div  style="margin: 200px auto; font-size: 1.1em;">
        <h1>결과</h1>
        <br>
            <!--하위 페이지 별 페이지 개수 불러오기-->
            {{range first 1 .Site.RegularPages}}
            <!--Content Folder 이후 경로 및 파일-->
            <h4>.Date</h4>
            {{.Date}}
            <br><br>
            {{.Date | time.Format ":date_long" }}
            <br><br>
            {{.Date | time.Format ":date_short" }}
            <br><br>      
            {{end}}

    </div>
    {{ end }}
    ```

![Untitled](Documentation_2/Untitled%2020.png)