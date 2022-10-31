---
layout: post
title: '[ALGORITHM_JOBS] 3. 짝수의 합 구하기'
date: '2022-10-27 09:59:10 +0900'
description: '짝수의 합 구하기.'
categories: [ALGORITHM_JOBS,part.1]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
1부터 N까지의 숫자 중 짝수의 합을 구하는 프로그램을 작성하여라.
<hr>
# <b>입력</b>
첫째 줄에 N이 주어진다. (1 <= N <= 2000)
<hr>
# <b>출력</b>
1부터 N까지의 숫자 중 짝수의 합을 출력한다.
<hr>
# <b>아이디어</b>
짝수의 합을 구하면 되는 문제다.<br>
반복문을 2부터 돌리는 이유는 1은 홀수니깐 2부터 돌린다.<br>
만약 i가 짝수면 합을 su에 저장한다.
<hr>
# <b>코드</b>
<hr>
~~~python
n = int(input())
su = 0
for i in range(2, n+1):
    if i % 2 == 0:
        su += i

print(su)
~~~