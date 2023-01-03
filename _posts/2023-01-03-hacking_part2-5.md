---
layout: post
title: '[해킹 기초] 11. 피싱(Phishing)공격'
date: '2023-01-03 09:59:10 +0900'
description: '피싱(Phishing)공격'
categories: [HACKING,HACKING - Part.2]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: true
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ 피싱(Phishing)공격이란?</b>
피싱(phishing)은 전자우편 또는 메신저를 사용해서 신뢰할 수 있는 사람 또는 기업이 보낸 메시지인 것처럼 가장함으로써, 비밀번호 및 신용카드 정보와 같이 기밀을 요하는 정보를 부정하게 얻으려는 소셜 엔지니어링(social engineering)의 한 종류이다.

> 출처 : 위키백과

### <b>■ setoolkit을 이용한 피싱(Phishing)공격 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux) - 공격자
    - Virtual Box(Window 7) - 피해자

<img src="/assets/img/hacking/part2-5/1.png" alt="표사진"><br>
피싱 공격을 하기 전에 공격자는 피해자를 속일 만한 사이트를 만들어야 된다. 사이트를 만들어주는 kali linux의 setoolkit을 이용할 것이다. kali linux에서 setoolkit을 실행시켜보자.
<hr>
<img src="/assets/img/hacking/part2-5/2.png" alt="표사진"><br>
setoolkit을 실행 시키면 위와 같이 실행 되고 메뉴중에 고르라고 나올 것이다. 우리는 Social-Engineering Attacks 종류은 피싱 공격을 해야 되니 1번을 선택하자.
<hr>
<img src="/assets/img/hacking/part2-5/3.png" alt="표사진"><br>
웹 사이트 공격을 할 것이니깐 Website Attack vectors인 2번을 선택하자.
<hr>
<img src="/assets/img/hacking/part2-5/4.png" alt="표사진"><br>
계정 정보(ID/PW)를 피싱할 것이니깐 3번을 선택하자.
<hr>
<img src="/assets/img/hacking/part2-5/5.png" alt="표사진"><br>
우리는 쉽게 기존에 있는 사이트 템플릿을 사용해 공격할 것이므로  1번을 선택하자.
<hr>
<img src="/assets/img/hacking/part2-5/6.png" alt="표사진"><br>
kali linux가 공격자 PC이므로 기본값 엔터를 누르자.
<hr>
<img src="/assets/img/hacking/part2-5/7.png" alt="표사진"><br>
피싱 페이지를 구글로그인 페이지로 만들 예정이기 때문에 2번을 선택하자.
여기까지 하면 피싱 페이지를 만든 것이다.
<hr>
<img src="/assets/img/hacking/part2-5/8.png" alt="표사진"><br>
피해자 PC인 Windows 7에 들어가서 공격자 IP를 입력하면 위와 같은 Google Login 페이지가 나온다. 여기서 피해자가 Email과 Password를 입력한다고 가정해보자.
<hr>
<img src="/assets/img/hacking/part2-5/9.png" alt="표사진"><br>
피해자 입장으로 Email : test password : test를 입력하고 Sign in 버튼을 눌러봤다.
<hr>
<img src="/assets/img/hacking/part2-5/10.png" alt="표사진"><br>
역시 정상적으로 로그인은 되지 않지만 google.com 페이지로 이동한다. 여기서 피해자는 로그인이 잘 안된건가? 생각하고 해킹 당한거라고 생각을 못할 것이다.
<hr>
<img src="/assets/img/hacking/part2-5/11.png" alt="표사진"><br>
이 상황에서 다시 공격자 kali linux로 돌아와 보면 위와 같이 피해자가 입력한 Email 과 Password를 볼 수 있다.<br>
여기까지 setoolkit을 이용한 피싱(Phishing)공격을 해봤다.
<hr>