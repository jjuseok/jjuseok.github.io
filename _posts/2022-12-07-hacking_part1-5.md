---
layout: post
title: '[해킹 기초] 5. 정보수집-웹 스캐닝'
date: '2022-12-07 11:59:10 +0900'
description: '정보수집-웹 스캐닝'
categories: [HACKING,HACKING - Part.1]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: true
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ 웹 스캐닝이란?</b>
- 웹 사이트를 사전에 조사하는 방법이다.
- 웹 서버의 종류나 버전, 디렉터리 구조 및 취약한 부분이 있나 분석하는 방법이다.

### <b>■ kali linux nmap을 통한 Port Scan 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux)
    - Virtual Box(Kioptrix Level 1)

우리는 <a href="https://jjuseok.github.io/posts/hacking_part1-4/">전 게시글에서</a> 대상 IP의 포트스캔을 통해서 80번 포트가 열려있는 것을 확인했다.
이번 시간에는 80번 http 포트 취약점을 이용해서 웹 스캐닝을 진행할 예정이다.
여기서 포트까지 다 설명하면 길어지니깐 새로운 게시글로 설명하고 여기서는 간단하게 설명할 것이다.
포트 중에 잘 알려진 포트 well-Known port가 있으며 범위는 0번 ~ 1023번이다.
여기에 포함된 80번 포트의 역할은 HTTP-웹 페이지 전송, 웹 서비스를 하는 포트이다.
따라서 지난 시간에 80번 포트가 열려있다는 의미는 즉 웹서비스가 실행중인 것이다. 따라서 firefox를 통해서 접속해봤다.<br>
<img src="/assets/img/hacking/webscan.png" alt="표사진"><br>
ip 주소로 접속을 해봤더니 위와 같은 TEST 페이지가 있다는 것을 알았다.
하지만 우리는 딱 여기까지만 알고 홈페이지 디렉터리 구조를 모른다.
여기서 웹 스캐닝을 통해 디렉터리 구조를 알아볼 것이다.<br>

웹 스캐닝은 <b>kali linux의 dirbuster</b>도구를 사용할 것이다.
dirbuster도구는 디렉터리와 파일 정보 수집 도구로 웹 / 어플리케이션상 숨겨진 디렉터리를 무작위대입공격 방식을 사용해
찾는 도구이다.

<img src="/assets/img/hacking/webscan1.png" alt="표사진"><br>

위와 같이 cmd창을 띄어 dirbuster 명령어를 입력해보자.

<img src="/assets/img/hacking/webscan2.png" alt="표사진"><br>

명령어를 입력하면 위와 같이 자바로 제작된 툴이 실행된다.

<img src="/assets/img/hacking/webscan3.png" alt="표사진"><br>

dirbuster을 실행시키고 Target URL 칸에 대상 IP를 위와 같이 입력한다.

<img src="/assets/img/hacking/webscan4.png" alt="표사진"><br>

IP를 입력 후 List Info 를 클릭한다.

<img src="/assets/img/hacking/webscan5.png" alt="표사진"><br>

List Info를 클릭하면 사전대입공격을 할 수 있는 파일들 리스트가 나온다. 여기서 지금은 directory-list-2.3-small.list를 이용할 것이다.
여기서 문제는 directory-list-2.3-small.list 파일의 경로를 입력해야 되는데 우리는 파일의 위치를 모른다.

<img src="/assets/img/hacking/webscan6.png" alt="표사진"><br>
그럴때 find 명령어로 파일의 위치를 찾는다. 위와 같이 입력하면 빨간색 부분 같이 파일의 경로가 나올 것이다.

<img src="/assets/img/hacking/webscan7.png" alt="표사진"><br>
파일의 경로가 나오면 위와 같이 File with list of dirs/files에 경로를 입력하면 된다.
경로를 입력하고 오른쪽 아래 start 버튼을 누른다.

<img src="/assets/img/hacking/webscan8.png" alt="표사진"><br>
start 버튼을 누르면 위와 같이 사전대입공격을 이용해 웹 스캐닝을 시작한다.웹 스캐닝을 하면 홈페이지 디렉터리 구조를 알 수 있다. 
테스트로 위에서 웹 스캐닝을 통해 얻은 결과를 직접 접속해보자. /icons/ 페이지를 접속할 것이다.

<img src="/assets/img/hacking/webscan9.png" alt="표사진"><br>
firefox 검색창에 http://[IP]/icons/를 입력하니깐 우리가 웹 스캔 없이는 찾을 수 없는 페이지에 접속할 수 있었다.

이렇게 웹 스캐닝을 통해 평소라면 알 수 없는 페이지에 접속할 수 있고, 여기서 많은 취약점을 찾을 수 있다.
