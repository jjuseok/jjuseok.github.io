---
layout: post
title: '[해킹 기초] 1. 정보수집-OSINT'
date: '2022-11-30 08:59:10 +0900'
description: '정보수집-OSINT'
categories: [HACKING,HACKING - Part.1]
image: /assets/img/1/hacking.png
tags: [network]
toc: true
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ OSINT란?</b>
- Open Source INTelligence 
- Passive Infomation Gathering(수동적인 정보수집)이다.
- 간단히 말해서 외부에 공개된 정보를 통해 얻은 데이터이다.
- 누구나 합법적으로 접근할 수 있는 데이터를 이용하는 것이다.

### <b>■ Netcraft</b>

[Netcraft](https://www.netcraft.com/)는 특정한 웹 사이트의 정보를 확인할 수 있는 대표적인 사이트이다.

<img src="/assets/img/hacking/part1-2-1.png" alt="표사진"><br>

사이트에 들어가서 조금 내리다 보면 위와 같은 화면이 나올 것이다.<br>
빨간색 박스 친 부분에 특정한 웹 사이트의 url을 입력하면 정보를 얻을 수 있다.

<img src="/assets/img/hacking/part1-2-2.png" alt="표사진"><br>

나는 구글 url을 입력하고 정보를 확인해 봤다.<br>
확인해 보니 생성날짜, 서버가동, OS, 위치 등 많은 정보를 제공하고 있다.

### <b>■ whois</b>
<b>whois</b>명령어는 도메인 정보를 확인하는 명령어이다.<br>
whois를 이용하면 도메인의 책임자 이름, 연락처, 주소, 네임서버의 호스트명, IP주소, 도메인 등록 대행기관등의 정보를 알 수 있다.<br>
<img src="/assets/img/hacking/part1-2-3.png" alt="표사진"><br>


### <b>■ nslookup</b>
<img src="/assets/img/hacking/part1-2.png" alt="표사진"><br>
나는 kali linux를 활용해서 nslookup을 실행했다.<br>
nslookup 명령어를 입력하고 Enter를 누르면 입력하라고 ">"가 나온다.<br>
그럼 IP를 얻고 싶은 URL를 입력하면 Address를 반환해준다.<br>
