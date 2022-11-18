---
layout: post
title: '[ALGORITHM_JOBS] 4. 소수 판별'
date: '2022-10-28 09:59:10 +0900'
description: '소수 판별하기.'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.1]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
자연수n이 주어질 때, n 이 소수인지 판별하는 프로그램을 작성하여라. 여기서 소수란, 약수가 1과 자기자신밖에 존재하지 않는 수를 말한다.
<hr>
# <b>입력</b>
첫째 줄에 자연수 n이 주어진다. (2≤n≤20,000)
<hr>
# <b>출력</b>
첫째 줄에 n이 소수이면 YES, 소수가 아니면 NO를 출력한다.
<hr>
# <b>아이디어</b>
소수를 판별하는 방식으로는 입력받은 수의 제곱근(루트)를 활용하여 구한다.<br>
예를 들어 입력받은 수가 16이면 2 ~ 16을 확인하지 말고 16의 루트 = 4를 활용한다.<br>
그러면 반복문을 2 ~ 16 다 돌리지 말고 2 ~ 4까지만 돌리면 소수를 판별할 수 있다.<br>
이렇게 루트를 활용할 수 있는 이유를 아래와 같이 살펴보자.<br>
ex) 16이 소수인가 소수가 아닌가?<br>
1 * 16<br>
2 * 8<br>
4 * 4<br>
8 * 2<br>
16 * 1<br>
사람은 일반적으로 이렇게 소수를 판별한다.<br> 하지만 잘 살펴보면 약수들이 대칭을 이루어 입력받은 수의 제곱근<br>
즉 16의 제곱근 4까지만 확인하면 소수를 판별할 수 있다.

<hr>
# <b>코드</b>
<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
import math

def primenumber(x):
    for i in range(2, int(math.sqrt(x)) + 1):
        if x % i == 0:
            return False
    return True

n = int(input())
if primenumber(n) == True:
    print("YES")
else:
    print("NO")
~~~
</div>
</details>