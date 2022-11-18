---
layout: post
title: '[ALGORITHM_JOBS] 7. N to M 2'
date: '2022-10-29 09:59:10 +0900'
description: 'N to M 2.'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.1]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
N부터 M까지 출력하는 프로그램을 작성해보자.
<hr>
# <b>입력</b>
첫째 줄에 자연수 N과 자연수 M이 공백을 가지고 주어진다. (N ≤ M ≤ 1,000)
<hr>
# <b>출력</b>
첫째 줄에 N부터 M까지의 자연수를 공백을 사이에 두고 차례대로 출력한다. (단, 한 줄에 최대 8개씩 출력해야 한다.)
<hr>
# <b>아이디어</b>
a, b를 입력받고 차례대로 출력하면 된다.<br>
한 줄에 최대 8개까지 출력 가능하니깐, count 변수를 새로 만들고 8개가 되면 줄바꿈을 한다.
<hr>
# <b>코드</b>
<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">


~~~python
a, b = map(int, input().split())
count = 0

for i in range(a, b+1):
    count += 1
    print(i,end=" ")
    if  count % 8 == 0:
        print()
~~~
</div>
</details>
