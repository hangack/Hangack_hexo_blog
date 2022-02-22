---
title: G2G poe 현거래 매물 수집시작
categories:
  - 연습
  - 파이썬
  - crwaling_G2G
tags:
  - 파이썬
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
thumbnail: /thumbnails/CS/python.svg
date: 2022-02-07 12:13:40
---


저번 토요일(02/05) poe 리그 시작일에 맞춰 한국시간 06시마다 매일 현거래 매물 데이터를 postSQL과 GBQ에 수집중이다.

![postSQL](/images/2202/g2g-poe-수집/postSQL.png)

[pandas_gbq python과 google bigquery 연동하기](https://hangack.github.io/2022/02/16/Codding/Python/SQL/pandas_gbq-python-google-bigquery/)

![GBQ](/images/2202/g2g-poe-수집/GBQ.png)

2, 3 시즌 이상 데이터가 쌓이면 반복되는 데이터로 머신 러닝을 돌려 유저가 빠지는(혹은 매물이 폭락하는) 기간을 예상할 수 있을 것이다.

그 전에 [google data studio](https://marketingplatform.google.com/about/data-studio/?utm_source=google&utm_medium=cpc&utm_campaign=japac-KR-all-en-dr-bkws-all-all-trial-b-dr-1009882&utm_content=text-ad-none-none-DEV_c-CRE_308452914459-ADGP_Hybrid+%7C+BKWS+-+PHR+%7C+Txt+~+Data+Analytics+~+Google+Data+Studio_Data+Studio-KWID_43700065777624269-kwd-355732973731&userloc_1009863-network_g&utm_term=KW_google%20datastudio&gclid=Cj0KCQiAmKiQBhClARIsAKtSj-l71qfnWEwmx4uDL4V0iXKQQpyZ-o_Bbdg4ceQbT3errRfqtEhthokaAgMcEALw_wcB&gclsrc=aw.ds)를 이용해서 대쉬보드도 관리할 예정이다.

