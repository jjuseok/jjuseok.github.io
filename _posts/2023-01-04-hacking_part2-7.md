---
layout: post
title: '[해킹 기초] 13. 메타스플로잇(Metasploit)'
date: '2023-01-04 09:59:10 +0900'
description: 'Kioprix_Level 1'
categories: [HACKING,HACKING - Part.2]
image: /assets/img/1/hacking.png
tags: [hacking]
toc: false
---
<a text-size="1px" target="_blank" href="https://icons8.com/icon/5503/hacking">Hacking</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

### <b>■ 메타스플로잇(Metasploit)이란?</b>
메타스플로잇(Metasploit)이란 온갖 취약점과 메타 데이터를 관리하는 프레임워크다. 즉 취약점 공격을 사용할 수 있도록 도구를 제공해주며 도구를 이용해 해킹을 쉽게 할 수 있도록 도와주는 해킹 테스트 도구이다.

### <b>■ 메타스플로잇(Metasploit)를 이용해 Kioprix_Level 1 공격 실습</b>
- [실습 환경]
    - Virtual Box(Kali Linux) - 공격자
    - Kioprix_Level 1 - 공격대상

- [공격 순서]
    1. nmap (정보수집)
    2. searchsploit (버전확인)
    3. metasploit (공격)

- [공격 목표]
    - samba 취약점을 이용한 Kioprix_Level 1 root 권한 획득

<hr>
<img src="/assets/img/hacking/part2-7/1.png" alt="표사진"><br>
metasploit을 실행시키려면 msfconsole 명령어를 입력하면 된다. 위와 같이 msf6> 프롬포트가 뜨면 정상적으로 실행된 것이다.
<hr>
<img src="/assets/img/hacking/part2-7/2.png" alt="표사진"><br>
우리는 이전 게시물에서 Kioprix_Level 1에 대한 포트 스캔을 진행하고 result.txt파일로 결과를 저장했다. result.txt를 살펴보면 위와 같이 공격 대상 PC가 139/tcp samba를 사용하는 것을 알았다. 오늘은 samba 취약점을 이용해 공격을 할 것이다. 공격자는 samba 취약점을 검색하려고 하는데 정확한 버전을 모르고 있다.
<hr>
<img src="/assets/img/hacking/part2-7/3.png" alt="표사진"><br>
버전 정보를 확인하기 위해 위와 같이 search smb vesion 명령어를 이용해 smb vesion을 알아내는 모듈을 검색해봤다.
<hr>
<img src="/assets/img/hacking/part2-7/4.png" alt="표사진"><br>
검색하니 smb version을 알아낼 수 있는 모듈이 나왔다. 우리는 이 모듈을 사용해서 smb version을 알아낼 것이다. 이 모듈을 사용하려면 use auxiliary/scanner/smb/smb_version
명령어를 입력하면 모듈을 사용할 수 있다.
<hr>
<img src="/assets/img/hacking/part2-7/5.png" alt="표사진"><br>
use 명령어를 이용해 해당 모듈을 로드시킬 수 있으며 위와 같이 모듈 이름이 나오고 info를 이용해 해당 모듈의 설명을 확인할 수 있다.
<hr>
<img src="/assets/img/hacking/part2-7/7.png" alt="표사진"><br>
모듈을 로드 했으면 show options 명령으로 옵션을 확인할 수 있으며 Required 부분에 yes 라고 나와 있으면 해당 부분의 Current Setting에 값이 무조건 필요하다는 의미이다. 하지만 RHOSTS라는 name에 Current Setting 값이 비어있으므로 해당 되는 값 공격 대상 PC(Kioprix_Level 1)의 IP를 입력하면 된다. setting 하는 방법은 set rhosts [Kioprix_Level 1 IP]를 입력하면 되고 다시 show options를 해보면 RHOSTS setting 값이 들어간 것을 확인할 수 있다.
<hr>
<img src="/assets/img/hacking/part2-7/8.png" alt="표사진"><br>
필요한 setting 값을 다 넣었으면 run을 통해 해당 모듈을 실행 시킬 수 있다. 우리가 실행한 모듈은 위에서도 말했듯이 공격 대상 PC(Kioprix_Level 1)의 smb version 정보를 확인하는 모듈이다. 해당 모듈을 run 명령어를 통해 실행 시키면 위와 같이 공격 대상 PC(Kioprix_Level 1)의 samba version을 알아낼 수 있다. 우리가 samba version을 확인 했으면 그 버전에 맞는 취약점을 알아낸 뒤 공격할 것이다.
<hr>
<img src="/assets/img/hacking/part2-7/9.png" alt="표사진"><br>
이번에는 알아낸 samba version에 대한 취약점을 검색할 것이다. searchsploit samba 2.2.1a 명령어를 이용해 해당  버전의 취약점을 검색 해봤다. 검색해보니 4개의 취약점이 나오는데 오늘은 trans2open Overflow 취약점을 이용해 공격할 것이다. 
<hr>
<img src="/assets/img/hacking/part2-7/10.png" alt="표사진"><br>
trans2open Overflow 취약점을 공격하기 위해 해당 취약점에 대한 모듈이 있나 search 명령어로 검색을 해봤더니 위와 같이 Linux 운영체제에 맞는 모듈을 발견할 수 있었다. 이 모듈을 통해 취약점을 공격할 것이다.
<hr>
<img src="/assets/img/hacking/part2-7/11.png" alt="표사진"><br>
이 모듈을 사용하기 위해 위와 같이 use 명령어를 사용하고 모듈이 바뀐 것을 확인했다. 이 모듈에 대한 정보를 확인하려면 위에서 말했듯이 info 명령어를 입력하면 모듈에 대한 정보를 확인할 수 있다.
<hr>
<img src="/assets/img/hacking/part2-7/12.png" alt="표사진"><br>
정보를 확인하고 이 모듈도 마찬가지로 show options 명령을 이용해 필요한 옵션을 확인해보자. 옵션을 확인해봤더니 RHOSTS setting 값이 비어있다. 이 모듈 또한 RHOSTS setting 값이 무조건 필요하며 set rhosts[공격 대상 IP] 명령을 이용해 rhosts에 값을 넣어주자. 넣었으면 다시 show options로 확인할 수 있다. 확인해보니 공격 대상 IP가 잘 들어갔다. 여기서 Payload options 부분은 쉽게 말해서 공격자 setting 값이다.
<hr>
<img src="/assets/img/hacking/part2-7/13.png" alt="표사진"><br>
option에 필요한 setting 값을 다 넣었으면 run을 통해 해당 모듈을 실행시키자. 실행 시켰더니 위와 같이 Meterpreter session 1 closed. Reason: Died라는 문구가 떴다. Meterpreter은 메타스플로잇(Metasploit) 전용 쉘인데 이것을 이용하면 공격 대상 PC에 정보를 알아낼 수 있는데 위 문구를 통해 여기서 이용할 수 없다는 것을 알았다. 이런 상황에서 공격자는 Payload를 바꿔줘야 된다.
<hr>
<img src="/assets/img/hacking/part2-7/14.png" alt="표사진"><br>
payload를 reverse shell로 바꿔주려고 한다. show payloads를 입력해 payloads 목록을 확인하고 33번에 있는 payload로 바꿔줄 것이다.
<hr>
<img src="/assets/img/hacking/part2-7/15.png" alt="표사진"><br>
payload를 바꿔주기 위해 set 명령어를 사용해 reverse shell payload로 바꿔줬다. 바꾸고 show option을 이용해 살펴보면 공격자 부분에서 Payload가 바뀐것을 확인할 수 있다.
<hr>
<img src="/assets/img/hacking/part2-7/16.png" alt="표사진"><br>
여기까지 정상적으로 했으면 모든 공격의 준비가 끝났다 바로 run을 입력해 모듈을 실행하자. 실행하면 위와 같이 모듈이 공격을 실행하고 공격에 성공하면 공격대상(Kioprix_Level 1)의 root 쉘을 획득한 것을 볼 수 있다. 여기까지 메타스플로잇(Metasploit)을 이용한 공격을 알아봤다.
<hr>