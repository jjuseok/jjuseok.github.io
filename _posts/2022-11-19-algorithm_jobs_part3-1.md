---
layout: post
title: '[ALGORITHM_JOBS] 19. maxofarr'
date: '2022-11-19 08:59:10 +0900'
description: 'maxofarr'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.3]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
<그림 1>과 같이 9×9 격자판에 쓰여진 81개의 자연수가 주어질 때, 이들 중 최댓값을 찾고 그 최댓값이 몇 행 몇 열에 위치한 수인지 구하는 프로그램을 작성하시오.<br>

예를 들어, 다음과 같이 81개의 수가 주어지면<br>
<span><img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/maxofarr.png" alt="표사진"></span><br>
이들 중 최댓값은 90이고, 이 값은 5행 7열에 위치한다.
<hr>
# <b>입력</b>
첫째 줄부터 아홉 번째 줄까지 한 줄에 아홉 개씩 자연수가 주어진다. 주어지는 자연수는 100보다 작다.
<hr>
# <b>출력</b>
첫째 줄에 최댓값을 출력하고, 둘째 줄에 최댓값이 위치한 행 번호와 열 번호를 빈칸을 사이에 두고 차례로 출력한다.<br>
최댓값이 두 개 이상인 경우 그 중 행의 번호가 가장 작은 곳의 위치를 출력한다.<br>
행 번호도 같은 곳이 여러개일 경우에는 열 번호가 가장 작은 곳의 위치를 출력한다.<br>
<hr>
# <b>예제 입력</b><br>
<pre>
3 23 85 34 17 74 25 52 65
10 7 39 42 88 52 14 72 63
87 42 18 78 53 45 18 84 53
34 28 64 85 12 16 75 36 55
21 77 45 35 28 75 90 76 1
25 87 65 15 28 11 37 28 74
65 27 75 41 7 89 78 64 39
47 47 70 45 23 65 3 41 44
87 13 82 38 31 12 29 29 80
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
90
5 7
</pre>
<hr>
# <b>아이디어</b>
2차원 배열로 입력을 받은 뒤 완전 탐색으로 하나씩 리스트 모든 요소에 접근해서 최댓값을 찾는다.<br>
비교를 할 때 큰 값이 들어오면 maxSu에 저장하고 요소의 위치도 line, low 변수에 저장한다.<br>
2중 for문이 끝난 것은 모든 요소에 접근하여 비교한 것이므로 maxSu와 line, low를 출력한다.
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
arr1 = [list(map(int, input().split())) for _ in range(9)]
maxSu, line, low = 0, 0, 0
for i in range(9):
    for j in range(9):
        if arr1[i][j] > maxSu:
            maxSu = arr1[i][j]
            line = i + 1
            low = j + 1
print(f"{maxSu}\n{line} {low}")
~~~
</div>
</details>
