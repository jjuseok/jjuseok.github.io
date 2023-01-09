---
layout: post
title: '[해킹 기초] 10. XSS(Cross Site Scripting)공격'
date: '2023-01-03 08:59:10 +0900'
description: '파일업로드 취약점'
categories: [HACKING,HACKING - Part.2]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: true
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ XSS(Cross Site Scripting)공격이란?</b>
XSS(Cross Site Scripting) 약어를 살펴보면 CSS가 맞지만 이미 CSS는 Cascading Style Sheets 약어로 사용하고 있어서 XSS라고 불린다.
XSS 공격은 XSS(Cross-Site Scripting) 이란 SQL injection과 함께 웹 상에서 가장 기초적인 취약점 공격 방법중 하나로, 권한이 없는 사용자가 악의적인 용도로 웹 사이트에 스크립트를 삽입하는 공격 기법을 말한다.<br>

XSS 공격은 크게 2가지가 있다.
- Reflected XSS
  - URL의 변수 부분처럼 스크립트 코드를 입력하는 동시에 결과가 바로 전해지는 공격기법
  - 반사된 XSS는 피싱 공격의 일부로 자주 사용되며 악용하기도, 차단하기도 가장 쉬움
  - 공격자가 HTTP 요청에 악성 콘텐츠를 주입하면 그 결과가 사용자에게 "반사되는" 형태 
  - 링크를 클릭하도록 피해자를 속이고, 유인해 세션을 하이재킹 할 수 있는 공격
  - 반사된 XSS는 피싱 공격에서 가장 많이 사용됨

- Stored XSS
  - 가장 일반적인 XSS공격 유형
  - 정상적 평문x -> 스크립트 코드를 입력
  - 사용자가 게시물을 열람시, 공격자가 입력해놓은 악성 스크립트가 실행되어 사용자의 쿠키 정보가 유출되거나, 악성 스크립트가 기획한 공격에 당함
  - 저장된(지속적) XSS공격은 공격자가 웹 애플리케이션을 속여 데이터베이스에 악성코드를 저장하도록 하는 수법으로, 
    서버에 저장된 악성코드는 시스템 자체를 공격 할 수 있으며 웹 앱 사용자 상당수 또는 전체에 악성 코드를 전송할 수 있음
  - 일반적인 예로는 블로그 댓글에 악성코드를 게시하는 것
  - 지속적(저장형) XSS 가장 위험한 XSS공격 유형


> 출처 : 
이지미디어

### <b>■ BeEF를 이용한 Stored XSS 공격 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux) - 공격자
    - Virtual Box(DVWA) - 공격 사이트
    - Virtual Box(Window 7) - 피해자

<img src="/assets/img/hacking/part2-4/1.png" alt="표사진"><br>
Stored XSS 공격을 하기 위해서 공격자가 페이지에 악성 스크립트를 심어놔야 된다. 악성 스크립트를 심기 위해서 위 사진과 같이 kali beef-xss를 이용할 것이다. beef-xss를 처음 실행하면 초기 PW를 정하라고 나올것이다. 초기 PW를 정하면 된다.
<hr>

<img src="/assets/img/hacking/part2-4/2.png" alt="표사진"><br>
초기 PW를 정했으면 위와 같이 페이지가 뜰 것이다. 페이지가 뜨지 않았으면 http://127.0.0.1:3000/ui/panel로 접속하면 위와 같은 페이지에 접속할 수 있다. ID : beef는 모두 동일하고 전 단계에서 각자 지정한 PW를 입력하면 로그인 할 수 있다.
<hr>
<img src="/assets/img/hacking/part2-4/3.png" alt="표사진"><br>
로그인 하고나서 다시 kali linux로 돌아온뒤 위 사진에 나온 Hook 부분의 script로 시작하는 부분을 복사하자. 여기서 IP 부분은 공격자 PC IP이다.
<hr>
<img src="/assets/img/hacking/part2-4/4.png" alt="표사진"><br>
전 단계에서 script 부분을 복사했으면 DVWA 사이트에 접속헤서 security low로 설정한 뒤 XSS stored 페이지에 접속하자. 페이지에 접속하면 게시글을 올릴 수 있는 화면이 나오는데 여기서 일반 게시글을 위장한 악성 게시물을 올릴 것이다. 사진과 같이 Name은 평소대로 입력하고 Message 부분에 아까 복사한 script 부분을 삽입하고 Sign Guestbook을 누르자.
<hr>
<img src="/assets/img/hacking/part2-4/5.png" alt="표사진"><br>
게시글을 등록했으면 위와 같이 방금 올린 게시글이 나올 것이다. 이제 악성 스크립트가 삽입된 게시글이 등록 된거다. 이제 다른 사람들이 평소같이 이 사이트를 접속하면 XSS 공격을 당할 것이다.
<hr>
<img src="/assets/img/hacking/part2-4/6.png" alt="표사진"><br>
일반 사용자(피해자)를 가장해서 Windows 7 PC 가상머신을 돌렸다. 피해자 PC에서 악성 스크립트를 올린 게시물 목록에 들어가 보자. DVWA에 접속해 XSS stored에 접속하면 위와 같이 평소대로 잘 접속이 되고 아무 이상이 없다.
<hr>
<img src="/assets/img/hacking/part2-4/7.png" alt="표사진"><br>
하지만 아까 로그인 한 beef 사이트에 들어가보면 위와 같이 피해자 PC가 보일 것이다. 여기서 피해자 PC에 대한 정보를 볼 수 있고 조종도 마음대로 할 수 있다. 여러가지 기능이 있지만 몇가지만 해볼 것이다.
<hr>
<img src="/assets/img/hacking/part2-4/8.png" alt="표사진"><br>
왼쪽에 뜬 IP를 누르고 Details에서 여러 정보를 확인할 수 있다. 우리는 redirect 공격을 해볼 것이다. Commands에 들어간뒤 Module name에 redirect를 검색하면 Redircet Browser이라고 나올 것이다. 이 공격을 하면 피해자는 자신의 의도와 상관 없이 공격자가 Redirect한 페이지로 이동할 것이다.
오른쪽에 Redircet URL 을 설정하고 Execute로 보내면 피해자는 Redirect URL로 강제 이동될 것이다.
<hr>
<img src="/assets/img/hacking/part2-4/9.png" alt="표사진"><br>
피해자 PC를 보면 어느샌가 Redirect URL페이지로 이동한 것을 볼 수 있다. 여기서 공격자가 만든 악성 페이지로 이동시켜 2차 공격을 할 수 있다.
<hr>
<img src="/assets/img/hacking/part2-4/10.png" alt="표사진"><br>
다음 공격은 Google Phishing 공격이다. 이 공격을 간단하게 설명하자면 Google Login 페이지로 강제 Redirect 시켜서 피해자가 ID / PW를 입력하면 그 정보를 Phishing 하는 것이다. 위와 같이 Google Phishing 을 Excute해보자.
<hr>
<img src="/assets/img/hacking/part2-4/12.png" alt="표사진"><br>
그러면 피해자 PC에는 위와 같이 Google Login 페이지가 뜰 것이다. 아무것도 모르는 피해자는 Google에 로그인 하려고 Username과 Password를 입력할 것이다. Username : test / Password : test를 입력하고 Sign in 을 눌러봤다.
<hr>
<img src="/assets/img/hacking/part2-4/13.png" alt="표사진"><br>
다시 공격자 PC beef 사이트의 History를 클릭해보면 위와 같이 피해자가 입력한 Username과 Password의 정보를 알 수 있다.<br>
여기까지 XSS 공격 종류인 Stored XSS를 실습해봤다.
<hr>