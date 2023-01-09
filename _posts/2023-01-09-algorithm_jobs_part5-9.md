---
layout: post
title: '[ALGORITHM_JOBS] 38. findprime'
date: '2023-01-09 08:50:10 +0900'
description: 'findprime'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.5]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
주어진 숫자들 중 소수가 몇 개인지 찾아서 출력하는 프로그램을 작성하시오.

<hr>
# <b>입력</b>
첫 줄에 수의 개수 N이 주어진다. N은 100이하이다. 다음으로 N개의 줄에 걸쳐 N개의 수가 주어지는데 수는 1,000 이하의 자연수이다.
<hr>
# <b>출력</b>
주어진 수들 중 소수의 개수를 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
4
1
3
5
7
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
3
</pre>
<hr>
# <b>아이디어</b>
이 문제는 소수의 정의만 알면 쉽게 풀 수 있는 문제이다. 소수란 1보다 큰 자연수 중 1과 자기 자신만을 약수로 가는 수이다. 코드 중에 primeNumber 함수를 간단하게 설명하면 소수는 1보다 큰 자연수이기 때문에 if문을 통해 걸러낸 다음 소수를 판별하는 for문을 구현했다. for문의 범위에 제곱근(math.sqrt)이 사용되는 이유는 예를 들어 숫자 8을 소수 판별한다고 가정해 보자. 1과 자기 자신을 제외하고 2 ~ 7까지는 약수로 가지면 안된다. 이 말인 즉슨 2 ~ 7 사이의 수가 8과 나누어 떨어지면 소수가 아니다. 하지만 2 ~ 7 범위에 수중 2, 4는 8과 나누어 떨어진다. 따라서 8은 소수가 아니다. 여기서 8의 약수는 1 2 4 8이다. 여기서 8의 제곱근의 범위를 보자. 8의 제곱근은 약 2.828427.....이다.
<br>따라서 약수에 포함시키면 8의 약수는 1 2 <span style="background-color:yellow;">&radic;8 </span> 4 8 이다. 여기서 중요한점은 약수는 서로 대칭이며 꼭 2,3,4,5,6,7 다 비교해보지 않고 &radic;8까지만 비교해도 소수를 판별할 수 있고 시간도 절약할 수 있다. 이에 따라서 for문의 범위가 2 ~ 8이 아닌 2 ~ &radic;8이다.

<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
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


n = int(input())
count = 0
for i in range(n):
    k = int(input())
    if primeNumber(k):
        count += 1

print(count)
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
ALGORITHM JOBS