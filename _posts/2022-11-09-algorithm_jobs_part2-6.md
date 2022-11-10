---
layout: post
title: '[ALGORITHM_JOBS] 15. 숫자 피라미드(고민중....)'
date: '2022-11-09 09:59:10 +0900'
description: '숫자 피라미드'
categories: [ALGORITHM_JOBS,ALGORITHM_JOBS - Part.2]
image: /assets/img/aj.PNG
tags: [python]
toc: true
---
# <b>문제</b>
N과 시작 숫자 S가 주어지면 숫자 피라미드를 만드는 프로그램을 작성하시오.
예를 들어, N이 5이고 S가 3 이라면, 그 숫자 피라미드는 다음과 같다.
```
    3
   456
  21987
 3456789
987654321
```

- 시작 숫자 S는 꼭대기부터 1씩 증가한다.
- 시작 행의 번호가 1번이라고 했을때, 짝수번째 행은 왼쪽에서 오른쪽으로 1씩 증가하도록 적고, 홀수번째 행은 거꾸로 적는다.
- 숫자가 만약 10이 될 경우, 1로 바꾸고 다시 증가한다.  

<hr>
# <b>입력</b>
입력의 첫 번째 줄에 N과 시작 숫자 S가 주어진다. ( 1≤N≤100, 1 ≤S≤ 9)
<hr>
# <b>출력</b>
첫 번째 줄부터 숫자 피라미드를 출력한다.<br>(각 줄에 존재하는 공백의 개수와 숫자의 개수를 정확하게 확인해주시바랍니다.)
<hr>
# <b>아이디어</b>
이 문제는 그렇게 쉽게 풀리지 않았다......<br>
아래는 n = 5, s = 3일 경우 결과값이다.<br>
```
    3
   456
  21987
 3456789
987654321
```
이 문제를 풀기 전에 생각해야 되는 경우가 몇 가지 있다.<br>
1. **<span style="color:blue ">홀수</span>** 번 째 줄에 있는 숫자는 **<span style="color:blue">감소</span>**한다.
2. **<span style="color:red">짝수</span>** 번 째 줄에 있는 숫자는 **<span style="color:red">증가</span>**한다.
3. 각 줄에 첫 번째 숫자는 어떻게 구해야 될까?<br>
- 짝수 줄의 첫 번째 숫자는 전 줄 첫 번째 숫자 + 1 이다.<br>
- 홀수 줄의 첫 번째 숫자는 전 줄 마지막 숫자에서 다음 줄의 숫자 개수만큼 플러스하면 된다.<br>
- 여기서 중요한 점이 있다. 위의 예시에서 세 번째 줄의 첫 번째 숫자를 구한다고 가정해 보자.<br>
- 각 줄에서 규칙을 찾으면 각 줄의 숫자 개수는 1, 3, 5, 7......으로 증가하고 있다.<br>
- 여기서 세 번째 줄의 첫 번째 숫자를 구하면<br>6(2번째 줄에 마지막 숫자) + 5(세 번째 줄에 숫자 개수)가 아니다.<br>
6 에서 1씩 앞으로 가야 된다. 6+1=7, 7+1=8, 8+1=9, 9+1=10이 아니라 1이다. 1+1=2<br>따라서 세 번째 줄의 첫 번째 숫자는 1이다.<br>

이 방법들을 생각하면서 천천히 코드를 작성해 봤다.<br>
### <b> :star: 이 문제는 어려워서 반복해서 다시 봐야 될 문제이다.</b>
<hr>
# <b>코드</b>
~~~python
n, s = map(int, input().split())
space = n - 1

num = 1
firstNum = 0
endNum = 0

for i in range(1,n+1): # 숫자 출력 하기 전 공백 출력
    for j in range(space):
        print(' ',end="")
    
    if i % 2 == 0: #짝수 일 경우
        firstNum += 1
        if firstNum == 10:
            firstNum = 1
        for k in range(num):
            print(firstNum ,end="")
            firstNum += 1
            if firstNum == 10:
                firstNum = 1

    else: #홀수 일 경우
        if i == 1: # 첫 번째 줄의 숫자는 무조건 s가 출력 된다.
            print(s, end="")
            firstNum = s
        else:
            endNum = firstNum
            for p in range(num-1):
                if endNum >= 10:
                    endNum = 1
                endNum += 1
                if endNum == 10:
                    endNum = 1

            firstNum = endNum

            for z in range(num):
                print(endNum,end="")
                endNum -= 1
                if endNum == 0:
                    endNum = 9
    num += 2
    space -= 1
    print()
~~~

