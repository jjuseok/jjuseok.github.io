---
layout: post
title: '[ALGORITHM_JOBS] 8. 세 개의 숫자 중 최댓값 찾기'
date: '2022-10-30 08:59:10 +0900'
description: '세 개의 숫자 중 최댓값 찾기.'
categories: [ALGORITHM_JOBS,part.1]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
3 개의 정수가 주어질 때, 이 중 최댓값을 찾는 프로그램을 작성하여라.
<hr>
# <b>입력</b>
첫째 줄에 3개의 정수a,b,c 가 주어진다. (0≤a,b,c≤10,000)
<hr>
# <b>출력</b>
첫째 줄에 a,b,c 중 최댓값을 출력한다.
<hr>
# <b>아이디어</b>
arr에 3개의 정수 a, b, c를 입력받고<br>
python 리스트 정렬 함수인 sort()를 이용해 정렬 한 뒤<Br>
arr 리스트의 3번째 요소를 출력하면 된다.
<hr>
# <b>코드</b>
~~~python
arr = list(map(int, input().split()))
arr.sort()
print(arr[2])
~~~

