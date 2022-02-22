---
title: "g2g-crwaling01: 크롤링 g2g 종목 선정"
categories:
  - 연습
  - 파이썬
  - crwaling_G2G
tags:
  - 크롤링
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
thumbnail: /thumbnails/CS/selenium.svg
date: 2022-01-23 04:37:44
---

현거래 매물 크롤링을 통해 얻을 수 있는 정보는 간단하게 가격 범위와 판매자 인원으로 볼 수 있다.

판매 가격은 대쉬보드로 활용할 수 있을거 같다.

하지만 결국 어느 시점에 게임(혹은 신규 컨텐츠)의 수명이 어느 순간까지 지속되는지 예측하는 등 프로모션, 마케팅적으로 아웃풋이 나오는게 중요하다.
따라서 신규 컨텐츠 출시 간격이 나름 규칙적인, 그리고 신규 컨텐츠 발매마다 서버가 초기화되서 재화 가치도 고정되지 않는 게임인 POE에 대한 현거래 data를 크롤링하기로 했다.

전 세계가 공유하고 모드만 바뀌는 서버 구성이므로 모든 서버를 수집할 예정이고, 시각화 혹은 예측 모델을 만들 때 업자 매물을 제거하기 편하게 리그가 종료된 시점에도 수집을 계속한다.

신규 컨텐츠가 나올 때 항상 20:00 UTC(05:00 KOR)에 서버가 열리므로 1시간 뒤인 새벽 6시에 매일 수집한다.


# 외부링크
 - [G2G](https://www.g2g.com/)
 - [Path of Exile](https://www.pathofexile.com/)
 - [POE League](https://pathofexile.fandom.com/wiki/League)