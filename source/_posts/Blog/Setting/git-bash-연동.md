---
title: git bash 연동 및 연동해제
categories:
  - 블로그
  - 설정
tags:
  - 블로그
  - 설정
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
date: 2021-11-12 06:48:34
---
  
## Git Bash: GitHub 연동

github와 컴퓨터를 연동해주는 터미널인 git bash를 이용하기 위해 우선 git bash에 연동시킬 user명과 계정을 확인시켜줄 필요가 있다.
```
$ git config --global user.name "user name"
$ git config --global user.email email@mail.com
```

위 명령어를 입력하고서 계정 연동이 필요한 작업을 하게되면 웹 브라우저 혹은 code를 통한 인증을 요구한다.
![GitHub 연동](/images/2111/GitBash_connect/연동.png)


## Git Bash: 연동해제

일반적으로 GitHub 관리는 개인 컴퓨터에서 진행하겠지만, 예외적으로 외부 컴퓨터에서 작업하게될 경우가 있을 수 있다.
이런 경우 로그아웃을 해야하지만, 웹 페이지도 아닌 로컬에 입력된 정보에 연동을 끊는 방법이 필요하다.

### 자격증명제거

[제어판] - [사용자 계정] - [자격 증명 관리] - [Windows 자격 증명] 순으로 진입하면 Git~ 으로 연동된 자격 증명을 확인 할 수 있다.
![window 자격증명](/images/2111/GitBash_connect/연동해제.png)

자격 증명 [제거]를 클릭하면 Git Bash에서 연동은 우선 해제된다.

하지만 문제가 하나 남게되는데, 첫 연동 이후엔 연동 정보가 캐쉬되어 이메일 추가 인증을 요구하지 않는다.

### cookie 제거

자격 증명을 제거한 다음 hithub 엑세스에 사용한 웹 브라우저의 캐쉬를 삭제하면 다음 연동 때 cookie로 남긴 데이터가 없기 때문에 추가 인증을 요구한다.
![쿠키 제거](/images/2111/GitBash_connect/del_cookie.png)

외부에서 로그인 했을 경우엔 시크릿 모드를 쓰거나 발자취를 지우는게 보안상 중요.