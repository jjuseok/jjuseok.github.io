---
layout: post
title: '[해킹 기초] 12. Kioprix_Level 1'
date: '2023-01-04 09:59:10 +0900'
description: 'Kioprix_Level 1'
categories: [HACKING,HACKING - Part.2]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: false
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ Kioprix_Level 1 공격 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux) - 공격자
    - Kioprix_Level 1 - 공격대상

- [공격 목표]
    - Kioprix_Level 1 root 권한 획득

- [공격 기법 참고 게시글]
    - [[해킹 기초] 4. 정보수집-Port Scan](https://jjuseok.github.io/posts/hacking_part1-4/)
    - [[해킹 기초] 6. 정보수집-취약점 검색(Search Sploit)](https://jjuseok.github.io/posts/hacking_part1-6/)

<img src="/assets/img/hacking/part2-6/2-1.png" alt="표사진"><br>
지금 가상머신으로 Kioprix_Level 1을 실행 시켜 놓은 상태이다. 이 서버의 root 권한을 획득하는게 이번 공격의 목표이다.
<hr>
<img src="/assets/img/hacking/part2-6/1.png" alt="표사진"><br>
일단 우리는 Kioprix_Level 1의 정보를 하나도 모르는 상태이기 때문에 
[저번 시간에 공부한 port scan](https://jjuseok.github.io/posts/hacking_part1-4/)을 활용해서 Kioprix_Level 1의 정보를 찾을 것이다. 위의 명령어를 간단하게 설명하자면  범위 내에서 포트가 열려있는 장비들을 출력하는 명령어이다. 이렇게 출력된 내용을 보면  Kioprix_Level 1의 IP를 알아낼 수 있다.
<hr>
<img src="/assets/img/hacking/part2-6/2.png" alt="표사진"><br>
Kioprix_Level 1의 IP를 알아냈으면 다시 nmap을 활용해서 해당 포트의 서비스/버전 정보를 확인하는 명령어를 이용해서 결과를 result.txt로 저장한다. [이 명령어도 저번 시간에 공부한 명령어이다.](https://jjuseok.github.io/posts/hacking_part1-4/)
<hr>
<img src="/assets/img/hacking/part2-6/4.png" alt="표사진"><br>
nmap 결과가 result.txt로 만들어졌으면 cat 명령어를 이용해서 result.txt 파일의 내용을 살펴보면 위와 같은 포트를 사용하고 어떤 종류의 서비스를 사용하는 것을 볼 수 있는데 우리는 이번 시간에 443/tcp mod_ssl의 취약점을 공격할 것이다. 여기서 Apache 1.3.20 / Red-Hat / Linux / mod_ssl 2.8.4 버전을 사용하는 것을 알아 냈다.
<hr>
<img src="/assets/img/hacking/part2-6/5.png" alt="표사진"><br>
위에서 발견한 정보를 바탕으로 [searchsploit으로 mod_ssl 1.3.20 취약점을 검색했다.](https://jjuseok.github.io/posts/hacking_part1-6/) searchsploit도 저번 시간에 알아봤으니깐 오늘은 간단하게 넘어갈 것이다. 검색하면 아래와 같이 취약점 3개가 나오는데 지금 시간에는 3번째 취약점을 공격할 것이다. 공격툴의 이름은 47080.c 이며 이 파일의 위치를 찾기위해 find 명령어로 찾고 현재 경로에 복사해서 가져왔다. 저 툴을 실행하기 전에 apt-get을 이용해 libssl-dev를 설치해야 오류가 안나온다. 설치 후 gcc를 이용해서 47080.c 파일을 컴파일 했다.
<hr>
<img src="/assets/img/hacking/part2-6/6.png" alt="표사진"><br>
컴파일 한 후 파일을 실행해보니 사용 설명과 함께 옵션이 나온다. 사용방식은 ./47080 target box [port] [-c N]이며 -c 옵션을 잘 모르면 40 ~ 50 사이의 수를 넣으면 된다고 나와있다.
<hr>
<img src="/assets/img/hacking/part2-6/7.png" alt="표사진"><br>
옵션을 내리다 보면 우리가 해킹 대상 정보수집 단계에서 발견한 apache-1.3.20 버전을 공격하려면 0x6b 옵션을 쓰면 된다.
<hr>
<img src="/assets/img/hacking/part2-6/8.png" alt="표사진"><br>
사용방식대로 ./47080 0x6b [대상 IP] -c 40을 실행시켰다. 실행시키니깐 아래와 같이 shell 권한을 탈취 해서 명령어가 실행이 가능하다. 그리고 우리의 공격 목표인 root 권한을 획득에 성공했다.
<hr>