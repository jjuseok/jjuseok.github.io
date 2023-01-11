---
layout: post
title: '[ALGORITHM_JOBS] 43. 팰린드롬 조사'
date: '2023-01-11 09:50:10 +0900'
description: '팰린드롬 조사'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.6]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
문자열이 주어질 때, 이것이 팰린드롬인지 조사하는 프로그램을 작성하시오. 팰린드롬이란, 앞으로 읽을 때와 뒤로 읽을 때의 결과가 같은 문자열을 말한다.  
<hr>
# <b>입력</b>
첫 번째 줄에 문자열이 주어진다. ( 1 ≤ 문자열의 길이 ≤ 1,000 )  
<hr>
# <b>출력</b>
입력된 문자열이 팰린드롬이면 YES, 아니면 NO를 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
abcba
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
YES
</pre>
<hr>
# <b>아이디어</b>
이번 문제도 너무 간단하게 문자열의 성질을 이용해서 입력받은 문자열과 뒤집은 문자열이 같으면 'YES'출력 아니면 'NO'를 출력했다.
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
arr = input()
if arr == arr[::-1]:
    print('YES')
else:
    print('NO')
~~~
</div>
</details>
<hr>
### <b>문제 출처</b>
ALGORITHM JOBS