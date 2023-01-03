---
layout: post
title: '[ALGORITHM_JOBS] 33. beehive'
date: '2023-01-03 08:30:10 +0900'
description: 'beehive'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.5]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
<img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/beehive.png" alt="표사진"><br>
위의 그림과 같이 육각형으로 이루어진 벌집이 있다. 그림에서 보는 바와 같이 중앙의 방 1부터 시작해서 이웃하는 방에 돌아가면서 1씩 증가하는 번호를 주소로 매길 수 있다.

숫자 N이 주어졌을 때, 벌집의 중앙 1에서 N번 방까지 최소 개수의 방을 지나서 갈 때 몇 개의 방을 지나가는지(시작과 끝을 포함하여)를 계산하는 프로그램을 작성하시오. 예를 들면, 13까지는 3개, 58까지는 5개를 지난다.
<hr>
# <b>입력</b>
첫째 줄에 N(1 ≤ N ≤ 1,000,000)이 주어진다.
<hr>
# <b>출력</b>
입력으로 주어진 방까지 최소 개수의 방을 지나서 갈 때 몇 개의 방을 지나는지 출력한다.  
<hr>
# <b>예제 입력</b><br>
<pre>
58
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
5
</pre>
<hr>
# <b>아이디어</b>
이 문제는 생긴거와(?)는 다르게 간단한 문제이다. 벌집은 6각형으로 되어 있으니깐 벌집의 개수가 6개씩 증가한다.
<img src="/assets/img/1/beehive.png" alt="표사진"><br>
위 그림과 같이 증가하는 값이 6씩 증가하는 것을 볼 수 있다. 방 번호는 시작과 끝 번호를 포함하니 2 ~ 7 사이 값은 2개의 방, 8 ~ 19 사이 값은 3개의 방, 20 ~ 37 사이 값은 4개의 방..... 을 지나 가는것을 알 수 있다. 따라서 위와 같은 규칙을 바탕으로 코드를 작성했다.
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
num = int(input())
start = 1
count = 1

while (start < num):
    start += 6 * count
    count += 1

print(count)
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
ACM-ICPC Daejeon Nationalwide Internet Competition 2004 B번  
