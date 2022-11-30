---
layout: post
title: '[ALGORITHM_JOBS] 26. bingo :star:'
date: '2022-11-30 16:30:10 +0900'
description: 'bingo'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.3]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
빙고 게임은 다음과 같은 방식으로 이루어진다.

먼저 아래와 같이 25개의 칸으로 이루어진 빙고판에 1부터 25까지 자연수를 한 칸에 하나씩 쓴다
<img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/bingo1.gif" alt="표사진"><br>

다음은 사회자가 부르는 수를 차례로 지워나간다. 예를 들어 5, 10, 7이 불렸다면 이 세 수를 지운 뒤 빙고판의 모습은 다음과 같다.<br>
<img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/bingo2.gif" alt="표사진"><br>

다음은 사회자가 부르는 수를 차례로 지워나간다. 예를 들어 5, 10, 7이 불렸다면 이 세 수를 지운 뒤 빙고판의 모습은 다음과 같다.<br>
<img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/bingo3.gif" alt="표사진"><br>

이러한 선이 세 개 이상 그어지는 순간 "빙고"라고 외치는데, 가장 먼저 외치는 사람이 게임의 승자가 된다.<br>
<img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/bingo4.gif" alt="표사진"><br>
철수는 친구들과 빙고 게임을 하고 있다. 철수가 빙고판에 쓴 수들과 사회자가 부르는 수의 순서가 주어질 때, 사회자가 몇 번째 수를 부른 후 철수가 "빙고"를 외치게 되는지를 출력하는 프로그램을 작성하시오.
<hr>
# <b>입력</b>
첫째 줄부터 다섯째 줄까지 빙고판에 쓰여진 수가 가장 위 가로줄부터 차례대로 한 줄에 다섯 개씩 빈 칸을 사이에 두고 주어진다. 여섯째 줄부터 열째 줄까지 사회자가 부르는 수가 차례대로 한 줄에 다섯 개씩 빈 칸을 사이에 두고 주어진다. 빙고판에 쓰여진 수와 사회자가 부르는 수는 각각 1부터 25까지의 수가 한 번씩 사용된다.
<hr>
# <b>출력</b>
첫째 줄에 사회자가 몇 번째 수를 부른 후 철수가 "빙고"를 외치게 되는지 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
11 12 2 24 10
16 1 13 3 25
6 20 5 21 17
19 4 8 14 9
22 15 7 23 18
5 10 7 16 2
4 22 8 17 13
3 18 1 6 25
12 19 23 14 21
11 24 9 20 15
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
15
</pre>
<hr>
# <b>아이디어</b>
문제를 풀기 전에 빙고 조건에 대해서 생각해봤다.<br>
빙고가 되기 위한 조건은 아래와 같다.<br>

1. 같은 행의 5개 숫자가 불린 경우.
(0,0) ~ (0,4)<br>
<img src="/assets/img/1/part3-8.png" alt="표사진"><br>
2. 같은 열의 5개 숫자가 불린 경우.
(0,0) ~ (4,0)<br>
<img src="/assets/img/1/part3-8-1.png" alt="표사진"><br>
3. 왼쪽 -> 오른쪽 대각선 5개 숫자가 불린 경우.
(0,0) -> (1,1) ~ (4,4)<br>
<img src="/assets/img/1/part3-8-2.png" alt="표사진"><br>
4. 오른쪽 -> 왼쪽 대각선 5개 숫자가 불린 경우.
(0,5) -> (1,4) ~ (4,0)<br>
<img src="/assets/img/1/part3-8-3.png" alt="표사진"><br>

이렇게 네가지가 있다.

풀이 방법을 간단히 설명하면<br>

1. 내 빙고 숫자와 사회자가 부르는 숫자를 입력받는다.
2. 사회자가 부르는 숫자와 내 숫자를 하나씩 비교한다.(for문이 4개 필요한 이유)
3. 사회자가 하나씩 부를 때마다 order에 1씩 증가시킨다.(마지막에 몇 번짼지 출력하기 위함.)
4. 사회자가 부르는 숫자가 내 빙고에 있으면 0으로 바꾼다.(코딩에서 색칠할 수 없기 때문)
5. 사회자가 하나부르고 내 빙고 비교 후 위에 나와있는 빙고 4가지 경우를 비교해본다.
6. 빙고가 1개 나오면 count 변수에 누적시킨다.
7. 빙고가 3개 즉 count 변수에 3이 들어가면 몇 번짼지 출력하고 코드를 종료 시킨다.




<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
import sys

arr1 = [list(map(int, input().split())) for _ in range(5)]
arr2 = [list(map(int, input().split())) for _ in range(5)]
order = 0

# 사회자가 뽑는 숫자
for i in range(5):
    for j in range(5):
        # 사회자가 뽑는 숫자랑 내 숫자랑 비교
        for k in range(5):
            for l in range(5):
                if arr1[k][l] == arr2[i][j]:
                    arr1[k][l] = 0

        order += 1 # 몇 번째 숫자를 부르는지 저장하는 변수
        count = 0 # 빙고의 수
        
        for z in range(5): # 행의 빙고 확인
            xcnt = 0
            for c in range(5):
                if arr1[z][c] == 0:
                    xcnt += 1
            if xcnt == 5:
                count += 1

        for z in range(5): #열의 빙고 확인
            xcnt = 0
            for c in range(5):
                if arr1[c][z] == 0:
                    xcnt += 1
            if xcnt == 5:
                count += 1
        
        # 왼쪽 -> 오른쪽 대각선
        if arr1[0][0] == 0 and arr1[1][1] == 0 and arr1[2][2] == 0 and arr1[3][3] == 0 and arr1[4][4] == 0:
            count += 1
        
        # 오른쪽 -> 왼쪽 대각선
        if arr1[0][4] == 0 and arr1[1][3] == 0 and arr1[2][2] == 0 and arr1[3][1] == 0 and arr1[4][0] == 0:
            count += 1
        
        # 빙고가 3개이면 n번째 출력하고 종료
        if count >= 3:
            print(order)
            sys.exit()
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
KOI 2006 지역본선 초등부 3번, 중등부 2번
