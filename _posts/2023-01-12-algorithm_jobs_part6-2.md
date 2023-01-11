---
layout: post
title: '[ALGORITHM_JOBS] 41. 과제물 망치기'
date: '2023-01-11 08:51:10 +0900'
description: '과제물 망치기'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.6]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
철수는 영희를 괴롭히는 것을 매우 좋아한다. 오늘도 철수는 영희를 어떻게 괴롭힐지 고민을 하다가, 영희가 최근에 작성하고 있던 문서가 떠올랐다. 이에 철수는 영희의 문서를 망쳐놓기로 결심한다. 바로 띄어쓰기를 모두 제거해버리는 것이다. 영희의 문서를 확인한 철수는, 띄어쓰기가 너무 많아 직접 모두 제거할 수는 없다는 것을 깨닫고 도움을 요청했다. 영희의 문서가 주어질 때, 띄어쓰기를 모두 제거하는 프로그램을 작성하시오.
<hr>
# <b>입력</b>
첫째 줄에 영희의 문서가 주어진다. 영희의 문서는 한 줄 짜리 문자열이며, 문서의 길이는 100,000을 넘지 않는다.  
<hr>
# <b>출력</b>
문자열의 띄어쓰기를 모두 제거한 결과를 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
Please do not touch anything
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
Pleasedonottouchanything
</pre>
<hr>
# <b>아이디어</b>
이번 문제도 너무 간단하게 replace를 이용해서 띄어쓰기를 모두 제거 했다.
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
arr = input()
arr = arr.replace(' ', '')
print(arr)
~~~
</div>
</details>
<hr>
### <b>문제 출처</b>
ALGORITHM JOBS