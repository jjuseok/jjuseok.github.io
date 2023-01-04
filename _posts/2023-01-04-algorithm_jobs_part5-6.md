---
layout: post
title: '[ALGORITHM_JOBS] 35. combinationzero'
date: '2023-01-04 08:50:10 +0900'
description: 'combinationzero'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.5]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
n명의 사람중 m명을 순서에 상관없이 뽑는 경우의 수를 조합이라고 하며 nCm으로 나타낸다.

nCm은 수식으로 n!/m!(n-m)! 으로 구할 수 있다. (5! = 1 * 2 * 3 * 4 * 5)

n과 m이 주어졌을때 nCm의 끝자리 0의 개수를 출력하는 프로그램을 작성하시오.  
<hr>
# <b>입력</b>
첫째 줄에 정수 n, m(0≤m≤n≤1,000,000)이 들어온다.
<hr>
# <b>출력</b>
첫째 줄에 0의 개수를 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
25 12
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
2
</pre>
<hr>
# <b>아이디어</b>
nCm의 끝자리 0에 개수를 구하려면 0이 되는 조건을 알아봐야 된다. 1 ~ 9까지 숫자에서 서로 곱해서 10의 배수가 되는 경우는 2와 5를 곱했을 경우이다.
문제서 나와있듯이 nCm은 수식으로 n!/m!(n-m)!으로 구할 수 있다. 여기서 규칙을 찾을 수 있는게 0의 개수는 2와 5의 지수중에 최소값이 0의 개수이다.
n = 10, m = 5로 예를 들어 보면 10!/5!(10-5)! -> 3628800 / 120 * 120이 된다. 소인수분해를 해보면
5<sup>2</sup> * 2<sup>8</sup> * 3<sup>4</sup> * 7<sup>1</sup> / (5<sup>1</sup> * 2<sup>3</sup> * 3) * (5<sup>1</sup> * 2<sup>3</sup> * 3)이 된다.
즉 여기서 2의 지수와 5의 지수중에 작은 값이 0의 개수가 된다. 5의 지수는 5<sup>2-1-1</sup>이므로 0, 2의 지수는 2<sup>8-3-3</sup>이므로 2이다.
따라서 최소 지수의 수가 0이므로 0의 갯수도 0이 된다. 이 내용을 바탕으로 아래와 같이 코드를 구현했다.
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
N, M = map(int, input().split())

def count_num(n,k):
    count = 0
    while n:
        n //= k
        count += n
    return count

five_count = count_num(N, 5) - count_num(M, 5) - count_num(N - M, 5)
two_count = count_num(N, 2) - count_num(M, 2) - count_num(N - M, 2)

print(min(five_count,two_count))
~~~
</div>
</details>

<hr>
### <b>문제 출처</b>
ALGORITHM JOBS  