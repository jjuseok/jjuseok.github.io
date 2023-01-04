---
layout: post
title: '[ALGORITHM_JOBS] 34. fibonacci'
date: '2023-01-04 08:30:10 +0900'
description: 'fibonacci'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.5]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
피보나치 수열은 수학에서 아주 유명한 수열이다. 피보나치 수열을 이루는 수들을 피보나치 수라고 한다.

피보나치 수는 0과 1로 시작한다. 0번째 피보나치 수는 0이고, 1번째 피보나치 수는 1이다. 그 다음 2번째 부터는 바로 앞 두 피보나치 수의 합이 된다.

이를 식으로 써보면 F(n)= F(n-1) + F(n-2), (n>=2)가 된다.

n이 0 ~ 15일때 까지 피보나치 수를 써보면 다음과 같다.

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610

n이 주어졌을 때, n번째 피보나치 수를 구하는 프로그램을 작성하시오.
<hr>
# <b>입력</b>
첫째 줄에 n이 주어진다. (0 ≤ n ≤ 45)
<hr>
# <b>출력</b>
첫째 줄에 n번째 피보나치 수를 출력한다.  
<hr>
# <b>예제 입력</b><br>
<pre>
10
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
55
</pre>
<hr>
# <b>아이디어</b>
피보나치 수열은 문제에 나와있듯이 다음과 같은 규칙이 존재한다. F(n) = F(n-1) + F(n-2) (n >= 2)<br>
이 규칙을 통해 쉽게 코드를 세울 수 있었다. 초기 배열에 0번째 0, 1번째 1을 넣어 놓고 for문을 통해 n번째까지 반복문을 돌리고 마지막을 출력하면 n번째 피보나치 수를 구할 수 있다. 마지막 출력할 때 if문을 통해 n이 0과 1이면 초기 배열을 출력하고 2이상이면 규칙을 통한 값을 출력하도록 했다.
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
n = int(input())
arr = [0,1]

for i in range(2, n+1):
    arr.append(arr[i-2] + arr[i-1])
    
if n < 2:
    print(arr[n])
else:
    print(arr[-1])
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
ALGORITHM JOBS
