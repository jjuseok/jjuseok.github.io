---
layout: post
title: '[ALGORITHM_JOBS] 6. 배수의 개수 세기'
date: '2022-10-29 09:59:10 +0900'
description: '배수의 개수 세기.'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.1]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
세 개의 자연수 A, B, C가 주어진다. 이 때, A부터 B까지 숫자 중에서 C의 배수의 개수를 출력하는 프로그램을 작성하시오.<br>

예를 들어, A = 3, B = 9, C = 2 라고 하자. 그러면 3부터 9까지 숫자 중 2의 배수의 개수이므로 4, 6, 8 총 3개가 존재한다. 따라서 3을 출력한다.<br>

또한, A = 10, B = 3, C = 4라고 하자. 그러면 10에서 3까지 숫자 중 4의 배수의 개수이므로 4, 8 총 2개가 존재한다. 따라서 2를 출력한다.<br>
<hr>
# <b>입력</b>
첫 번째 줄에 A, B, C가 주어진다. (1 <= A, B, C <= 1000)
<hr>
# <b>출력</b>
A부터 B까지 숫자 중에서 C의 배수의 개수를 출력한다.
<hr>
# <b>아이디어</b>
a, b, c를 입력 받는데 a가 b보다 클수도 있고, 작을수도 있다.<br>
그래서 if 문을 사용해서 a가 b보다 크면 a와 b의 값을 서로 바꾼다.<br>
바꾸고 나서 for문을 이용해 c의 배수를 찾고 count에 누적시키기고 마지막에 count를 출력한다.
<hr>
# <b>코드</b>
~~~python
a, b, c = map(int, input().split())
count, temp = 0, 0

if a > b:
    temp = a
    a = b
    b = temp

for i in range(a, b+1):
    if i % c == 0:
        count += 1

print(count)
~~~

