---
layout: post
title: '[ALGORITHM_JOBS] 40. 대소문자 변환'
date: '2023-01-11 08:50:10 +0900'
description: '대소문자 변환'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.6]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
문자열이 주어질 때, 대문자는 소문자로, 소문자는 대문자로 바꾸는 프로그램을 작성하시오. 알파벳이 아닌 문자는 그대로 유지한다.
<hr>
# <b>입력</b>
첫 번째 줄에 문자열이 주어진다. ( 1 ≤ 문자열의 길이 ≤ 1,000 )  
<hr>
# <b>출력</b>
문자열 내의 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
hELLO wORLD!
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
Hello World!
</pre>
<hr>
# <b>아이디어</b>
이번 문제는 배열으로 풀었다. for문을 돌려 배열의 i번째가 대문자면 소문자로, 소문자면 대문자로 변환 하도록 했다.
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
arr = list(input())

for i in range(len(arr)):
    if arr[i].isupper():
        arr[i] = arr[i].lower()
    else:
        arr[i] = arr[i].upper()

for i in range(len(arr)):
    print(arr[i], end='')
~~~
</div>
</details>
<hr>
### <b>문제 출처</b>
ALGORITHM JOBS