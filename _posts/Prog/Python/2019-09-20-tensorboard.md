---
layout: article
title: Tensorboard in remote server
tags: Python
sidebar:
  nav: docs-en
---

### Notation
- IP: Server IP
- ID: Server ID
- PORT: Client에서 사용하고자 하는 포트번호
- LOG: Tensorboard log 파일이 있는 directory


### Linux server에 접속하여 tensorboard를 실행시킨 결과를 Windows에서 보기
1. Windows cmd

        > ssh -L PORT:localhost:6006 ID@IP

2. Server ssh

        $ tensorboard --logdir=LOG

3. Windows internet browser

        http://localhost:PORT
