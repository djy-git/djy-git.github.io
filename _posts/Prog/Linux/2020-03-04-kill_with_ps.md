---
title: Kill process with ps
tags: Linux
---

```
$ pkill -9 -ef PROCESS_NAME
```

# Remarks
이 글은 [박연오님의 포스팅](https://bakyeono.net/post/2015-05-05-linux-kill-process-by-name.html)을 요약한 글입니다.

<!--more-->

---

일반적으로 process를 `kill`하기 위해서는 `ps`를 통해 pid를 찾은 다음 `kill PID` 처럼 사용하는데, 종료시켜야할 일련의 process의 수가 많아지면 하나하나 치기가 힘들죠. 이런 작업을 간단하게 해주는 방법이 몇 가지 있습니다.


## 1. Find PID then kill
```
$ ps r | grep PROCESS_NAME   // find PID (r: running process)
$ pgrep r PROCESS_NAME       // shortcut to print only PID
$ kill -9 PID
```


## 2. Kill with PROCESS_NAME
```
$ killall -9 PROCESS_NAME  // kill all process with PROCESS_NAME
```


## 3. Kill with PROCESS_NAME_PARAM (PROCES_NAME + PARAMETER)
```
$ pkill -9 r PROCESS_NAME_PARAM
```
