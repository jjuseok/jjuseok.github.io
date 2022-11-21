---
layout: post
title: '[ALGORITHM_JOBS] 1. 짝수 판별하기'
date: '2022-10-24 09:59:10 +0900'
description: '짝수 판별하기.'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.1]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
정수 N을 입력받고, N이 짝수인지 아닌지 판별하는 프로그램을 작성해보자. (단, if문과 else문 모두 사용할 것)
<hr>
# <b>입력</b>
첫째 줄에 자연수 N이 주어진다.
<hr>
# <b>출력</b>
첫째 줄에 N이 짝수라면 “even”, N이 짝수가 아니라면 “not even"를 출력한다.
<hr>
# <b>아이디어</b>
기본적인 문제로 if-else문을 사용하여 풀이하면 된다.
<hr>
# <b>코드</b>
<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
n = int(input()) # n을 정수로 입력 받는다.
if n % 2 == 0: # 만약에 n % 2 가 0 이라면 
    print("even") # "even"을 출력하고 
else: # n % 2 가 0이 아니면
    print("not even") # "not even"이 출력 된다.
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
ALGORITHM JOBS