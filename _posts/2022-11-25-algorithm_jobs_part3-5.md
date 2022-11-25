---
layout: post
title: '[ALGORITHM_JOBS] 23. colorpaper'
date: '2022-11-25 08:59:10 +0900'
description: 'colorpaper'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.3]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
평면에 색깔이 서로 다른 직사각형 모양의 색종이 N장이 하나씩 차례로 놓여진다. 이 때 색종이가 비스듬하게 놓이는 경우는 없다. 
즉, 모든 색종이의 변은 서로 평행하거나, 서로 수직이거나 둘 중 하나이다. 그림-1은 1번, 2번, 3번 세 장의 색종이가 순서대로 놓인 상태를 보여준다.<br>
<img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/colorpaper-1.jpg" alt="표사진"><br>
여기에 그림-2에서 보인 것처럼 4번 색종이가 하나 더 놓이면 3번 색종이는 완전히 가려서 보이지 않게 된다. 그리고, 1번 색종이와 2번 색종이는 부분적으로 가려 보이며, 4번 색종이는 완전히 보이게 된다.<br>
<img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/colorpaper-2.jpg" alt="표사진"><br>
<hr>
# <b>입력</b>
입력의 첫 번째 줄에는 색종이의 장수를 나타내는 정수 N (1 ≤ N ≤ 100)이 주어진다. 이어서 N장의 색종이에 관한 입력이 각 색종이마다 한 줄씩 차례로 주어진다. 색종이가 놓이는 평면은 가로 최대 101칸, 세로 최대 101칸으로 구성된 격자 모양이다. 격자의 각 칸은 가로, 세로 길이가 1인 면적이 1인 정사각형이다.

편의상 가로 6칸, 세로 6칸으로 이루어진 격자의 예를 들어 설명하면, 각 칸에 표시된 값 (a,b)는 해당 칸의 번호를 나타낸다. 가장 왼쪽 아래의 칸은 (0,0) 가장 오른 쪽 위의 칸은 (5,5)이다.<br>
<img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/colorpaper-3.png" alt="표사진"><br>
색종이가 놓인 상태는 가장 왼쪽 아래 칸의 번호와 너비, 높이를 나타내는 네 정수로 표현한다. 예를 들어, 위 그림에서 회색으로 표시된 색종이는 (1,4)가 가장 왼쪽 아래에 있고 너비 3, 높이 2이므로 1 4 3 2로 표현한다. 색종이가 격자 경계 밖으로 나가는 경우는 없다.
<hr>
# <b>출력</b>
입력에서 주어진 순서에 따라 N장의 색종이를 평면에 놓았을 때, 입력에서 주어진 순서대로 각 색종이가 보이는 부분의 면적을 한 줄에 하나씩 하나의 정수로 출력한다. 만약 색종이가 보이지 않는다면 정수 0을 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
2
0 0 10 10
2 2 6 6
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
64
36
</pre>
<hr>
# <b>아이디어</b>
<img src="/assets/img/1/colorpaper1.png" alt="표사진"><br>
위 표처럼 전체 표가 11 X 11이고 예제를 입력받았다고 가정해 보자.<br>
문제 표에서는 왼쪽 모서리가 (0,0)으로 시작하는데 나는 더욱 쉽게 접근하기 위해서 첫 번째 왼쪽 모서리를 (0,0)으로 잡았다.
 첫 번째 예제 입력에서 0 0 10 10 은 (0,0)에서 가로 10, 세로 10인 사각형 이므로 주황 색깔의 범위이고, 두 번째 예제인 2 2 6 6은 
(2,2)에서 가로 6, 세로 6인 사각형이므로 노랑색 범위이다. 따라서 주황색의 범위는 10*10 - 6*6 = 64 이고, 노랑색의 범위는 36이다.

색칠하는 코드는 3중 for 문을 돌려서 문제를 해결했다. 첫 번째 for문은 예제 입력 개수, 두 번째 for문은 색칠할 세로 범위, 세 번째 for문은 색칠할 가로 범위이다.
색칠할 때 표시를 i + 1로 해서 나중에 넓이를 구할 수 있게 문제를 풀었다.

<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
list = [[0] * 101 for _ in range(101)]
n = int(input())
for i in range(n):
    a, b, c, d = map(int,input().split())
    #a: 가로, b: 세로, c: 가로길어, d: 세로길이
    for j in range(b,b+d):
        for k in range(a,a+c):
            list[j][k] = i + 1

list2 = sum(list,[])

for i in range(n):
    print(list2.count(i+1))
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
KOI 2014 전국본선 초등부 1번  