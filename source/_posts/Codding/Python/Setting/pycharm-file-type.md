---
title: 파이참 파일 확장자 타입 변경하기
categories:
  - 연습
  - 파이썬
  - 설정
tags:
  - 파이썬
  - 파이참
  - 설정
sidebar:
  left:
    sticky: true
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
toc: true
thumbnail: /thumbnails/CS/pycharm.svg
date: 2021-12-11 09:34:18
---


파이참에서 파일을 만들다보면 확장자명을 지정하지 않고 파일을 만드면서 text 형식으로 지정하는 경우가 있다.
보통의 경우 auto-detected이지만, 잘못 지정하면 확장자를 바꿔도 기존에 지정한 형식으로 읽어온다.
이 경우 지정한 형식을 제거해주면 된다.


![](\images\2112\pycharm-filetype\filetypes.png)

Setting - File Types