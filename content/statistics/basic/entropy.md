---
title: "정보 엔트로피"
date: 2022-03-06T13:47:07+09:00
image: "images/home/statistic.png"
Tags: ['엔트로피','Entropy']
draft: true
---
<br>
<!-- 
정보 Entropy는 집단 내 요소의 확률 분포를 알고 있는 상태에서, 새로운 요소를 예측하기 위해 필요한 질문 개수를 알려준다. -->

<br>


**정보 Entropy 공식**

<br>

{{< center >}}$H \ = \ E(x) = \  -\sum p(x) · \log_{2} p(x) $
{{< /center >}}

<br><br>

정보엔트로피를 처음 배울 땐 엔트로피라는 익숙치 않은 단어와 엔트로피 공식 안에 있는 $\log$ 때문인지 이해하기 어려운 개념으로 비춰진다. 하지만 엔트로피 공식이 고등학교 확률과 통계에서 봤던 기댓값 공식과 다르지 않다는 점과 정보량이 무엇인지만 알게 된다면 그렇게 어려운 개념은 아니다. 정보 엔트로피는 평균 정보량을 구하는 공식일 뿐이기 때문이다. 

우리가 정보엔트로피를 배우면서 어렵고 헷갈리는 가장 큰 이유는 정보 엔트로피가 다양한 방식으로 설명 가능하기 때문이다. 그 중 하나가 엔트로피를 현상의 Surprise를 찾는 공식으로 바라보는 경우이다. 

**Surprise 공식**

$Surprise = \frac{1}{p(x)}$

<br>

Surprise는 발생 확률의 역수를 의미한다. 어떤 현상이 발생 확률이 1/8 이라면 그 현상의 surprise는 8이 된다. Surprise가 높다는 말은 그만큼 발생 가능성이 낮다는 뜻이므로 통계적으로 많은 정보량을 가지고 있음을 보여준다. Surprise라는 개념을 더 알고싶거나 이를 활용해 정보 엔트로피를 이해하고 싶다면 [StatQuest youtube](https://www.youtube.com/watch?v=YtebGVx-Fxw)를 추천한다.

<br>

정보 엔트로피가 오래전 고안된 개념이고, 이를 바탕으로 다양한 이론이 만들어졌기에 다양하게 해석되는건 당연한 결과이다. 이 글을 쓰고 있는 나도 정보 엔트로피를 이해하기 위해서 여러 글을 읽으면서 상당한 혼란을 겪었다. 따라서 이 글은 누군가에게 정보 엔트로피를 소개하기 위한 글이기도 하지만 명확하게 형성한 개념을 다시 혼란스럽게 만들지 않기 위해서 정리하려는 목적도 있다. 이 글은 정보 엔트로피를 이해했으나 여러 개념이 복합적으로 나와서 혼란을 겪고 있는 사람들에게 도움 될거라 생각한다. 

이 글은 정보 엔트로피를 보다 직관적으로 접근함으로서 정보 엔트로피를 어떻게 해석해야하는지 기준을 소개하려 한다. 특히 엔트로피 공식이 어떻게 만들어졌는지, 공식으로 얻은 값이 단순한 숫자인지 아니면 의미를 가지고 있는지 설명할 예정이다.

<br>

## 정보 엔트로피와 기댓값 | `Expected Value`

앞서 소개했듯 정보 엔트로피는 정보량의 기댓값이다. 이번 장에선 기댓값이 무엇인지, 정보 엔트로피가 어떻게 정보량의 기댓값이라 할 수 있는지 알아보겠다.

<br>

 기댓값이라는 개념 자체는 매우 단순하다. 확률을 가지고 있는 변수의 평균 값이라 생각하면 된다. 기댓값이 무엇인지 예시를 통해 복습해보자. 아래 차트는 주사위 2개를 던져 나온 값의 합을 빈도수에 따라 확률로 표현한다. x축은 주사위 값의 합을 y축에는 합이 나올 확률이 표시되어있다.


<br>

![확률분포](/statistics/basic/dice.png) 
출처 위키피디아 이산확률분포

<br>

**기댓값 공식**

{{< center >}} $E(x) = \sum \ p(x) \ ·x \quad \quad $ {{< /center >}}  

<br><br>


기댓값은 확률변수가 취할 수 있는 모든 값들의 평균이다. x는 주사위의 합(2~12)을 의미하고 p(x)는 이러한 합이 나올 확률을 의미한다. 주사위 합이 7이 될 확률은 6/36이다. x는 7이고 p(x)는 6/36이 된다. 그러면 기댓값 공식을 활용해 실제로 주사위 2개의 합에 대한 기댓값을 구해보자.

<br>

 {{< center >}} $E(x) \ = \  2·\frac{1}{36} + 3·\frac{2}{36} + 4·\frac{3}{36} + \ \cdots \ + 11·\frac{2}{36} + 12·\frac{1}{36} = \frac{252}{36}  \ = \ 7 $
{{< /center >}}
<br><br>

공식을 통해 계산된 기댓값은 7이다. 주사위를 무한번 던지면 나온 값들은 평균 7을 가진다는 의미이다. 주사위를 던지는 개별 상황에는 2~12가 확률에 기반해 나온다. 기댓값 7은 이렇게 개별적으로 던져서 나온 값들을 모두 합한 뒤 던진 횟수로 나눈 값을 의미한다. 5번 주사위를 던져서 3,6,12,4,10 나오면 평균 7이 나온다. 개별 값은 3,4,6,10,12이지만 한 번 던졌을때 값은 평균적으로 7의 가치를 한다고 해석할 수 있다. 이처럼 기댓값은 우리가 일상에서 자주 사용하는 평균과 같은 의미로 활용된다. 다만 기댓값은 구하고자 하는 대상이 확률 변수일 뿐이다.


<br><br>

## 정보 엔트로피 공식을 기댓값 공식으로

기댓값이 무엇인지 알았으니 정보 엔트로피가 어째서 정보량의 기댓값으로 불릴 수 있는지 확인해보자. 정보 엔트로피 공식을 약간만 변경하면 앞에서 봤던 기댓값 공식으로 변경할 수 있다. 


**정보 Entropy 공식**

<br>

{{< center >}}$H \ = \ E(x) = \  -\sum p(x) · \log_{2} p(x) $
{{< /center >}}

<br><br>

$\sum$ 앞에 있는 마이너스( - )를 $log_{2}{p(x)}$ 앞으로 옮기자. 그러면 정보량 공식인 $ -\log_{2}{p(x)}$ 이 나온다.(다음 장에서 정보량에 대해 설명한다.) 그 다음  $ -\log_{2}{p(x)}$ 을 x로 치환하자. 그러면 기댓값 공식인 $E(x) = \sum \ p(x) \ ·x  $이 된다.



<br>

**엔트로피 공식 변경**

<br>

{{< center >}}$ H \ =  \ \sum p(x)\ · -\log_{2}{p(x)} \ = \ \sum \ p(x) \ ·x ${{< /center >}}

<br><br>

정보 엔트로피에서 $x$는 정보량을, $p(x)$는 정보량의 확률을 의미한다. 2개 주사위를 굴려 나온 합에 대한 확률분포로 정보량을 계산해보자. 이미 확률을 알고 있으므로 어렵지 않게 정보량을 구할 수 있다.

|값|$p(x)$|$-\log_{2}{p(x)}$|
|:--:|:----:|:-----------------------:|
|2|$\frac{1}{36}$|$-\log_{2}{\frac{1}{36}} \ = \ \log_{2}{36}$ = 3.584|
|3|$\frac{2}{36}$|$-\log_{2}{\frac{2}{36}} \ = \ \log_{2}{18}$ = 4.169|
|4|$\frac{3}{36}$|$-\log_{2}{\frac{3}{36}} \ = \ \log_{2}{12}$ = 5.169|
|$\cdots$|$\cdots$|$\cdots$|
|10|$\frac{3}{36}$|$-\log_{2}{\frac{3}{36}} \ = \ \log_{2}{12}$ = 5.169 |
|11|$\frac{2}{36}$|$-\log_{2}{\frac{2}{36}} \ = \ \log_{2}{18}$ = 4.169|
|12|$\frac{1}{36}$|$-\log_{2}{\frac{1}{36}} \ = \ \log_{2}{36}$ = 3.584|

<br>


**주사위 합에 대한 정보 엔트로피**

<br>

 {{< center >}} $E(x) \ = \  3.584·\frac{1}{36} + 4.169·\frac{2}{36}  + \ \cdots \  + 4.169·\frac{2}{36} +  3.584·\frac{1}{36} = 3.274 $
{{< /center >}}

<br><br>
주사위 합에 대한 정보 엔트로피를 구해봤다. 아직 정보량이 무엇인지 배우지 않았으니 3.274이 어떤 의미를 가지고 있는지 설명할수 없다. 다음 장에서 정보량이 무엇인지 배운 다음 3.274를 어떻게 해석해야 하는지 설명하곘다. 

<br><br>


## 정보량

<br><br>

{{< youtube d3iyDP3_AjU >}}

<br><br>

**정보량 공식**

<br>

{{< center >}}$I(x) = -\log_{2}{p(x)} ${{< /center >}}

<br><br>

정보량이라는 단어는 정보 엔트로피와 다르게 친숙하게 들린다. 단어 뜻 자체가 정보 + 양이라는 의미이다보니 정보를 수치화 한 것이라는 생각이 자연스럽게 든다. 
정보라는 용어는 우리가 일상에서 자주 사용합니다. 그러다보니 단어에 대해 기본적으로 내제된 인식이 있습니다.  최근 우크라이나-러시아 전쟁의 진행상황만 보더라도 미국의 막대한 정보력의 도움을 받은 우크라이나군이 의외의 선전을 보이고 있다고 합니다. 이뿐만 아니라 우리는 정보화 시대에 살며 빅데이터의 중요성을 실감하고 있습니다. 

이와 같이 우리는 정보는 많으면 좋다는 인식을 당연하게 갖고 있습니다. 오히려 정보가 적으면 좋다는 말은 다소 어색하게 들립니다. 하지만 1940년대 고안된 정보량이라는 개념은 이러한 선입견을 없애야 이해할 수 있습니다. (을 이해하기 위해서는 우리가 가지고 있는 정보에 대한 선입견을 없애야 합니다.) 정보가 많으면 좋은거라는 생각으로 정보량을 배우게 되면 이해에 어려움을 겪을 수 있습니다. 실제로 일부 학자들은 정보 이론(엄밀히 말해서는 통신 이론)의 한계중 하나로 정보 개념에 대한 혼란을 발생시켰다는 점을 꼽기도 합니다. 

우리가 상식적으로 알고 있는 정보의 의미를 배제 한체 정보량이라는 의미를 새롭게 이해해봅시다. 여기서 정보량이라 함은 단어가 됐던, 숫자가 됐던 어떤 기호가 됐건 하나의 대상을 다른 대상과 명확하게 구분할 수 있는 최소한의 크기를 말합니다. 이때 구분이라는 단어는 질문이라는 단어로 대체 할 수 있습니다. 철수와 영희가 동전을 하나 던진다고 해봅시다. 이때 영희는 시력이 좋지 않아서 철수만 결과를 볼 수 있습니다. 철수는 장난기가 발동해서 순수하게 결과를 말해주지 않고 물어보면 yes or no로만 대답해준다고 합니다. 이때 영희는 철수에게 최소 몇번의 질문을 해야 결과를 알 수 있을까요? 한번의 질문으로 앞면 또는 뒷면인지 물어보면 그 결과에 따라 동전이 앞면인지 뒷면인지 쉽게 알 수 있습니다. 조금 복잡하게 주사위 결과값을 맞추는 게임을 한다고 해봅시다. 다른 조건은 같습니다. 영희는 최소 몇번의 질문을 사용하면 답을 알 수 있을까요? 여러 전략이 있겠지만 결과가 1인지 2인지 차례대로 물어보는 전략은 좋은 전략이 아닙니다. 여기서 가장 효과적인 전략은 선택지를 줄여 나가는 방법입니다. 영희가 철수에게 나올 수 있는 값인 1~6 중 가운데 값인 3보다 큰지(또는 작은지) 물어보면 그 결과에 따라 선택지 3개를 무조건 지울 수 있습니다. 이런식으로 물어본다면 2~3번의 질문이면 주사위 값을 맞출 수 있습니다.

정보량은 영희가 택한 전략을 그대로 따릅니다. 정보량 공식은 해당 게임(주사위 던지기 또는 동전 던지기)을 해결하기 위해 필요한 질문 수를 쉽게 알려줍니다. $-\log{2}{\frac{1}{6}} = 2.58$ 즉 한 문제당 평균 2.58번의 질문을 수행하면 된다는 말입니다. 2번 질문 2회 3번 질문 4회의 평균을 계산해보면 2.66번으로 얼추 비슷합니다. 두 값이 약간 다른 이유는 공식을 통해서 구한 값이 가장 최적화 된 질문 갯수이기 때문입니다. 자세한 내용은 이 글 하단부에서 소개할 예정입니다. 

클러드 섀넌은 최초로 정보를 수치화 한 사람입니다. 섀넌은 정보의 기본 단위를 0 또는 1을 표현하는 비트로 표현했습니다. 컴퓨터가 2진수로 활용되는 이유 또한 그의 이론에서부터 시작한겁니다. 그의 석사 논문은 인간의 모든 언어가 참 또는 거짓으로 표현될 수 있다는 조지불의 이론을 회로에 접목 가능하다는 사실을 증명해냈습니다. 즉 인간의 모든 언어는 0 또는 1로 표현 될 수 있음을 보여준 셈입니다. 그가 정보의 최소단위를 0 또는 1인 비트로 정의한건 어찌보면 당연한 이유였습니다. 

다시 정보량의 정의로 넘어오겠습니다. 정보량은 대상을 구분하는 최소한의 크기라고 했습니다. 정보의 최소단위인 비트는 두 가지 정보를 포함할 수 있습니다. 비트는 1 or 0 아니면 True or False, yes or no 등으로 표현되겠죠. 동전이 앞면인지, 뒷면인지를 정보 단위로 나타내기 위해선 1비트면 충분합니다.

비트는 yes or no라는 방법으로 정보를 표현한다고 볼 수 있습니다. 우리가 친구와 스무고개 게임을 할 때 yes or no로 대답한 것을 떠올리면 쉽게 이해가 갈 겁니다. 동전의 앞 또는 뒷면을 맞추는 게임이라면 질문 하나로 원하는 답을 얻을 수 있습니다. 친구에게 동전이 앞면인지 한번만 물어보더라도 친구의 답을 통해서 동전이 앞면인지 뒷면인지 쉽게 알 수 있습니다.

이번엔 난이도를 높혀 26개 문자로 구성된 알파벳을 맞추는 문제라고 생각해봅시다. 문제를 맞추기 위해서 사용되는 가장 단순한 방법은 일일이 알파벳이 무엇인지 물어보는 것입니다. A? B? ... Z? 이 방법은 운이 좋다면 한 번에 좋지 않다면 26번째 질문을 해야만 알 수 있습니다. 정말 비효율적인 방법이며 확률에 의존한 방법입니다.

알파벳을 맞추는 게임에서 가장 효율적으로 질문하는 방법은 한번의 질문으로 식별해야하는 대상의 절반을 없애는 이진 탐색을 사용하는 것입니다.
친구에게 알파벳을 직접 물어보는게 아니라 26개 알파벳 중 14번째 알파벳인 N을 기준으로 맞춰야 하는 문자가 앞에 있는지 물어보면 됩니다. N보다 앞에 있냐는 질문에 친구가 yes라고 답했다면 찾고자 하는 문자가 A~M에 있다는 말이 되니 N~Z를 제거할 수 있습니다. 이런 방식으로 질문을 해나가다보면 아래와 같은 도식이 완성됩니다. 아래 완성도를 보면 개별 알파벳을 알기 위해 필요한 최소한의 질문 갯수간 나와있습니다. A를 알기 위해선 ~번, D를 알기 위해서는 ~번 질문을 해야한다는 사실을 알 수 있습니다. 종합적으로 보자면 4번 질문으로 답을 찾을 수 있는 문자는 6개 5번 질문으로 답을 찾을 수 있는 문자는 20개입니다.

이는 평균적으로 알파벳 하나를 맞추기 위해서 평균 4.76번 질문이 필요하다는 것을 의미합니다. 알파벳 하나를 맞추는 게임을 100번 진행한다면 약 476번의 질문만 하면 모두 맞출 수 있다는 말입니다. 

여기서 중요한 점은 앞에서 설명한 비트를 대상을 구분하는데 필요한 질문 갯수로 이해할 수 있다는 점입니다. 대상을 구분할 때 최소한 4번의 질문이 필요하다는 말은 4비트와 같은 의미입니다. 따라서 알파벳 하나를 구분하기 위해서 필요한 비트수는 평균 4.76개 입니다.

추가적인 이해를 돕기위해 숫자 1~8을 맞추는 게임으로 바꿔보겠습니다. 알파벳 문제를 해결하는 방법과 동일하게 대상을 절반씩 줄이도록 질문하면 아래 도식처럼 3 번의 질문이면 모든 문제를 해결 할 수 있습니다. 

1~8 대신 숫자 0~9를 비교한다면 3~4번 질문으로 모든 문제를 해결 할 수 있습니다.


우리가 여기서 알 수 있는 재밌는 사실은 $2^{평균 질문개수} = 문제범위$ 라는 것입니다.  평균 3번의 질문을 필요로하는 경우 8가지 대상 중 하나를 맞추는 게임임을 알 수 있습니다. 

이 공식을 활용한다면 평균 질문 개수를 알수 있습니다. 양변에 $log{2}$를 취하면 $평균 질문 개수 = log{2}{문제범위}$ 공식을 구할 수 있습니다. 

1~8 중 하나를 맞추는 문제의 경우 구분되는 대상이 8개이므로 $log{2}{8}$ = 평균 3번의 질문이면 해결됩니다. 
0~9 중 하나를 맞추는 문제는 구분 대상이 10개 이므로 $log{2}{10}$ = 평균 3.xx번 질문이면 해결 됩니다. 앞서 직접 구했던 방법인 3.xx와는 다소 차이가 있습니다.
알파벳 문제의 경우 구분대는 되상이 26개이므로 $log{2}{26}$ 평균 4.7004번 질문이면 해결됩니다. 앞서 문제를 구했던 4.76개와는 다소 차이가 있습니다. 


그렇다면 이런 의문이 들 수 있습니다. 실제로 구한 경우와 $평균 질문 개수 = log{2}{문제범위}$ 공식으로 구한 질문 개수가 비슷하지만 다르다보니 공식을 통해서 평균 질문을 구하는 방법이 과연 맞을까 궁금합니다. 



**$log_{2}$문제범위 로 평균 질문 개수를 구할 수 있는지 검증하기**

다시 알파벳 문제로 가서 우리는 어떤 알파벳이든 4번 또는 5번 질문이면 대상을 구분할 수 있음을 배웠습니다. 그리고 $log{2}{문제범위}$로 평균 질문 개수를 구하는 방법도 배웠습니다. 하지만 계산 결과는 4.76과 4.7004로 다소 차이가 있습니다. 10000개 되는 문제를 식별하는 게임에 필요한 질문 개수인 47600개와 47004개는 차이가 많이 납니다. 

이게 무슨 이유인지 혼란스러울 것입니다. 둘 다 맞는 말인데 도출된 값에는 차이가 있으니 말입니다. 이 둘에는 어떤 차이가 있을까요?

우리가 구한 4.76번 질문은 26개의 알파벳을 하나 구분하는데 필요한 질문 개수였습니다. 이번에는 알파벳 두 개를 구분해보겠습니다. AA, AB ... ZY,ZZ까지 총 26 * 26 = 676가지 경우의 수가 있습니다.  9번 질문으로 구분되는 대상는 348개 10번 질문으로 구분되는 대상은 328개 입니다. 676개 대상을 구분하기 위한 평균 질문 개수를 구하면 $\frac{9 * 348 + 10 * 328}{676} = 9.485 $개가 됩니다.  $평균 질문 개수 = log{2}{문제범위}$ 공식으로 676개를 구분하면 4.7004로 변함 없습니다. 

|구분 개수|경우의 수 | 평균 질문 개수 | 문자 당 평균 질문 개수 |
|:------:|:---:|:---:|:---:|
|1|$26^1$|4.76|$\frac{4.76}{1} = 4.76$|
|2|$26^2$|9.485|$\frac{9.485}{2} = 4.74$|
|3|$26^3$|14.13|$\frac{14.13}{3} = 4.71$|
|$\vdots$|$\vdots$||$\vdots$|$\vdots$|
|10|$26^{10}$|47.006|$\frac{47.006}{10} = 4.7006$|

문자 하나를 맞추는 경우에는 4.76번의 질문이 필요하지만 맞춰야 하는 문자의 갯수가 늘어날 수록 4.70004에 근접함을 알 수 있습니다. 

따라서 $log{2}{문제범위}$로 얻은 평균 질문개수인 4.7004는 대상이 가질 수 있는 가장 이상적인 평균 질문 개수라고 할 수 있습니다. 



<br><br>

**정보량과 평균질문개수**

이 글의 목적이 엔트로피 공식을 이해하는 것이므로 지금까지 배운 내용을 다시 정리하여 어떻게 엔트로피와 관련이 있는지 알아보겠다. 우리는 정보 엔트로피가 X에 대한 기대값이라는 사실을 알았다. X라 함은 $\log_{2}({\frac{1}{p(x)}})$ 공식을 말한다. 그리고 $\log_{2}({\frac{1}{p(x)}})$ 공식은 정보량이라는 이름을 가지고 있다. 우리가 1~8, 0~9, 알파벳 문제를 풀면서 알게된 공식은 평균질문개수 = $log_{2}$문제범위 였다. 

정보량이라는 개념은 확률을 통해 구한 값인 반면 평균질문 개수는 문제범위를 가지고 구한 값이므로 같은 두 공식이 닮긴 했는데 같인 값인지 애매하다. 이 내용의 처음으로 다시 돌아가보자. A와 B는 랜덤으로 생성된 값을 가지고 게임을 하고 있다. A는 알파벳 A~Z 중 랜덤으로 하나의 값을 고르고 B는 질문을 통해 값을 맞춰야한다. 

여기서 우리는 너무 당연히 여기다보니 고민조차 하지 않는 조건이 하나 있다. 다른 조건이 주어지지 않는 한 A~Z를 무작위로 무수히 선택한다면 개별 값의 빈도수가 모두 같으리라 생각한다. 이를 다르게 표현하자면 개별 값들이 선택될 확률이 일정하다는 사실이다. 즉 A-Z의 개별 값은 1/26의 확률을 가진다.

테이블

|값|확률|
|:------:|:---:|
|A|$\frac{1}{26}$|
|B|$\frac{1}{26}$|
|$\vdots$|$\vdots$|
|Y|$\frac{1}{26}$|
|Z|$\frac{1}{26}$|

A~Z까지 확률이 같으니 대표로 A의 정보량을 구해보자.  $p(x)=\frac{1}{26}$ 이므로 $\log_{2}({\frac{1}{\frac{1}{26}}})$ = $log_{2}(26)$ 이 된다.

흥미롭게도 정보량과 평균질문개수가 동일한 식이다. 따라서 정보량이라는 이름을 가진  $\log_{2}({\frac{1}{p(x)}})$은 대상 하나를 식별하는데 필요한 평균질문개수를 의미한다. 

<br><br>


## 엔트로피 공식 이해하기
지금까지 엔트로피 공식이 X에 대한 기댓값이라는 사실과 기댓값 X로 치환했던 존재인 $\log_{2}({\frac{1}{p(x)}})$가 평균질문개수라는 사실을 설명했다. 

이렇게 알게 된 두 사실을 조합하면 정보 엔트로피 공식의 의미를 알 수 있다. 결론을 도출하기에 앞서 앞에서 계속해서 설명한 예시인 알파벳 문제의 정보 엔트로피를 구해보자.

<br>

**정보 Entropy 공식**

{{< center >}}$ H \ = \ -\sum p(x)\ · \log_{2}{p(x)} \ = \ \sum p(x)\ · \log_{2}({\frac{1}{p(x)}})  ${{< /center >}}

<br><br>

A~Z는 발생할 확률이 동일하다. 확률 $p(x)=\frac{1}{26}$ 이고 정보량 $I(x) = log_{2}(26)$이다. 따라서 $ H = E(x) = \sum \frac{1}{26} \ · \ log_{2}(26) $이다.  

A~Z 값이 26개이므로 아래와 같은 식이 성립된다. 
<br>

$\frac{1}{26} \ · \ log_{2}(26) · 26 = log_{2}(26) \approx 4.70004$

정보 엔트로피를 계산하니 정보량과 값이 같다. 돌고돌아보니 결국 정보 엔트로피, 정보량 평균 질문 개수는 동의어에 불과하다..... 과연 그럴까?

<br><br>

### 발생할 확률이 동일하지 않은 경우
지금까지 우리는 발생할 확률이 동일한 경우를 예시로 활용했다. 예시가 다르다고 지금까지 배웠던 개념이 달라지는건 없다. 정보 엔트로피는 X에 대한 기대값이고 정보량인 X는 평균 질문개수다.

<!-- 
좀 더 현실적인 예시를 들어보자. 아래 테이블은 전세계 노트북 시장 점유율을 보여준다. 주어진 값은 상위 5개 기업과 나머지 기업을 합친 others로 총 6개이다. A와 B가 이번엔 노트북 회사 이름 맞추기 게임을 하고 있다.. A는 기업의 점유율에 맞게 회사를 선택한다. B는 문제 하나를 맞추기 위해 평균 몇 번을 질문 해야할까? 

|회사|점유율|
|:------:|:---:|
|Lenovo|$30%$|
|HP|$20%$|
|DELL|$15%$|
|APPLE|$10%$|
|ACER|$5%$|
|Others|$20%$|

이전 게임에서 최고의 전략으로 여겨졌던 이진탐색을 사용해보자.

정보량은 구할 수 있는데 트리는 어떻게 구현해야하는지 모르겠다. -->


이번엔 난이도를 높혀서 A~D의 발생확률이 다른 상황에서 문제를 맞춰야 한다. A~D가 발생할 확률은 아래 테이블과 같다. 

|값|확률|
|:------:|:---:|
|A|$0.5$|
|B|$0.25$|
|C|$0.125$|
|D|$0.125$|

앞선 예시처럼 단순히 절반을 나누는 방법을 사용해보자. 아래 그림과 같은 구조를 가지게 되며 정보엔트로피 = 정보량 = 평균 질문 개수 = 2가 된다.
그림

하지만 개별 값의 확률 분포를 고려하지 않고 만들었기에 최적의 전략은 아니다.
차라리 이런 모양의 트리를 만든다면 어떻게 될까? A가 선택될 학률이 50%이니 가장 먼저 A를 물어보는게 가능성을 더 높혀주기 때문이다. 이와 마찬가지로 B가 C 또는 D보다 발생 확률이 2배 높으니 B를 물어보는게 좋은 선택이 된다. 완성된 트리는 다소 불균형해 보이지만 실제로는 효과가 좋다. 


이 전략이 효과적이라는 사실을 알았다. 이제는 B가 이 방법을 택해서 문제를 해결한다면 평균 몇번 질문을 필요로하는지 계산해보자. 단순히 반반씩 나눈 전략에 비해 얼마나 질문 수를 줄일 수 있을지 비교하기 위함이다.

A와 B는 40번의 문제 맞추기 게임을 했다. 문제 비율은 확률과 똑같이 발생했다. A는 40번 중 20번, B는 10번 C와 D는 각각 5번 발생했다.  


|값|빈도수|질문 개수|
|:--:|:----:|:--:|
|A|20회|1번|
|B|10회|2번|
|C|5회|3번|
|D|5회|3번|
총합|40회||

빈도수와 질문 개수를 알았으니 이 방법을 사용한다면 평균적으로 사용하는 질문 개수를 알 수 있다. 이 방법을 활용하면 평균 1.75번 질문이 필요하다는 사실을 알수 있다.

<br>

{{< center >}}$\frac{20·1+10·2+5·3+5·3}{40} \ = \ \frac{20}{40} · 1 + \frac{10}{40} · 2  + \frac{5}{40} · 3 + \frac{5}{40} · 3 \ = \ 1.75$ {{< /center >}}

<br><br>




### 정보 엔트로피와 평균 질문 개수
앞선 설명에서 알파벳 문제 처럼 개별 값들의 확률이 동일할 경우, 정보 엔트로피 = 개별 값의 정보량 = 평균 질문 개수라는 사실을 확인했다. 개별 값이 발생할 확률이 다른 경우에도 정보 엔트로피 = 개별 값의 정보량 = 평균 질문 개수가 사실일까? 발생 확률이 다른 A~D 문제의 정보 엔트로피를 구해보자.

<br>

**정보 엔트로피 공식**

|값|$p(x)$|$\log_{2}{p(x)}$|
|:--:|:----:|:-----------------------:|
|A|$\frac{1}{2}$|$\log_{2}{\frac{1}{\frac{1}{2}}} \ = \ \log_{2}{2}$ = 1|
|B|$\frac{1}{4}$|$\log_{2}{\frac{1}{\frac{1}{4}}} \ = \ \log_{2}{4}$ = 2|
|C|$\frac{1}{8}$|$\log_{2}{\frac{1}{\frac{1}{8}}} \ = \ \log_{2}{8}$ = 3|
|D|$\frac{1}{8}$|$\log_{2}{\frac{1}{\frac{1}{8}}} \ = \ \log_{2}{8}$ = 3|

<br>

이를 엔트로피 공식에 대입하면 

$\frac{1}{2} · 1 + \frac{1}{4} · 2  + \frac{1}{8} · 3 + \frac{1}{8} · 3 = 1.75$ 

즉 정보 엔트로피와 평균 질문 개수는 같다. 따라서 우리가 어떤 집단의 확률분포를 알고있다면 하나의 대상을 구분하기 위해 필요한 질문 수(=bit)를 계산할 수 있다. 그리고 정보 엔트로피 공식으로 얻은 값이 곧 질문 개수이다.



<br><br>
2부에서는 평균 질문 개수가 정보 엔트로피라는 사실을 바탕으로 정보 엔트로피의 의미에 대해서 이야기하겠다. 

<!-- 기댓값에서 짚고넘어가야 할 사실은 기댓값을 구하기 위해서는 특정 집단의 이산확률분포를 안다는 것을 전제해야한다. 정보 엔트로피도 정보량의 기댓값을 계산하는 공식이므로 구하고자 하는 집단의 확률분포를 필요로한다는 사실을 염두에 두자. -->