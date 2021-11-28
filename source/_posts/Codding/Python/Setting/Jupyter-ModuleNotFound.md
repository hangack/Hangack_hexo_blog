---
title: Jupyter ModuleNotFound 에러 (feat.plotly)
categories:
  - 연습
  - 파이썬
  - 설정
tags:
  - 파이썬
  - 쥬피터
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
thumbnail: /thumbnails/CS/jupyter.svg
date: 2021-11-09 15:04:15
---
  
### 0. 모듈 에러 확인

Plotly를 외부 컴퓨터에서 잘 사용하다가 집에서 모듈을 설치하기 위해 [plotly](https://plotly.com/python/getting-started/)에서 안내된 install 명령어 대로 설치하고 jupyter로 사용하려니 아래와 같이
```
ModuleNotFoundError: No module named 'plotly'
```
<img src="\images\2111\ModuleNotFound\PLOTLY 1.png">

오류를 뱉어내더라.

cmd에서 plotly를 확인해도 깔려 있는데, 막상 로컬 소프트인 jupyter에서 사용하려니 경로를 못 찾아가는 느낌이라 주피터 path 경로 문제인가 했었다.

구글링해서 내린 결론은 일반 cmd로 모듈을 다운받으면 python에 대한 모듈로 다운받는게 문제였다.

"jupyter는 파이썬 아니냐?"
하겠지만 jupyter에서 import로 참조되는 모듈들은 Anaconda 설치 경로에서 참조되기 때문에 python에 모듈을 설치하는 경우는 아무 의미 없는 작업이된다.

### 1. Anaconda Prompt

결국 로컬 jupyter에서 외부 모듈을 적용시키기 위해선 anaconda 경로로 설치할 필요가 있고, 많은 방법 중 하나가 Anaconda Prompt다.

아나콘다 경로 혹은 시작화면 앱 찾기에서 Anaconda Prompt를 실행하고
<img src="\images\2111\ModuleNotFound\PLOTLY 2.png">

### 2. plotly 설치

Plotly 설치를 Anaconda prompt에서 진행한다.
```
> pip install plotly==5.3.1
```
<img src="\images\2111\ModuleNotFound\PLOTLY 3.png">

### 3. Jupyter 모듈 오류 해결

anaconda 로컬 소프트인 jupyter notebook에서 정상적으로 import되는 걸 확인할 수 있다.
<img src="\images\2111\ModuleNotFound\PLOTLY 4.png">

## 그렇다면 구글, 당신이 신이란거야?
 - [anaconda plotly](https://stackoverflow.com/questions/42521772/importerror-no-module-named-plotly-plotly-in-linuxmint17-3/48774224#48774224)