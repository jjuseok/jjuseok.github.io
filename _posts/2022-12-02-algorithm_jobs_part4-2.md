---
layout: post
title: '[ALGORITHM_JOBS] 27. baseball game'
date: '2022-12-02 16:30:10 +0900'
description: 'baseball game'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.4]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
정보문화진흥원 정보 영재 동아리에서 동아리 활동을 하던 영수와 민혁이는 쉬는 시간을 틈타 숫자야구 게임을 하기로 했다.

영수는 1에서 9까지의 서로 다른 숫자 세 개로 구성된 세 자리 수를 마음속으로 생각한다. (예: 324) 민혁이는 1에서 9까지의 서로 다른 숫자 세 개로 구성된 세 자리 수를 영수에게 묻는다. (예: 123) 민혁이가 말한 세 자리 수에 있는 숫자들 중 하나가 영수의 세 자리 수의 동일한 자리에 위치하면 스트라이크 한 번으로 센다. 숫자가 영수의 세 자리 수에 있긴 하나 다른 자리에 위치하면 볼 한 번으로 센다. 예) 영수가 324를 갖고 있으면

- 429는 1 스트라이크 1 볼이다.
- 241은 0 스트라이크 2 볼이다.
- 924는 2 스트라이크 0 볼이다.

영수는 민혁이가 말한 수가 몇 스트라이크 몇 볼인지를 답해준다. 민혁이가 영수의 세 자리 수를 정확하게 맞추어 3 스트라이크가 되면 게임이 끝난다. 아니라면 민혁이는 새로운 수를 생각해 다시 영수에게 묻는다. 현재 민혁이와 영수는 게임을 하고 있는 도중에 있다. 민혁이가 영수에게 어떤 수들을 물어보았는지, 그리고 각각의 물음에 영수가 어떤 대답을 했는지가 입력으로 주어진다. 이 입력을 바탕으로 여러분은 영수가 생각하고 있을 가능성이 있는 수가 총 몇 개인지를 알아맞혀야 한다.

아래와 같은 경우를 생각해보자.

- 민혁: 123
- 영수: 1 스트라이크 1 볼.
- 민혁: 356
- 영수: 1 스트라이크 0 볼.
- 민혁: 327
- 영수: 2 스트라이크 0 볼.
- 민혁: 489
- 영수: 0 스트라이크 1 볼.

이 때 가능한 답은 324와 328, 이렇게 두 가지이다.

영수는 동아리의 규율을 잘 따르는 착한 아이라 민혁이의 물음에 곧이곧대로 정직하게 답한다. 그러므로 영수의 답들에는 모순이 없다.

민혁이의 물음들과 각각의 물음에 대한 영수의 답이 입력으로 주어질 때 영수가 생각하고 있을 가능성이 있는 답의 총 개수를 출력하는 프로그램을 작성하시오.
<hr>
# <b>입력</b>
첫째 줄에는 민혁이가 영수에게 몇 번이나 질문을 했는지를 나타내는 1 이상 100 이하의 자연수 N이 주어진다. 이어지는 N개의 줄에는 각 줄마다 민혁이가 질문한 세 자리 수와 영수가 답한 스트라이크 개수를 나타내는 정수와 볼의 개수를 나타내는 정수, 이렇게 총 세 개의 정수가 빈칸을 사이에 두고 주어진다.
<hr>
# <b>출력</b>
첫 줄에 영수가 생각하고 있을 가능성이 있는 답의 총 개수를 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
4
123 1 1
356 1 0
327 2 0
489 0 1
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
2
</pre>
<hr>
# <b>아이디어</b>
문제를 풀기 전에 많이 생각을 해봤다.... 사람이 풀기도 복잡한 문젠데 이걸 어떻게 하면 코드로 구현할 수 있을까?<br>

아무리 생각해도 하나씩 다 비교해 보는 방법밖에 없는 것 같다..... 그래서 하나씩 다 비교하기로 마음을 먹었다.<br>
예제 입력 중에 첫 번째 입력을 예시로 들어보자. [123, 1, 1] 123의 숫자에 대해서 1 스트라이크 1볼을 의미한다.<br>
이 경우의 수를 찾으려면 111 ~ 999가 있는데 세 숫자가 서로 중복되면 안 된다는 조건이 있다.<br>
따라서 if 문을 이용해 서로 중복되지 않은 경우에만 숫자를 비교하면 된다.<br>

코드를 간단히 설명하자면 일단 큰 틀로 for문 3개를 사용했다. for문 3개를 사용한 이유는 하나씩 다 확인하기 위함이다.<br>
123의 숫자에 대해서 111 ~ 999(중복제외)를 하나씩 비교하는 것이다. 123 과 123비교, 124와 123비교, 125와 123비교........<br>
n개의 숫자를 비교한 뒤 스트라이크와 볼의 개수가 맞으면 가능성이 있는 답으로 판단한다.<br>
비교할 때 first라는 변수로 첫째 자리, second 둘째 자리, third 셋째 자리로 구한 뒤 i, j, k랑 각 각 비교한다.<br>
첫째 자리, 둘째 자리, 셋째 자리를 구하는 방법은 간단하게 나눗셈과 나머지를 이용해서 하나씩 구했다.<br>
여기서 i: 첫째 자리, j: 둘째 자리, k: 셋째 자리를 의미한다.(비교하는 숫자의)<br>
최종적으로 가능성이 있는 답의 개수를 출력한다.


<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
n = int(input())
arr1 = [list(map(int, input().split())) for _ in range(n)]
result = 0

for i in range(1, 10):
    for j in range(1, 10):
        for k in range(1, 10):
            if i != j and j != k and i != k:
                flag = False
                for z in range(n):
                    first = arr1[z][0] / 100
                    first = int(first)
                    
                    second = (arr1[z][0] / 10) % 10
                    second = int(second)
                    
                    third = arr1[z][0] % 10
                    
                    strike = 0
                    ball = 0
                    
                    if first == i:
                        strike += 1
                    if second == j:
                        strike += 1
                    if third == k:
                        strike += 1
                    
                    if first == j or first == k:
                        ball += 1
                    if second == i or second == k:
                        ball += 1
                    if third == i or third == j:
                        ball += 1
                        
                    if arr1[z][1] != strike or arr1[z][2] != ball:
                        flag = True

                if flag == False:
                    result += 1
print(result)
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
KOI 2008 지역본선 초등부 3번