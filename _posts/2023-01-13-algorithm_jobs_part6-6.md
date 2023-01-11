---
layout: post
title: '[ALGORITHM_JOBS] 45. 문자열 포함관계 조사'
date: '2023-01-11 09:50:10 +0900'
description: '문자열 포함관계 조사'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.6]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
문자열 A와 B가 주어질 때, 문자열 B가 문자열 A에 포함되어 있는지를 조사하는 프로그램을 작성하시오. 단, 문자열 A와 B에는 알파벳으로만 이루어져 있으며, 공백은 포함되지 않는다고 가정한다.  
<hr>
# <b>입력</b>
첫 번째 줄에 문자열 A, 두 번째줄에 문자열 B가 주어진다. 각각의 길이는 1,000을 넘지 않는다. 두 문자열은 모두 소문자 알파벳으로만 구성되어있다.  
<hr>
# <b>출력</b>
문자열 B가 문자열 A에 포함되면 YES, 아니면 NO를 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
watermelon
melon
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
YES
</pre>
<hr>
# <b>아이디어</b>
문자열 string을 입력받기 tmp와 비교하는 문제이다. if 문을 사용해 string[i]번째와 tmp[0]번째가 같을 경우 그 문자부터 len(tmp)까지의 문자를 비교하는 것이다. 예제 입력으로 예를 들어보면 string : watermelon , tmp : melon이다. 여기서 string[5]와 tmp[0]이 'm'으로 같다. 이렇게 같을 경우 string[5:10]이랑 tmp랑 비교하는 것이다. string[5:10] = 'melon'이고 tmp도 'melon'이기 때문에 check를 'YES'로 바꾼 다음 마지막으로 check를 출력한다.

<hr>
(수정)
더 짧은 코드를 구현했다. 간단하게 in 을 사용하여 작성했다. string을 입력받고 tmp를 입력 받고 in을 사용해서 tmp문자열이 string에 있으면 TRUE 없으면 FALSE 값을 넣는다.
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
string = input()
tmp = input()
check = 'NO'

for i in range(len(string)):
    if string[i] == tmp[0] and string[i:i+len(tmp)] == tmp:
        check = 'YES'

print(check)
~~~
</div>
</details>
<hr>

<details>
<summary id="summary1">풀이보기- 더 짧은 코드(클릭)</summary>
<div markdown="1">

~~~python
string = input()
tmp = input() in string
if tmp:
    print("YES")
else:
    print("NO")
~~~
</div>
</details>
<hr>
### <b>문제 출처</b>
ALGORITHM JOBS