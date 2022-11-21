---
layout: post
title: '[ALGORITHM_JOBS] 13. 주사위 게임'
date: '2022-11-06 08:59:10 +0900'
description: '주사위 게임'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.2]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
1에서부터 6까지의 눈을 가진 3개의 주사위를 던져서 다음과 같은 규칙에 따라 상금을 받는 게임이 있다.<br>

규칙(1) 같은 눈이 3개가 나오면 10,000원+(같은 눈)*1,000원의 상금을 받게 된다.<br>

규칙(2) 같은 눈이 2개만 나오는 경우에는 1,000원+(같은 눈)*100원의 상금을 받게 된다.<br>

규칙(3) 모두 다른 눈이 나오는 경우에는 (그 중 가장 큰 눈)*100원의 상금을 받게 된다.<br>

예를 들어, 3개의 눈 3, 3, 6이 주어지면 상금은 1,000+3 * 100으로 계산되어 1,300원을 받게 된다.<br>

또 3개의 눈이 2, 2, 2로 주어지면 10,000+2 * 1,000 으로 계산되어 12,000원을 받게된다.<br>

3개의 눈이 6, 2, 5로 주어지면 그 중 가장 큰 값이 6이므로 6 * 100으로 계산되어 600원을 상금으로 받게 된다.<br>

N(2≤N≤1,000) 명이 주사위 게임에 참여하였을 때, 가장 많은 상금을 받은 사람의 상금을 출력하는 프로그램을 작성하시오.
<hr>
# <b>입력</b>
첫째 줄에는 참여하는 사람 수 이 주어지고 그 다음 줄부터 N개의 줄에 사람들이 주사위를 던진 3개의 눈이 빈칸을 사이에 두고 각각 주어진다.
<hr>
# <b>출력</b>
첫째 줄에 가장 많은 상금을 받은 사람의 상금을 출력한다..

<hr>
# <b>코드</b>
<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
n = int(input()) # 참가하는 사람의 수 n을 입력받는다.
arr_result=[] # 가장 큰 상금을 출력한다.
for i in range(n): # 참가하는 사람 수 만큼 반복문을 돌린다.
    arr_tmp = [] # 주사위 같은 눈의 개수를 저장할 list를 만들어준다.
    arr = list(map(int, input().split())) # 주사위 눈을 저장할 list를 만들어준다.
    for j in range(len(arr)-1): # 입력받은 주사위 개수 - 1 반복문을 돌린다.
    # -1 하는 이유는 예를들어 [3,3,6]일 때 두번째 리스트까지만 검사해도 개수가 나온다.
    # 세번째 리스트값까지 반복문을 돌릴 필요가 없다.
        arr_tmp.append(arr.count(arr[j])) # arr_tmp 리스트에 주사위 같은 눈의 개수를 저장한다.
    if max(arr_tmp) == 3: # 주사위의 같은 눈의 개수가 3일 경우
        arr_result.append(10000 + arr[arr_tmp.index(max(arr_tmp))] * 1000)
        # arr_result에 규칙에 맞게 결과 값을 저장한다.
    elif max(arr_tmp) == 2:# 주사위의 같은 눈의 개수가 2일 경우
        arr_result.append(1000 + arr[arr_tmp.index(max(arr_tmp))] * 100)
        # arr_result에 규칙에 맞게 결과 값을 저장한다.
    elif max(arr_tmp) == 1:# 주사위의 같은 눈의 개수가 1일 경우
        arr_result.append(max(arr) * 100)
        # arr_result에 규칙에 맞게 결과 값을 저장한다.
print(max(arr_result)) # arr_result 값에서 가장 큰 값을 출력한다.
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
KOI 2010 지역본선 초등부 2번