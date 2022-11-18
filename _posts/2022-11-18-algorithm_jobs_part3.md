---
layout: post
title: '[ALGORITHM_JOBS] 18. 완전탐색'
date: '2022-11-18 05:59:10 +0900'
description: '완전탐색'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.3]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
## <b>완전탐색(Exhaustive Search)</b>
### <b>완전탐색이란?</b>
👉 가능한 방법을 전부 만들어 시도해보는 알고리즘을 의미한다.<br>
👉 컴퓨터의 빠른 계산 속도를 잘 이용하는 방법이다.
### <b>예시</b>
<img src="/assets/img/1/door.PNG" width="700px">

<b>위와 같이 문이 3개가 있고 가운데 문에 보물이 숨겨져있다고 가정해보자.(여기서 우리는 보물의 위치를 모른다)<br>
이때 보물을 찾을 수 있는 방법은 문을 하나씩 열어보는 방법이다.<br>
이렇게 가능한 방법을 전부 시도해 보는 방법이 완전탐색이다.</b>
<hr>
# <b>완전탐색 문제</b>
1 ~ N까지의 숫자들 중에서 약수의 개수가 홀수인 숫자들의 개수를 출력하는 프로그램을 작성하여라.
<hr>
# <b>입력</b>
10
<hr>
# <b>출력</b>
3
<hr>
# <b>아이디어</b>
완전 탐색을 통해 문제를 풀었다.<br>
n을 입력받고 1 ~ n까지 for 문을 돌려서 약수의 개수를 구했다.<br>
약수를 구하는 방식은 1 ~ i + 1까지 for문을 돌리고 약수이면 count 변수에 1씩 증가했다.<br>
약수의 개수가 홀수인 것은 count가 홀수를 의미하므로 count가 홀수이면 resultCount에 1씩 누적시켰다.<br>
최종적으로 홀수 숫자들의 누적인 resultCount를 출력했다.
<hr>
# <b>코드</b>
<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
n = int(input())
resultCount = 0
for i in range(1, n + 1):
    count = 0
    for j in range(1, i+1):
        if i % j == 0:
            count += 1
    if count % 2 != 0:
        resultCount += 1
print(resultCount)
~~~
</div>
</details>