---
layout: post
title: '[ALGORITHM_JOBS] 20. offset'
date: '2022-11-20 08:59:10 +0900'
description: 'offset'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.3]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
5x5 2차원 배열이 주어질 때 어떤 원소가 상하좌우에 있는 원소보다 작을 때 해당 위치에 * 을 표시하는 프로그램을 작성하시오. 경계선에 있는 수는 상하좌우 중 존재하는 원소만을 비교한다.
<hr>
# <b>입력</b>
5x5 행렬의 정보가 25 개의 수로 주어진다. 각 수는 0 에서 9 사이 수이다.
<hr>
# <b>출력</b>
*를 포함한 행렬을 출력예의 형식으로 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
3 4 1 4 9
2 9 4 5 8
9 0 8 2 1
7 0 2 8 4
2 7 2 1 4
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
3 4 * 4 9 
* 9 4 5 8 
9 0 8 2 * 
7 0 2 8 4 
* 7 2 * 4 
</pre>
<hr>
# <b>아이디어</b>
다음 문제를 풀기 전 몇가지 고민을 해봤다.<br>
Q. 상하좌우를 비교하기 전 경계선에 있는 수는 존재하는 원소만 비교한다고 나와있는데 어떻게 구현할까?<br>
A. 상하좌우에 배열을 가장 큰 수로 추가해서 똑같이 비교를 하자.<br>
<span><img src="/assets/img/1/offset.png" alt="표사진"></span><br>
Q. 원소를의 상하좌우를 어떻게 비교할까?<br>
A. 2차원 배열의 좌표를 이용해서 상하좌우를 비교하자.<br>
<img src="/assets/img/1/offset2.png" width="700px" alt="표사진"><br>
만약에 첫 원소인 3을 기준으로 상하좌우를 비교한다고 가정해보자.<br>
원소의 좌표를 2차원 배열로 나열하면 위 그림과 같이 나온다.<br>
여기서 규칙을 찾아보면 위쪽을 비교할 땐 기준 좌표에서 (-1,0)<br>
왼쪽을 비교할 땐 기준 좌표에서 (0, -1), 오른쪽을 비교할 땐 기준 좌표에서 (0, +1)<br>
아래쪽을 비교할 땐 기준 좌표에서 (+1,0)을 해서 요소와 비교하면 된다.<br>
<br><b>따라서 간단히 요약하면</b>
<pre>
1. 2차원 배열로 입력받는다.
2. 테두리 요소를 비교하기 위해 테두리에 가장 큰 요소인 10을 넣는다.
3. 2중 for 문을 이용해 요소 하나하나씩 접근한다.
4. 요소를 기준으로 상하좌우를 비교한다.
5. if 문을 이용해 상하좌우 중 가장 작으면 *을 출력하고 아니면 요소를 출력한다.
</pre>
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
arr1 = [list(map(int, input().split())) for _ in range(5)]
for i in range(5):
    arr1[i].insert(0,10)
    arr1[i].append(10)
arr1.insert(0,[10,10,10,10,10,10,10])
arr1.append([10,10,10,10,10,10,10])

for i in range(1, 6):
    for j in range(1,6):
        if arr1[i-1][j] > arr1[i][j] and arr1[i+1][j] > arr1[i][j] and arr1[i][j-1] > arr1[i][j] and arr1[i][j+1] > arr1[i][j]:
            print('*',end=" ")
        else:
            print(arr1[i][j], end=" ")
    print()
~~~
</div>
</details>
