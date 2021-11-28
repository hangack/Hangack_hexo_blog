---
title: Pycharm 터미널 git bash로 변경하기
categories:
  - 블로그
  - 설정
tags: 
  - 블로그
  - 설정
  - 파이썬
  - git
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
thumbnail: /thumbnails/CS/git.svg
date: 2021-10-31 12:01:42
---

Github 업로드와 blog 작업을 위해 pycharm을 사용하고 있기 때문에 pycharm 터미널을 Windwos cmd에서 git bash로 변경할 필요가 생겼다.

### git 설치경로 파악하기

우선 git bash(혹은 sh)를 불러오기 위해 git 설치경로를 파악해야한다.
내 경우는 E 드라이브에 설치했기에 `E:\Sadness\Git`가 Git 경로다.

### Terminal 변경하기

pycharm 설정에서
`[settings] - [Tools] - [Terminal]` 경로에서 
`[Application Settings] - [Shell path: ]`를 아래의 두줄 중 하나로 변경해준다.
```
"(git경로)\bin\bash.exe" --login
"(git경로)\bin\sh.exe" --login
```
![Shell path](/images/2111/Pycharm_Terminal_git/PTG.png)

`Shell integration`과 `Activate virtualenv`가 체크 해제되어있다면 체크해주자.

설정이 끝나면 Pycharm 하단 Terminal에서 git bash를 기본 값으로 사용하게된다.


## 외부링크
 - [PyCharm 터미널 설정](https://opentutorials.org/course/3718/24657)