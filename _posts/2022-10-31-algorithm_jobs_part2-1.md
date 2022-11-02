---
layout: post
title: '[ALGORITHM_JOBS] 10. 삼각형 출력 1'
date: '2022-10-31 08:59:10 +0900'
description: '세 개의 숫자 중 최댓값 찾기.'
categories: [ALGORITHM_JOBS,part.2]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
n층의 삼각형을 출력하는 프로그램을 작성하여라. Input, Output의 예제를 참고한다.
<hr>
# <b>입력</b>
첫째 줄에 정수n이 주어진다. (0≤n≤100)
<hr>
# <b>출력</b>
다음 예제와 같이 삼각형 모양으로 ‘*’을 출력한다.
<hr>
# <b>예제 입력</b><br>
3
<hr>
# <b>예제 출력</b><br>
&#42;<br>
&#42;&#42;<br>
&#42;&#42;&#42;
<hr>
# <b>아이디어</b>
n을 입력받은 후 n층마다 n개의 별을 출력하면 된다.
<hr>
# <b>코드</b>
~~~python
n = int(input())
for i in range(n):
    print('*' * (i+1))
~~~
