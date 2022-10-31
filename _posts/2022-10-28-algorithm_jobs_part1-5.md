---
layout: post
title: '[ALGORITHM_JOBS] 5. 약수 구하기'
date: '2022-10-28 09:59:10 +0900'
description: '약수 구하기.'
categories: [ALGORITHM_JOBS,part.1]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
어떤 자연수 p와 q가 있을 때, 만일 p를 q로 나누었을 때 나머지가 0이면 q는 p의 약수이다.<br>6을 예로 들면

6 ÷ 1 = 6 … 0<br>
6 ÷ 2 = 3 … 0<br>
6 ÷ 3 = 2 … 0<br>
6 ÷ 4 = 1 … 2<br>
6 ÷ 5 = 1 … 1<br>
6 ÷ 6 = 1 … 0<br>

그래서 6의 약수는 1, 2, 3, 6, 총 네 개이다.<br>두 개의 자연수 N과 K가 주어졌을 때, N의 약수들 중 K번째로 작은 수를 출력하는 프로그램을 작성하시오.
<hr>
# <b>입력</b>
첫째 줄에 N과 K가 빈칸을 사이에 두고 주어진다. N은 1 이상 10,000 이하이다. K는 1 이상 N 이하이다.
<hr>
# <b>출력</b>
첫째 줄에 N의 약수들 중 K번째로 작은 수를 출력한다. 만일 N의 약수의 개수가 K개보다 적어서 K번째 약수가 존재하지 않을 경우에는 0을 출력하시오.
<hr>
# <b>아이디어(1)</b>
k번째로 작은 약수를 구하려면 일단 약수들을 저장해야 된다.<br>
for문을 이용해서 약수면 arr 리스트에 하나씩 저장한다.<br>
그런후 arr리스트에서 k번째를 출력한다.
# <b>코드(1)</b>
~~~python
n, k = map(int, input().split())
arr = []
for i in range(1, n + 1):
    if n % i == 0:
        arr.append(i)

if len(arr) < k:
    print(0)
else:
    print(arr[k-1])
~~~
<hr>
# <b>아이디어(2)</b>
아이디어(1)로 작성한 코드보다 길이가 적은 코드를 고안했다.<br>
구하는 방식은 똑같다.
# <b>코드(2)</b>
~~~python
a, b = map(int, input().split())
c = [i for i in range(1, a+1) if a%i==0]
print(0 if len(c)<b else c[b-1])
~~~
