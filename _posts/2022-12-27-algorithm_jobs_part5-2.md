---
layout: post
title: '[ALGORITHM_JOBS] 31. 정렬(sort)'
date: '2022-12-27 08:30:10 +0900'
description: '정렬(sort)'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.5]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
### <b>■ 정렬이란?</b>
우리가 실생활에서 엑셀을 써봤으면 정렬을 한 번쯤 꼭 사용해 봤을 것이다. 엑셀에는 대표적으로 오름차순 정렬, 내림차순 정렬이 있다.
여기서 정렬이란 <b>특정 기준을 적용하여 나열하는 것</b>을 의미한다.

### <b>■ 대표적인 정렬 종류</b>
1. 선택정렬(selection sort)
2. 삽입정렬(insertion sort)
3. 버블정렬(bubble sort)

### <b>1. 선택정렬(selection sort)</b>
선택정렬은 배열에서 가장 작은 값을 앞으로 보내는 정렬이다.<br>
시간복잡도 : O(n^2)
<img src="/assets/img/1/selectionsort.png" alt="표사진"><br>

1 5 6 8 3 4 5 9 2

위와 같은 수가 있을때 수들을 오름차순 선택정렬을 해보자.<br>
먼저 위 수에서 1에서 10까지 반복하며 최솟값을 찾는다.<br>
최솟값을 찾았으면 그 값을 맨 앞 원소와 교환하고 정렬을 한다.

이렇게 첫 번째 반복을 했으면 그다음 반복부턴 확정된 정렬을 제외한 나머지 원소 배열에서 최솟값을 찾은 후
그 값을 다시 확정된 정렬을 제외한 나머지 원소 배열의 맨 앞 원소와 비교해 교환 후 정렬한다.

<b>1</b> 5 6 8 3 4 5 9 2<br>
<b>1 2</b> 6 8 3 4 5 5<br>
<b>1 2 3</b> 8 6 4 5 5<br>
.<br>
.<br>
.<br>
<b>1 2 3 4 5 5 6 8 9</b>

### <b>1.1 선택정렬 알고리즘 구현(python)</b>
<div markdown="1">

~~~python
arr = list(map(int, input().split()))

length = len(arr)
for i in range(length-1):
    indearrMin = i
    for j in range(i+1, length):
        if arr[indearrMin] > arr[j]:
            indearrMin = j
    arr[i], arr[indearrMin] = arr[indearrMin], arr[i]
    print(arr)
~~~
</div>

### <b>2. 삽입정렬(insertion sort)</b>
삽입정렬은 두 번째 원소부터 시작하여 앞 원소들과 비교하여 삽입할 위치를 선택한 후 원소를 뒤로 옮기고 지정된 자리에 삽입되는 정렬이다.<br>
시간복잡도: О(n)
<img src="/assets/img/1/insertionsort.png" alt="표사진"><br>

9 4 3 5 1

위와 같은 수가 있을때 수들을 오름차순 삽입정렬을 해보자.<br>
1. 9와 4비교(삽입)<br>
<b>4</b> 9 3 5 1

2. 9와 3 비교(삽입) -> 3이 4보다도 작으니깐 맨 앞으로 삽입<br>
<b>3</b> 4 9 5 1

3. 9와 5 비교(삽입)<br>
3 4 <b>5</b> 9 1

3. 9와 1 비교(삽입) -> 1이 가장 작으니깐 맨 앞으로 삽입<br>
<b>1</b> 3 4 5 9

### <b>2.1 삽입정렬 알고리즘 구현(python)</b>
<div markdown="1">

~~~python
arr = list(map(int, input().split()))
for i in range(1, len(arr)):
    j = i - 1
    key = arr[i]
    while arr[j] > key and j >= 0:
        arr[j+1] = arr[j]
        j -= 1
    arr[j+1] = key
print(arr)
~~~
</div>

### <b>3. 버블정렬(bubble sort)</b>
버블정렬은 서로 인접한 두 원소를 검사하여 정리하는 알고리즘이다. 선택정렬과 기본 개념이 유사하지만 버블정렬은 서로 비교 후 가장 큰 자료가 맨 뒤로 이동한다.<br>
시간 복잡도: O(n^(2))
<img src="/assets/img/1/bubblesort.png" alt="표사진"><br>
<img src="/assets/img/1/bubblesort1.png" alt="표사진"><br>

### <b>3.1 버블정렬 알고리즘 구현(python)</b>
<div markdown="1">

~~~python
arr = list(map(int, input().split()))
length = len(arr)-1
for i in range(length):
    for j in range(length-i):
        if arr[j] > arr[j+1]:
            arr[j], arr[j+1] = arr[j+1], arr[j]
~~~
</div>