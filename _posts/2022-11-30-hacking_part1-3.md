---
layout: post
title: '[해킹 기초] 3. 정보수집-Ping Sweep'
date: '2022-11-30 19:59:10 +0900'
description: '정보수집-Ping SweepT'
categories: [HACKING,HACKING - Part.1]
image: /assets/img/1/hacking.png
tags: [network]
toc: true
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ Ping Sweep이란?</b>
- 해킹하기 전에 네트워크상에 어떤 장비가 살아있는지 확인하는 기법이다.
- 속도가 느린 단점이 있어서 소규모 네트워크에 사용하기 적합하다.
- 속도는 느리지만 정확한 결과를 가져다 준다.

### <b>:star: Ping Sweep을 실습해보기 전에 우선 Ping에대해 알아보자.<b>
### <b>■ Ping</b>
- Paket Internet Groper의 약자이며 컴퓨터 네트워크의 상태를 점검, 진단하는 명령어이다.
- ping 명령은 TCP/IP 프로토콜 중 ICMP를 통해 동작한다.
- ping에 간단한 원리를 살펴보자.
1. 상태를 확인하려는 대상을 향해 패킷을 보낸다.(ICMP echo request)
2. 이를 수신한 대상은 살아있으면 응답을 보낸다.(ICMP echo reply)
3. 응답이 오면 대상의 상태를 확인할 수 있다.

### <b>■ kali linux namp을 통한 Ping Sweep 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux)
    - Virtual Box(Kioptrix Level 1)
<img src="/assets/img/hacking/part3.png" alt="표사진"><br>

&#35; nmap -n -vv -sn [스캔하고자 하는 IP]-255 -oG - | grep -i 'up'<br>
ex) &#35; nmap -n -vv -sn 192.1.1.1-255 -oG - | grep -i 'up'<br>
이렇게 명령어를 치면 Status:&#39;up&#39;  즉 살아있는 장비들의 IP 주소 리스트를 출력한다.
- nmap : scanning 할 때 쓰는 대표적인 tool<br>
- -n : scanning 하는 IP에 대해 DNS 질문을 하지 않는다 -> 속도 향상
- -vv : 명령어를 실행하는 동안 실시간으로 보고한다.
- -sn : Ping Sweep을 하는 옵션
- -oG : 출력을 Grepable 형태로 나타낸다.
- &#124; grep -i &#39;up&#39; : 상태가 up인 결과만 뽑아서 출력한다.