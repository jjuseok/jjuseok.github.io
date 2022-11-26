---
layout: post
title: '[ALGORITHM_JOBS] 24. rook'
date: '2022-11-26 08:59:10 +0900'
description: 'rook'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.3]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
체스에서 룩이라는 기물은 막혀있지만 않으면 룩의 위치에서 같은 행, 같은 열에 해당하는 칸 중 하나로 한 번 이동할 수 있다. 단, 특정 칸이 막혀있다면 그 칸에서부터 더 나아갈 수는 없다. 만약 룩이 아래 그림과 같이 5행 4열에 존재하고 같은 행열에 기물이 없다면 5행이나 4열에 존재하는 칸 중 어디로든 갈 수 있다. 예를 들어, 5행 2열 혹은 1행 4열로 움직일 수 있다. 차례에 주어진 이동 횟수는 한 번이므로 이동이 완료되었다면 상대방의 차례로 넘어간다.<br>
<img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/rook.jpg" alt="표사진"><br>
체스는 킹만 잡히면 지게 되는 게임이다. 그 중에서도 알랩이는 룩으로 인해 게임을 지는 것을 극도로 싫어한다!<br>

주어진 체스판의 상태에서 현재 차례가 상대의 차례일 때, 이번 차례에 알랩이의 킹이 상대방의 룩에게 잡힐 가능성이 있는지 알아보자.
<hr>
# <b>입력</b>
8줄에 걸쳐 8x8 체스판의 상태가 주어진다. 이때 0은 기물이 없는 상태이고, 1은 알랩이의 킹을 의미하고, 2는 상대의 룩을 의미하며 3은 그 외 다른 기물들을 의미한다. (킹은 하나만 존재하며, 상대의 룩은 최대 2개까지 있을 수 있다. 그 외 기물들은 최대 29개까지 있을 수 있다.)
<hr>
# <b>출력</b>
킹이 룩에게 잡힐 가능성이 있으면 1, 아니면 0을 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
0 3 0 0 0 0 0 0
3 1 0 0 0 0 2 0
0 3 0 0 0 0 0 0
0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0
0 0 0 0 0 0 0 0
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
1
</pre>
<hr>
# <b>아이디어</b>
문제를 풀기 전에 아래와 같이 몇가지 상황을 생각해봤다.<br>

Q. 상대의 룩이 최대 2개이며 이를 어떻게 구분할 것인가?<br>
A. list와 sum함수, filter을 활용해서 2개의 룩을 구분했다.<br>

Q. 룩을 확인했으면 상하좌우는 어떻게 확인할 것인가?<br>
A. list좌표를 (x,y)로 활용하고 상 : (x-1,y) 하 : (x+1,y) 좌 : (x,y-1) 우 : (x,y+1)로 구현했다.<br>

Q. 상하좌우를 구현했으면 킹(1), 룩(2), 기물(3)을 어떻게 구분할 것인가?<br>
A. z라는 변수를 만들어 킹(1)과 기물(3) 을 만나면 1을 넣고 break를 한 뒤, 최종적으로 z의 값을 출력했다.<br>

코드 설명을 하면 첫 for문은 len(a)이고 len(a)는 룩(2)의 개수를 의미한다.
룩의 x, y 좌표 구하는 것은 간단하게 몫과 나머지로 구현하고 위에서 말한 방법으로 상, 하, 좌, 우를 구현한 뒤 
킹(1), 기물(3)을 만나면 z = 0을 넣고 break 하는 방법으로 구현했다.
중간에 if z == 1을 넣은 이유는 z가 1이면 더이상 볼 필요가 없기 때문이다.

<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
arr = [list(map(int, input().split())) for _ in range(8)]
arr1 = sum(arr,[])
a = list(filter(lambda e:arr1[e] == 2, range(len(arr1))))

z = 0

for k in range(len(a)):
    x = a[k] // 8
    y = a[k] - 8 * x

    #상
    tmpX = x
    for i in range(x):
        tmpX -= 1
        if arr[tmpX][y] == 1:
            z = 1
            break
        elif arr[tmpX][y] == 3:
            break
    if z == 1:
        break
    #하
    tmpX = x
    for i in range(7-x):
        tmpX += 1
        if arr[tmpX][y] == 1:
            z = 1
            break
        elif arr[tmpX][y] == 3:
            break
    if z == 1:
        break
    #좌
    tmpY = y
    for i in range(y):
        tmpY -= 1
        if arr[x][tmpY] == 1:
            z = 1
            break
        elif arr[x][tmpY] == 3:
            break
    if z == 1:
        break

    #우
    tmpY = y
    for i in range(7-y):
        tmpY += 1
        if arr[x][tmpY] == 1:
            z = 1
            break
        elif arr[x][tmpY] == 3:
            break
    if z == 1:
        break
print(z)
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
KOI 2014 전국본선 초등부 1번  
