---
layout: article
title: Tensorboard using remote server
tags: Python
sidebar:
  nav: docs-en
---

<!--more-->

### Notation
- IP: Server IP
- ID: Server ID
- PORT: Client에서 사용하고자 하는 포트번호
- LOG: Tensorboard log 파일이 있는 directory


### Linux server에 접속하여 tensorboard를 실행시킨 결과를 Windows에서 보기
1. CMD in Windows

        > ssh -L PORT:localhost:6006 ID@IP

2. ssh server

        $ tensorboard --logdir=LOG

3. Internet browser in Windows

        http://localhost:PORT
