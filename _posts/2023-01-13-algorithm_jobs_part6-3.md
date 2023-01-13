---
layout: post
title: '[ALGORITHM_JOBS] 42. 문자열 뒤집기'
date: '2023-01-11 08:52:10 +0900'
description: '문자열 뒤집기'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.6]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
문자열이 주어질 때, 이를 뒤집어서 출력하는 프로그램을 작성하시오.  
<hr>
# <b>입력</b>
첫 번째 줄에 문자열이 주어진다. ( 1 ≤ 문자열의 길이 ≤ 1,000 )  
<hr>
# <b>출력</b>
문자열을 뒤집은 결과를 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
Hello World!
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
!dlroW olleH
</pre>
<hr>
# <b>아이디어</b>
이번 문제도 너무 간단하게 문자열의 성질을 이용해서 풀었다.
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
arr = input()
print(arr[::-1])
~~~
</div>
</details>
<hr>
### <b>문제 출처</b>
ALGORITHM JOBS