---
layout: post
title: '[ALGORITHM_JOBS] 17. array 3 :star:'
date: '2022-11-14 09:59:10 +0900'
description: '점수 계산'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.2]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
N이 주어질 때, 다음과 같은 프로그램을 작성해보자.
<hr>
# <b>입력</b>
첫째 줄에 자연수 N이 주어진다.(1<=N<=100)
<hr>
# <b>출력</b>
예시를 참고하여 작성하자.<br>
예제 입력<br>
```
3
```
예제 출력
```
1 2 4
3 5
6 
```
<hr>
# <b>아이디어</b>
예제처럼 출력하기 위해 리스트 arr을 2차원 배열로 입력 받는다.<br>

<span><img src="/assets/img/table.png" alt="표사진"><br></span>
표로 설명을 하면 위에 나와있는 표처럼 결과가 나오기 위해서는 위 순서대로 2차원 리스트에 값을 저장해야 된다.<br>
표에서 나와있는 좌표는 arr좌표 즉 2차원 배열의 좌표이다.<br>
우리가 n에 3을 입력하면 arr : [[1, 2, 4], [3, 5, 0], [6, 0, 0]] 이라는 값을 가질 것이다.<br>

이렇게 arr을 정의하고 이제 반복문을 이용해 arr에 값을 하나씩 넣어야 된다.<br>
n을 입력받으면 행의 수가 n개니깐 처음 for문은 n번째까지 반복해야 된다. ex) n = 3은 표에서 봤듯이 행이 3줄이 나온다.<br>
여기서 중요한 점은 우리가 arr리스트에 넣어야 되는 순서이다.<br>
가시성 있게 좌표로 나타내면 (0,0)=1 / (0,1)=2 (1,0)=3 / (0,2)=4 (1,1)=5 (2,0)=6 순서로 값을 넣어야 된다.<br>
여기서 찾을 수 있는 규칙이 [y][x]라고 할 때 x는 1씩 줄어들고 y는 1씩 증가한다.
<span><img src="/assets/img/table2.png" alt="표사진"></span><br>

이렇게 값을 넣어야 되니깐 x = i, y = 0로 값을 초기화 해준다.<br>
두번째 for문에서 범위가 i+1인 이유는 위에 표 빗금친 부분을 잘 살펴보면 된다.<br>
첫 번째 빗금에서 보면 값을 1개만 넣으면 되고, 2번 째 빗금은 2개, 3번 째 빗금은 3개..... 이런 규칙으로 값을 넣어야 된다.<br>
따라서 두 번째 반복문은 i+1번을 실행하면 된다.<br>
arr에 cnt 값을 넣고 cnt는 1,2,3,4,5,6..... 이어야 되니깐 cnt += 1을 해준다.<br>
위에서 찾은 규칙을 바탕으로 x -= 1 y -= 1을 해준다.<br>

그리고 2중 for문을 이용해 arr값을 하나씩 출력해주면 된다..
<hr>
# <b>코드</b>
<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
n = int(input())
arr = [[0] * 105 for _ in range(105)]
cnt = 1

for i in range(n): # 입력받은 행의 수
    x = i
    y = 0
    for j in range(i+1):
        arr[y][x] = cnt
        cnt += 1
        x -= 1
        y += 1
        
for i in range(n):
    for j in range(n-i):
        print(arr[i][j], end=" ")
    print()
~~~
</div>
</details>

