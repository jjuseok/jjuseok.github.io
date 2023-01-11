---
layout: post
title: '[ALGORITHM_JOBS] 44. 문자열 압축'
date: '2023-01-11 09:50:10 +0900'
description: '문자열 압축'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.6]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
문자열의 길이가 굉장히 길 경우, 이를 압축하여 짧게 만들어야 할 때가 종종 있다. 이 문제에서는 문자열이 주어졌을 때, 같은 알파벳이 연속된 부분 문자열을 압축하여 결과를 출력하는 프로그램을 작성한다. 예를 들어, 문자열이 AAABBBBBCCCCDDDDEFFF 라고 하자. 이 문자열을 압축하면, 연속으로 같은 문자가 나오는 부분에, 그 문자가 몇번 나왔는지를 적어줌으로써 압축한다. 즉, 이 문자열은 3A5B4C4DE3F 로 압축된다. E는 1개밖에 없기 때문에 따로 1을 적어주지 않는다.
<hr>
# <b>입력</b>
첫 번째 줄에 압축하고자 하는 문자열이 주어진다. 문자열의 길이는 1000보다 작다. 문자열에 구성된 알파벳은 대문자다.  
<hr>
# <b>출력</b>
문자열을 압축한 결과를 출력한다.
<hr>
# <b>예제 입력</b><br>
<pre>
AAABBBBBCCCCDDDDEFFF
</pre>
<hr>
# <b>예제 출력</b><br>
<pre>
3A5B4C4DE3F
</pre>
<hr>
# <b>아이디어</b>
길이가 긴 문자열을 입력 받은 다음 문자열 i 번째와 i-1 번째를 비교해서 같으면 cnt += 1시키고 다를경우 새로운 arr배열에 cnt와 문자(string[i-1])를 추가 시켰다.
코드에서 중요한 부분은 2번째줄 string.append(0)과 9번쨰줄 if cnt != 1: 부분이다. string.append(0)을 한 이유는 마지막 문자의 개수를 세지 못하고 끝나기 때문이다.
만약에 이 코드가 없다고 하면 예제 입력에서 F의 개수는 출력되지 않는다. 그 이유는 우리가 새로운 배열 arr에 추가하는 조건은 string[i] == string[i-1]가 다를 경우 추가하는데 마지막 FFF 세개 다음 문자가 존재하지 않기 때문에 새로운 배열 arr에 추가하지 않는다. 따라서 string.append(0)을 함으로써 마지막 FFF까지 arr배열에 추가될 수 있게 해준다. 다음은 문제 조건에서 개수가 1이면 1E가 아닌 E로 출력하라는 조건이 있기 때문에 문자의 개수가 1개일 경우에는 개수는 추가하지 않는다.
<hr>
# <b>코드</b>

<details>
<summary id="summary1">풀이보기(클릭)</summary>
<div markdown="1">

~~~python
string = list(input())
string.append(0)
cnt = 1
arr=[]
for i in range(1, len(string)):
    if string[i] == string[i-1]:
        cnt += 1
    else:
        if cnt != 1:
            arr.append(cnt)
        arr.append(string[i-1])
        cnt = 1

for i in range(len(arr)):
    print(arr[i], end='')
~~~
</div>
</details>
<hr>
### <b>문제 출처</b>
ALGORITHM JOBS