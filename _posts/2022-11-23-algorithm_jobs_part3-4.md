---
layout: post
title: '[ALGORITHM_JOBS] 22. attackrange'
date: '2022-11-23 08:59:10 +0900'
description: 'attackrange'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.3]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
윤성이는 어렸을 적부터 수없이 몰려오는 적으로부터 기지를 방어하는 디펜스 유형의 게임을 플레이하는 것을 좋아했다. 그래서 간단한 디펜스 게임을 만들어 보려고 한다.

당신은 윤성이를 도와, 디펜스 게임 내에서 플레이어가 설치하는 유닛의 사거리를 나타내는 기능을 구현하면 된다.
<hr>
# <b>입력</b>
입력 첫째 줄에는 디펜스 게임의 맵 크기 N이 주어딘다. 맵은 N×N 크기의 2차원 형태이다. (N은 6이상 100이하의 짝수)

둘째 줄에는 유닛이 설치될 위치 X, Y와 유닛의 사거리 R이 주어진다. X는 행의 번호, Y는 열의 번호를 의미한다.<br>(X, Y는 1이상 N이하의 자연수, R은 N/2이하의 자연수)
<hr>
# <b>출력</b>
예제 출력과 같이 유닛의 사거리를 나타내어 출력한다. (유닛의 사거리가 아무리 길어도 맵을 벗어날 수는 없다.)
<hr>
# <b>예제 입력</b><br>
<pre>
6
2 3 3
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
3 2 1 2 3 0
2 1 x 1 2 3
3 2 1 2 3 0
0 3 2 3 0 0
0 0 3 0 0 0
0 0 0 0 0 0
</pre>
<hr>
# <b>아이디어</b>
<img src="/assets/img/1/attackrange1.png" alt="표사진"><br>
이 사진도 2차원 배열을 이용해 풀 거라서 표를 이용해 봤다.<br>
표를 간단히 설명하자면 좌표는 2차원 배열 기준으로 했고, 거리마다 색상을 다르게 칠했다.<br>
이 표를 보면서 생각한 방법은 완전탐색(하나씩 다 확인하는 방식)을 이용해서 풀 방법을 고민했다.<br>
(0,0)과 x좌표(1,2)의 거리는 3이다. 이 거리를 푸는 방법은 x좌표끼리 빼고, y 좌표끼리 빼고 더하면 된다.<br>
나는 여기서 음수가 나올 경우 abs(절대값) 함수를 사용했고 다른 방법으로는 if문을 여러개 이용해서 음수가 안나오게 하는 것이다. 두가지 방법으로 풀어볼 것이다.

거리 구하는 방법을 자세하게 설명하면 만약에 (0,1)좌표의 거리를 구한다고 가정해 보자<br>
x 좌표는 (1,2) 이므로 x끼리 빼고 절대값 => abs(0-1) y끼리 빼고 절대값 => abs(1-2) 한 뒤 둘이 더하면 2가 나온다.<br>
따라서 (0,1)의 값은 2이다. 거리 구하는 방법을 알았으면 이 문제를 다 푼 거나 다름없다.<br>
코드에서 x -= 1과 y -= 1을 해주는 것은 python list가 0부터 시작하기  때문이다.<br>
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
n = int(input())
arr1 = [[0] * n for _ in range(n)]
x, y, r = map(int, input().split())
distance = 0
x -= 1
y -= 1
for i in range(n):
    for j in range(n):
        if i == x  and j == y:
            print('x',end=" ")
        else:
            distance = abs((i-x)) + abs((j-y))
            if distance > r:
                distance = 0
            print(distance,end=" ")
            distance = 0
    print()
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
ALGORITHM JOBS