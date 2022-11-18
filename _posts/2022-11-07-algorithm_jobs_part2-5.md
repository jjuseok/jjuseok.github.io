---
layout: post
title: '[ALGORITHM_JOBS] 14. Card game'
date: '2022-11-07 09:59:10 +0900'
description: '주사위 게임'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.2]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
두 사람 A와 B는 1부터 10까지의 숫자가 하나씩 적힌 열 장의 카드로 ‘게임’을 한다. 게임은 총 열 번의 ‘라운드’로 구성되고, 각 라운드 마다 자신이 가지고 있는 카드 중 하나를 제시하고, 한 번 제 시한 카드는 버린다. 게임 승패는 다음과 같이 결정된다.

각 라운드는 더 높은 숫자를 제시한 사람이 승리하고, 제시한 숫자가 같은 경우는 비긴다.
열 번의 라운드에서 더 많은 라운드를 승리한 사람이 게임을 승리하고, 승리한 라운드 횟수 가 동일한 경우 비긴다.
다음은 게임의 한 예로, 각 라운드마다 A와 B가 제시한 카드의 숫자와 각 라운드의 승자를 보여준다. (비긴 라운드는 D로 표시함)

<img src="https://alms-problem.s3.ap-northeast-2.amazonaws.com/cardgame.png">

A는 5번의 라운드에서 승리하고 B는 4번의 라운 드에서 승리하였으므로, 이 게임은 A가 승리한다. 라운드 순서대로 A와 B가 제시한 카드의 숫자가 주어졌을 때, 게임의 승자를 판단하는 프로그램을 작성하시오.
<hr>
# <b>입력</b>
다음 정보가 표준 입력으로 주어진다. 첫 번째 줄 에는 A가 제시한 카드의 숫자 10개가 라운드 순서대로 주어지고, 두 번째 줄에는 B가 제시한 카드의 숫자 10개가 라운드 순서대로 주어진다.
<hr>
# <b>출력</b>
다음 정보를 표준 출력으로 출력한다. 게임의 승 패가 결정되는 경우 승리한 사람을 출력하고, 비기는 경우에는 D를 출력한다.

<hr>
# <b>코드</b>
<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
arr1 = list(map(int, input().split())) # A가 제시한 카드 값을 입력받는다.
arr2 = list(map(int, input().split())) # B가 제시한 카드 값을 입력받는다.
arrResult = [] # A와 B의 승 패를 저장할 리스트

for i in range(10):
    if arr1[i] > arr2[i]: # A가 B보다 높은 숫자로 이기는 경우
        arrResult.append('A')
    elif arr1[i] < arr2[i]:# B가 A보다 높은 숫자로 이기는 경우
        arrResult.append('B')
    else: # 비기는 경우
        arrResult.append('D')

if arrResult.count('A') > arrResult.count('B'): # A가 더 많이 이겼으면 A 출력
    print('A')
elif arrResult.count('A') < arrResult.count('B'): # B가 더 많이 이겼으면 B 출력
    print('B')
else: # 비긴 경우 D 출력
    print('D')
~~~
</div>
</details>