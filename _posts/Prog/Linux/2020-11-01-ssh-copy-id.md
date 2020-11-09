---
layout: article
title: Ubuntu ssh setting
tags: Linux
sidebar:
  nav: docs-en
---

# Remarks
이 글은 [https://jimnong.tistory.com/713](https://jimnong.tistory.com/713)의 글을 참조하여 작성되었습니다.

<!--more-->

---

### 1. `openssh-server` 설치

        $ sudo apt-get update
        $ sudo apt-get install openssh-server
        $ dpkg -l | grep openssh  // 설치 확인

<br>
### 2. ssh server service 시작

        $ sudo service ssh start

<br>
### 3. 확인

        $ service --status-all | grep +  // 실행 중인 service 목록
        $ sudo netstat -antp  // Port 번호 확인

<br>
### 4. ssh에서 root 계정 사용할 수 있게 하기

        $ sudo vi /etc/ssh/sshd_config

          // sshd_config
          ...
          PermitRootLogin yes
          ...

        $ sudo service ssh restart
