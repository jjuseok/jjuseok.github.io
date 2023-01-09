---
layout: post
title: '[ALGORITHM_JOBS] 39. chebyshevtheo'
date: '2023-01-09 09:50:10 +0900'
description: 'findprime'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.5]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
베르트랑-체비쇼프 정리는 임의의 자연수 n에 대하여, n보다 크고, 2n보다 작거나 같은 소수는 적어도 하나 존재한다는 내용을 담고 있다.

이 명제는 조제프 베르트랑(Joseph Louis François Bertrand, 1822–1900)이 1845년에 추측했고, 파프누티 체비쇼프(Пафнутий Львович Чебышёв, 1821–1894)가 1850년에 증명했다.

예를 들어, 10보다 크고, 20보다 작거나 같은 소수는 4개가 있다. (11, 13, 17, 19) 또, 14보다 크고, 28보다 작거나 같은 소수는 3개가 있다. (17, 19, 23)

n이 주어졌을 때, n보다 크고, 2n보다 작거나 같은 소수의 개수를 구하는 프로그램을 작성하시오.  
<hr>
# <b>입력</b>
입력은 여러 개의 테스트 케이스로 이루어져 있다. 각 케이스는 n을 포함하며, 한 줄로 이루어져 있다. (n ≤ 123,456)

입력의 마지막에는 0이 주어진다.
<hr>
# <b>출력</b>
각 테스트 케이스에 대해서, n보다 크고, 2n보다 작거나 같은 소수의 개수를 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
1
10
13
100
1000
10000
100000
0
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
1
4
3
21
135
1033
8392
</pre>
<hr>
# <b>아이디어</b>
<a href="https://jjuseok.github.io/posts/algorithm_jobs_part5-9/">38번 findprime 문제를</a> 잘 풀었으면 이번 문제도 쉽게 풀 수 있을 것이다. 문제는 거의 비슷한데 살짝 변형된 문제이다. n이 주어지면 n보다 크고 2 x n 보다 같거나 작은 범위의 수들 중에서의 소수 개수를 구하는 문제이다. 나는 38번 문제에서 코드만 살짝 바꿔서 제출했는데 문제에 맞게 정답이 잘 출력되지만 시간 초과 오류가 발생했다. 따라서 나는 문제에 주어진 범위 2 ~ 246913(123465 x 2)의 소수를 다 구한 다음 조건에 맞는 개수들만 출력하는 방식으로 바꿔서 문제를 풀어 제출하였더니 시간 초과 문제가 발생하지 않고 잘 출력됐다.


<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기 - 시간 초과 코드 (클릭)</summary>
<div markdown="1">

~~~python
import math

def primeNumber(x):
    if x == 1:
        return False
    else:
        for i in range(2, int(math.sqrt(x) + 1)):
            if x % i == 0:
                return False
        return True

while True:
    n = int(input())
    count = 0
    if n == 0:
        break
    else:
        for i in range(n+1, 2*n+1): 
            if primeNumber(i):
                count += 1
        print(count)
~~~
</div>
</details>
<details>
<summary id="summary1">풀이보기 - (정상코드)(클릭)</summary>
<div markdown="1">

~~~python
import math

prime = []

def primeNumber(x):
    if x == 1:
        return False
    else:
        for i in range(2, int(math.sqrt(x) + 1)):
            if x % i == 0:
                return False
        return True


for j in range(2, 246913):
    if primeNumber(j):
        prime.append(j)

while True:
    n = int(input())
    count = 0
    
    if n == 0:
        break
    else:
        for k in prime:
            if n < k <= 2*n:
                count += 1
    print(count)
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
ACM-ICPC Japan 2011 Domestic Contest A번  