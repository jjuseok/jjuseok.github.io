---
layout: post
title: '[해킹 기초] 4. 정보수집-Port Scan'
date: '2022-12-07 10:59:10 +0900'
description: '정보수집-Port Scan'
categories: [HACKING,HACKING - Part.1]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: true
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ Port Scan이란?</b>
- 단어 의미 그대로 대상의 어떤 포트가 열려있는지 확인하는 작업이다.
- 포트 스캔은 운영 중인 서버에서 열려 있는 TCP/UDP 포트를 검색하는 것을 의미한다.

### <b>■ kali linux nmap을 통한 Port Scan 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux)
    - Virtual Box(Kioptrix Level 1)
<img src="/assets/img/hacking/portscan.png" alt="표사진"><br>

&#35; nmap -sn [스캔하고자 하는 IP]-255 --open<br>
ex) &#35; nmap -sn 192.168.1.1-255 --open<br>
이렇게 명령어를 치면 범위 내에서 포트가 열려있는 장비들을 출력한다.<br>
나는 Virtual Box(Kioptrix Level 1)를 찾는 걸로 목표로 portscan을 진행했다.<br>
최종적으로 빨간색 친 부분이 Virtual Box(Kioptrix Level 1)이다.<br>
- nmap : scanning 할 때 쓰는 대표적인 tool<br>
- -sn : 연결 가능한 대상만 출력
- --open : 열려있는 포트만 표시
<img src="/assets/img/hacking/portscan1.png" alt="표사진"><br>
&#35; nmap -O -sV -sS [스캔하고자 하는 IP]<br>
ex) &#35; nmap -O -sV -sS 192.168.1.1<br>
위 port scan에서 얻은 특정 대상 IP를 이용해 더 상세한 정보를 표시한다.<br>
목표 대상이 Virtual Box(Kioptrix Level 1)이므로 상세히 출력하는 명령어이다.

- nmap : scanning 할 때 쓰는 대표적인 tool<br>
- -O : OS 탐색
- sV : 포트의 서비스/버전 정보를 확인
- -sS : TCP SYN 스캔
