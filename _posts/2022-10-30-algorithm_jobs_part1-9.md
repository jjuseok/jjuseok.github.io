---
layout: post
title: '[ALGORITHM_JOBS] 9. 제곱근 구하기'
date: '2022-10-30 08:59:10 +0900'
description: '세 개의 숫자 중 최댓값 찾기.'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - <b>Part.1</b>]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
N이 주어질 때, 제곱하여 N보다 크거나 같은 숫자들 중 최솟값을 출력하는 프로그램을 작성하시오.<br>

예를 들어, N = 10 이라고 하자. 그러면 s=3 일 경우 3 x 3 = 9 이므로 10보다 크거나 같지 않다. s=4일 경우, 4 x 4 = 16 이므로 10보다 크거나 같다. s=5일 경우, 5 x 5 = 25 이므로<br>10보다 크거나 같다. 즉, s = 4, 5, 6, ..., 의 숫자들은 모두 제곱하면 10보다 크거나 같다. 이 중 최솟값은 4이므로, 4를 출력한다.<br>
<hr>
# <b>입력</b>
첫 번째 줄에 N이 주어진다. (1 <= N <= 10000)
<hr>
# <b>출력</b>
제곱하여 N보다 크거나 같은 숫자들 중 최솟값을 출력한다.
<hr>
# <b>아이디어</b>
n, s를 입력받는데 s는 math 함수를 이용해 제곱근으로 변환한다.<br>
변환하고 나서 s의 제곱이 n보다 크거나 같으면 출력하고 아니면 +1을 해서 출력한다.
<hr>
# <b>코드</b>
~~~python
import math
n = int(input())
s = int(math.sqrt(n))
print(s if s**2 >= n else (s+1))
~~~

