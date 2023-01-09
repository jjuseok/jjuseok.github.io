---
layout: post
title: '[해킹 기초] 9. LFI와 RFI 취약점'
date: '2022-12-30 11:59:10 +0900'
description: '파일업로드 취약점'
categories: [HACKING,HACKING - Part.2]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: true
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ LFI(Local File Inclusion)이란?</b>
웹 브라우저를 통해 서버에 파일을 포함시키는 과정에서 발생하는 취약점이다.

### <b>■ ■ LFI(Local File Inclusion) 취약점 공격 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux)
    - Virtual Box(DVWA) -공격 대상

<img src="/assets/img/hacking/part2-2/2.png" alt="표사진"><br>
DVWA 사이트에 들어가서 security를 low로 설정해준뒤 왼쪽 메뉴에서 File Inclusion으로 들어간다.

<img src="/assets/img/hacking/part2-3/2.png" alt="표사진"><br>
File Inclusion으로 들어가서 위에 URL을 보면 page 파라미터를 통해 include.php를 화면에 불러오는 것을 확인할 수 있다.

<img src="/assets/img/hacking/part2-3/3.png" alt="표사진"><br>
page 파라미터를 /etc/passwd로 넣으면 위와 같이 계정 정보가 출력되는 것을 확인할 수 있다. 즉 위에 네모 부분에서 File Includ가 일어나는 것을 확인할 수 있다.
여기서 LFI 취약점을 이용하면 위와 같이 개인정보 같은 중요한 정보들을 출력할 수 있다.

<hr>

### <b>■ RFI(Remote File Inclusion)이란?</b>
공격자가 악성 스크립트를 대상 웹 서버에 전달하여 해당 페이지를 통하여 전달한 악성코드가 실행 되도록 하는 것이다.

### <b>■ RFI(Remote File Inclusion) 취약점 공격 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux)
    - Virtual Box(DVWA) -공격 대상

<img src="/assets/img/hacking/part2-3/4.png" alt="표사진"><br>
cd 명령어를 이용해 /var/www/html 경로로 이동한뒤 leafpad를 이용해 test.html파일을 만들고 안에 위와 같이 적는다.

<img src="/assets/img/hacking/part2-3/5.png" alt="표사진"><br>
test.html페이지를 만들었으면 웹 서비스 apache2를 실행시킨다.

<img src="/assets/img/hacking/part2-2/2.png" alt="표사진"><br>
DVWA 사이트에 들어가서 security를 low로 설정해준뒤 왼쪽 메뉴에서 File Inclusion으로 들어간다.

<img src="/assets/img/hacking/part2-3/7.png" alt="표사진"><br>
File Inclusion으로 들어가서 page 파라미터에 http://[위에서 apache2 실행한 공격자 IP 주소]/test.html을 입력하면 위 그림과 같이
우리가 만든 test.html에 내용 Hello HTML~이 표시된다. 이 부분을 이용해서 공격을 할 것이다. 우리가 <a href="https://jjuseok.github.io/posts/hacking_part2-2/">파일업로드 취약점 게시글</a>에서 이용한 shell.php 파일을 이용할 것이다.

<img src="/assets/img/hacking/part2-3/8.png" alt="표사진"><br>
shell.php를 이용하기 위해서 home 경로에서 shell.php를 현재 경로에 복사해온다.

<img src="/assets/img/hacking/part2-3/10.png" alt="표사진"><br>
복사를 하고나서 파일업로드 취약점 공격했을때와 동일하게 공격자 PC에서 7777포트를 열어준다.

<img src="/assets/img/hacking/part2-3/9.png" alt="표사진"><br>
포트를 열었으면 위 경로에 아까 실습했던 것처럼 page 파라미터에 http://[위에서 apache2 실행한 공격자 IP 주소]/shell.php를 입력해 보자.

<img src="/assets/img/hacking/part2-3/11.png" alt="표사진"><br>
입력하고 포트 열었던 cmd 창으로 이동하면 위와 같이 접속이 되고 사용자 웹 쉘을 획득한 것을 볼 수 있다.
위와 같이 웹 쉘을 획득한 상태에서 피해자 컴퓨터에 명령어 사용이 가능한다. 여러 명령어를 사용해 피해자 컴퓨터를 조종할 수 있으며 여러 중요한 파일들도 볼 수 있다.