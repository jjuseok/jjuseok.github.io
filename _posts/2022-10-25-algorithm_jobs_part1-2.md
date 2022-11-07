---
layout: post
title: '[ALGORITHM_JOBS] 2. 윷놀이'
date: '2022-10-25 09:59:10 +0900'
description: '짝수 판별하기.'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - <b>Part.1</b>]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
우리나라 고유의 윷놀이는 네 개의 윷짝을 던져서 배(0)와 등(1)이 나오는 숫자를 세어 도, 개, 걸, 윷, 모를 결정한다. 네 개 윷짝을 던져서 나온 각 윷짝의 배 혹은 등 정보가 주어질 때 도(배 한 개, 등 세 개), 개(배 두 개, 등 두 개), 걸(배 세 개, 등 한 개), 윷(배 네 개), 모(등 네 개) 중 어떤 것인지를 결정하는 프로그램을 작성하라.
<hr>
# <b>입력</b>
첫째 줄부터 셋째 줄까지 각 줄에 각각 한 번 던진 윷짝들의 상태를 나타내는 네 개의 정수(0 또는 1)가 빈칸을 사이에 두고 주어진다.
<hr>
# <b>출력</b>
첫째 줄부터 셋째 줄까지 한 줄에 하나씩 결과를 도는 A, 개는 B, 걸은 C, 윷은 D, 모는 E로 출력 한다.
<hr>
# <b>아이디어</b>
일단 문제 입력이 첫째 줄 ~ 셋째 줄이므로 for문을 사용하여 3번 돌리면 된다.<br>
for문을 3회 돌리고 if-elif-else문을 활용하여 도, 개, 걸, 윷, 모에 해당 되는 알파벳을 출력하면 된다.
<hr>
# <b>코드</b>
<hr>
~~~python
for i in range(3): #문제 입력부분에서 3회 반복
    a = list(map(int, input().split())) # 각 해당되는 부분의 알파벳 출력
    if a.count(0) == 1:
        print('A')
    elif a.count(0) == 2:
        print('B')
    elif a.count(0) == 3:
        print('C')
    elif a.count(0) == 4:
        print('D')
    else:
        print('E')
~~~