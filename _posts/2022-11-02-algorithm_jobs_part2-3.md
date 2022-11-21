---
layout: post
title: '[ALGORITHM_JOBS] 12. 소수 판별 2'
date: '2022-11-02 08:59:10 +0900'
description: '소수 판별 2.'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.2]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
n층의 삼각형을 출력하는 프로그램을 작성하여라. Input, Output의 예제를 자연수n,m이 주어질 때, n부터m까지 존재하는 소수를 모두 출력하는 프로그램을 작성하여라. 여기서 소수란, 약수가 1과 자기자신밖에 존재하지 않는 수를 말한다.
<hr>
# <b>입력</b>
첫째 줄에 자연수 n, m이 주어진다. (1≤n,m≤20,000)
<hr>
# <b>출력</b>
첫째 줄에 n부터m까지 존재하는 소수를 모두 출력한다.
<hr>
# <b>아이디어</b>
primenumber이라는 함수를 만들어 소수 판별하는 함수를 작성했다. | 참고 → <b style="font-size:20px">[소수판별 문제](https://jjuseok.github.io/posts/algorithm_jobs_part1-4/)</b><br>
함수를 만들고 n, m을 입력받고 소수인 정수만 출력했다.
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

n, m = map(int, input().split())
for i in range(n, m+1):
    if primenumber(i) == True and i != 1:
        print(i,end=" ")
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
ALGORITHM JOBS