---
layout: post
title: '[ALGORITHM_JOBS] 32. nextnum'
date: '2023-01-03 08:30:10 +0900'
description: 'nextnum'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.5]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
위키피디아에 따르면 등차수열 AP는 연속되는 두 숫자의 차가 같은 숫자들이 연속되는 수열이다. 예를 들어, 수열 3,5,7,9,11,13…. 은 공차(연속된 숫자의 차이) 2를 가지는 등차수열이다. 이 문제에서 공차는 0이 아닌 정수이다.

등비수열 GP는 이전의 숫자에 0이 아닌 공비(연속된 숫자의 비율)를 곱하여 구하는 수열이다. 예를 들어 수열 2,6,18,54 는 공비가 3인 등비수열이다. 이 문제에서 공비는 0이 아닌 정수이다. 수열을 구성하는 세 개의 숫자가 주어졌을 때, 주어진 수열이 등차 수열인지 등비수열인지를 결정하고, 다음에 연속될 숫자를 결정하는 프로그램을 작성하시오.
<hr>
# <b>입력</b>
입력은 여러 개의 테스트 케이스로 이루어져 있다.

- 각각의 케이스는 3개의 정수 a1, a2, a3가 한줄로 주어질 것이다. (−10, 000 < a1, a2, a3 < 10, 000)
- a1, a2, a3는 각각 다르다.
- 마지막 테스트 케이스는 세 개의 0으로 주어진다.
<hr>
# <b>출력</b>
각 테스트케이스마다 한 줄씩 결과를 출력한다. 형태 : XX v (XX는 주어진 수열이 등차수열이면 ‘AP’ 이고 등비수열이면 ‘GP’이다. v는 수열 다음에 오는 상수이다. ) 모든 입력 케이스는 등비수열 또는 등차수열임이 보장되어 있다.
<pre>
XX V
</pre>
XX부분은 AP 또는 GP로 주어진 수들이 등차수열을 이룰 경우 AP를, 등비수열을 이룰 경우 GP를 출력한다. V는 주어진 수들 다음에 나올 수이다. 모든 입력은 항상 등차수열이나 등비수열이다.
<hr>
# <b>예제 입력</b><br>
<pre>
4 7 10
2 6 18
0 0 0
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
AP 13
GP 54
</pre>
<hr>
# <b>아이디어</b>
처음에 세 수를 입력을 받고 등차수열인지 등비수열인지 마지막 테스트 케이스인 세 개의 0인지 구별해야 된다.
간단하게 등차 수열은 연속되는 두 숫자의 차가 같으면 등차수열이고, 두 숫자의 나누기 몫의 값이 같으면 등비수열이다.
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
while True:
    a, b, c = map(int, input().split())
    tempA, tempB = b - a, c - b
    if a == b == c: break
    if tempA == tempB:
        nextNum = c + tempA
        print('AP', nextNum)
    elif b // a and c // b:
        nextNum = c * (b//a)
        print('GP', nextNum)
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
2010 Arab Collegiate Programming Contest A번
