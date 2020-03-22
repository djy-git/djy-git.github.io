---
title: Noise reduction
tags: Etc
---

## 1. Audacity를 사용한 noise reduction 음성 파일 생성
1. [Audacity](https://www.audacityteam.org/download/) 다운로드
2. 만약 AAC 코덱을 사용하는 경우,  
2.1. Audacity 실행 후 **Ctrl + P**로 `환경설정` 창을 띄우고 `라이브러리` 항목에서 `FFmpeg 라이브러리: 다운로드`를 눌러 다운로드 (Windows의 경우 다음 링크로 다운받을 수 있다. [FFmpeg library](https://lame.buanzo.org/ffmpeg-win-2.2.2.exe))  
2.2. 기본 설정된 위치에 설치하면 자동으로 라이브러리를 잡아내기 때문에 `확인`을 눌러 `환경설정` 창에서 나온다.
3. 노이즈가 포함된 음성파일 혹은 영상파일을 drag & drop하여 빈 창에 올려놓는다.
4. 노이즈만 포함된 영역을 drag하여 선택한다.
5. **Ctrl + G**로 노이즈의 profile을 저장한다.
6. **Ctrl + A**로 전체 영역을 선택하고 **Ctrl + R**로 전체 영역에서 노이즈를 제거한다.
6.1. 4 ~ 6 에서 사용하는 shortcut은 `효과(C)` 항목의 `노이즈 리덕션 (잡음 감쇄)` 항목에서 확인할 수 있다.
7. 제대로 노이즈가 제거되었는지 확인하고 `파일(F)` 항목의 `내보내기` 항목에서 원하는 format으로 음성파일을 생성한다. (영상파일을 내보낼 수는 없음)


## 2. 팟플레이어를 사용한 추가적인 noise reduction
1. Audacity로 생성한 음성파일을 불러온다.
2. 영상파일에 불러오는 경우,
2.1. Drag & drop 으로 `외부 오디오 불러오기` 를 선택한다.
2.2. **Alt + A**로 불러온 오디오를 선택한다.
3. **Shift + N**으로 `노말라이저`를 추가하여 소리를 증폭시키고, **Shift + D**로 `잡음 제거` 옵션을 추가하면 조금 더 깔끔한 음성을 들을 수 있다.
