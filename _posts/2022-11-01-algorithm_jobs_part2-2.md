---
layout: post
title: '[ALGORITHM_JOBS] 11. 삼각형 출력 3'
date: '2022-11-01 08:59:10 +0900'
description: '삼각형 출력 3.'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.2]
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
다음 예제와 같이 삼각형 모양으로 ‘*’을 출력한다.(공백의 개수와 별의 개수를 정확하게 확인해주시바랍니다.)
<hr>
# <b>예제 입력</b><br>
3
<hr>
# <b>예제 출력</b><br>
&nbsp;&nbsp;&#42;<br>
&nbsp;&#42;&#42;<br>
&#42;&#42;&#42;
<hr>
# <b>아이디어</b>
n을 입력받은 후 공백을 n-i개 출력 후 별을 (2*i-1)개 찍으면 된다.
<hr>
# <b>코드</b>
<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
n = int(input())
for i in range(1, n+1):
    print(' ' * (n-i)+'*' * (2*i-1))
~~~
</div>
</details>
