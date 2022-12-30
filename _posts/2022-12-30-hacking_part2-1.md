---
layout: post
title: '[해킹 기초] 7. SQL Injection'
date: '2022-12-30 11:59:10 +0900'
description: 'SQL Injection'
categories: [HACKING,HACKING - Part.2]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: true
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ SQL Injection이란?</b>
응용 프로그램 보안 상의 허점을 의도적으로 이용해, 악의적인 SQL문을 실행되게 함으로써 데이터베이스를 비정상적으로 조작하는 코드 인젝션 공격 방법이다. 인젝션 공격은 OWASP Top10 중 첫 번째에 속해 있으며, 공격이 비교적 쉬운 편이고 공격에 성공할 경우 큰 피해를 입힐 수 있는 공격이다.

### <b>■ SQL Injection 공격 종류</b>
1. Error based SQL Injection
2. Union based SQL Injection
3. Blind SQL Injection
4. Stored Procedure based SQL Injection
위와 같이 SQL Injection 공격에는 여러 종류가 있는데 오늘은 Error based SQL Injection을 알아볼 것이다.<br>

### <b>■ Error based SQL Injection이란?</b>
논리적 에러를 이용한 인젝션 방법이며 가장 많이 사용되고 대중적인 공격방법이다.<br>

### <b>■ Error based SQL Injection 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux)
    - Virtual Box(DVWA) -공격 대상

<img src="/assets/img/hacking/part2-1/1.png" alt="표사진"><br>
DVWA서버를 구동시키고 security level을 low로 저장해준다.<br>

<img src="/assets/img/hacking/part2-1/2.png" alt="표사진"><br>
SQL Injection 페이지에 들어가서 User ID에 1을 입력하면 위와 같이 ID가 1인 사용자에 대한 정보가 나오는 것을 볼 수 있다.<br>

<img src="/assets/img/hacking/part2-1/3.png" alt="표사진"><br>
User ID에 2을 입력하면 위와 같이 ID가 1인 사용자에 대한 정보가 나오는 것을 볼 수 있다.<br>

<img src="/assets/img/hacking/part2-1/4.png" alt="표사진"><br>
User ID에 3을 입력하면 위와 같이 ID가 3인 사용자에 대한 정보가 나오는 것을 볼 수 있다.<br>


여기서 우리가 추측할 수 있는 것은 SQL 구문을 이용해 DB 서버에서 사용자 정보를 가져온다는 것을 추측할 수 있다.<br>
그럼 당연히 SQL 구문이 들어가있을 것이다. 여기서 DB 서버에 어떤 SQL 구문이 들어가는지 고민을 해봐야 된다.<br>
사용자가 User ID를 입력하면 정보를 표시해주고 있다는 것을 생각하면서 고민을 해보자.<br>
SQL 구문 : select * from member where id='[사용자입력]' 이라고 예상을 해본다.<br>
이 구문을 간단히 분석해보면 member라는 테이블에서 id가 [사용자입력]인 데이터의 모든 정보를 가져와라 라는 의미이다.<br>
SQL 구문에서 member이라는 테이블명은 정확하지 않고 가상으로 만든 것이고 여기서 정확한 테이블명은 중요하지 않다.<br>
여기서 우리가 User ID 값에 1을 입력하면 SQL 구문 : select * from member where id='1'이 되는 것이다.<br>
위와 같이 SQL 구문이 있다고 가정하면 취약점이 존재한다. 만약에 사용자가 정상적으로 ID 입력 값에 1, 2, 3.... 와 같은 정보를 입력하면 문제가 되지 않지만
악의적인 목적을 가진 사람이 위협할 수 있는 코드를 입력할 수 있다.<br>
예를들어 ID 입력 값에 1' or '1'='1를 입력한다고 가정해보자<br>
그럼 위에 SQL 구문에 ID 값에 대입하면 SQL 구문 : select * from member where id='1' or '1'='1'이 된다<br>
이 구문을 간단히 분석해보면 member라는 테이블에서 id가 [사용자입력]가 아닌 테이블에 있는 모든 사용자의 모든 정보를 가져와라 가 된다.<br>

<img src="/assets/img/hacking/part2-1/5.png" alt="표사진"><br>
따라서 위와 같이 악의적인 코드를 넣으면 테이블에 있는 모든 사용자의 모든 정보가 위와 같이 출력되는 것을 알 수 있다.<br>
이 공격이 바로 Error based SQL Injection 이다.