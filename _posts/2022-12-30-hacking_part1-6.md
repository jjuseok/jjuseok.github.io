---
layout: post
title: '[해킹 기초] 6. 정보수집-취약점 검색(Search Sploit)'
date: '2022-12-30 11:59:10 +0900'
description: '정보수집-취약점 검색(Search Sploit)'
categories: [HACKING,HACKING - Part.1]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: true
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ Exploit-DB</b>
<a src="https://www.exploit-db.com/">https://www.exploit-db.com/</a><br>
위 사이트는 프로그램, 운영체제, 데이터베이스 등 알려진 취약점들을 모아놓은 웹 사이트이다.<br>
kali linux에서 이 사이트를 활용할 수 있는 명령어가 search sploit이다.<br>
search sploit를 활용해서 대상 컴퓨터의 취약점을 알아보자.

### <b>■ search sploit 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux)
    - Virtual Box(Kioptrix Level 1) -공격 대상

<img src="/assets/img/hacking/part1-6/1.png" alt="표사진"><br>
일단 search sploit를 하기 전에 공격 대상 PC의 정보를 nmap을 활용해서 수집한다.<br>
&#35; nmap -O -sV -sS [스캔하고자 하는 IP] > result.txt<br>
ex) &#35; nmap -O -sV -sS 192.168.1.1 > result.txt<br>
위와 같이 명령어를 입력하면 nmap을 이용해 스캔한 내용을 result.txt 파일로 만들어 저장된다. result.txt파일이 만들어졌으면 cat 명령어를 이용해서 result.txt파일을 살펴보자
우리는 21번 포트인 ftp 취약점을 search sploit를 이용해서 알아볼 것이다.

nmap을 이용해서 정보수집하는 방법은 이전 게시글을 참고하면 된다. <a src="https://jjuseok.github.io/posts/hacking_part1-4/">👉 4. 정보수집-Port Scan</a><br>


<img src="/assets/img/hacking/part1-6/2.png" alt="표사진"><br>
search sploit 사용법은 간단하다. 알아볼 취약점 서비스 및 버전을 입력하면 된다.<br>
ex) &#35; searchsploit ftp 1.3.2c<br>
위와 같이 입력하면 ftp 서비스 1.3.2c 버전에 대한 취약점 목록이 나온다. 여기서 우리는 command Execution 취약점을 알아볼 것이다.
취약점 오른쪽을 보면 공격 코드의 파일 이름이 나온다. 여기서 우리는 find 명령어를 이용해서 파일의 위치를 찾을 수 있다.
파일의 위치를 알아냈으면 공격파일을 가져오자. 공격파일을 가져오면 이제 이 파일을 사용해서 해당 취약점을 공격할 수 있게 된다.