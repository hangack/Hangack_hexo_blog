---
title: 파이참, 파이썬 인코딩 설정
categories:
  - 연습
  - 파이썬
  - 설정
tags:
  - 파이썬
  - 파이참
  - 설정
widgets:
  - type: profile
    position: left
    social_links:
        Github:
            icon: fab fa-github
            url: 'https://github.com/hangack'
        Youtube:
            icon: fab fa-youtube
            url: 'https://www.youtube.com/channel/UCQuHrr7-mBtutw9V94XGH-g'
        Twitch:
            icon: fab fa-twitch
            url: 'https://www.twitch.tv/hangack'
        Steam:
            icon: fab fa-steam
            url: 'https://steamcommunity.com/id/HanGack/'
  - type: toc
    position: left
    index: false
  - type: categories
    position: left
sidebar:
  left:
    sticky: true 
toc: true
thumbnail: /thumbnails/CS/pycharm.svg
date: 2021-12-08 09:04:22
---


어떤 작업환경을 사용하든 가능하다면 `UTF-8` 포멧으로 작업하는걸 추천한다.

pycharm에서도 인코딩 방식 변경을 지원함.

file - setting - editor - file encodings에서 Global Encoding이 `UTF-8`이 아니라면 변경해주자.

프로젝트 인코딩과 속성 파일 인코딩 방식은 OS가 윈도우라면 새 프로젝트를 열 때 마다 기본값으로 돌아갈 것이다.
필요한 설정이 아니라면 크게 신경쓰진 말자.

![encoding](\images\2112\pycharm-encoding\utf-8.png)


※ 코드 파일 맨 윗단에 아래 주석을 추가하면 자동 UTF-8 인코딩 해준다.

```python
# -*- coding: utf-8 -*-
```

pycharm에서 UTF-8로 변경했고 python 3++를 사용중이기에 추가할 필요는 없지만 작업 파일을 공유하거나 먼 미래에 열어볼 나를 위해 추가한다.