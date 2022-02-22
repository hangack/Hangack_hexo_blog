---
title: "g2g-crwaling00: javascript 동적페이지 크롤링"
categories:
  - 연습
  - 파이썬
  - crwaling_G2G
tags:
  - 크롤링
  - 파이썬
  - selenium
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
date: 2022-01-17 08:04:22
---
  
현거래 매물 거래 현황을 수집하려 한다.
전 세계를 대상으로하는 게임의 거래 데이터를 수집할 예정이니 세계 규모의 사이트 중 유명한 현거래 사이트인 [G2G](https://www.g2g.com/)를 크롤링할 예정이다.

G2G를 크롤링 하는데 request로 html을 가져오니 사이트 구조만 긁어오고 텍스트 내용이 들어간 태그들은 가져오지 못했다.

문제는 request의 경우 사이트에서 바로 html 코드를 긁어오기 때문에 유저의 행동에 따라 혹은 서버에서 요청을 받고 정보를 불러오는 javascript 동적페이지에 대한 대응을 할 수 없던거였다.

# my work
 - [selenium 사용하기](https://hangack.github.io/2022/01/16/Codding/Python/crawling/selenium-driver/)
 - github: [project](https://github.com/hangack/project-green/tree/main/crawling-g2g)
 - [crawl_URL_boost.py](https://github.com/hangack/project-green/blob/main/crawling-g2g/source/crawl_URL_boost.py)

# 외부링크
 - [G2G](https://www.g2g.com/)