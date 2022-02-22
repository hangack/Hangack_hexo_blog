---
title: datetime 날짜와 시간
categories:
  - 연습
  - 파이썬
  - 모듈
tags:
  - 파이썬
  - datetime
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
date: 2022-02-04 02:14:30
---


# datatime

datetime 모듈은 특정 시간과 날짜를 불러오는 파이썬 내장 모듈이다.

## 날짜와 시간 함수

datatime 모듈을 사용하면 시간 날짜 UTC timezone을 불러올 수 있고, 내장 함수로 `data`, `time` 등을 사용해 날짜 혹은 시간만 지정하고 특정 시간대를 지정해 불러올 수도 있다.
```python
import datetime

print(datetime.date.today())
print(datetime.datetime.today())
print(datetime.time(12,59,33, microsecond=333333, tzinfo=datetime.timezone.utc))
```
    2022-02-03
    2022-02-03 03:36:07.407621
    12:59:33.333333+00:00


## strftime(원하는 형식으로 변경)

strftime을 사용하면 불러온 시간을 원하는 형식으로 바꿀 수 있다.
```python
print(datetime.datetime.today().strftime("%Y/%m/%d %H:%M:%S"))
```
    2022/02/03 03:40:36


# 외부링크
 - [datatime — 기본 날짜와 시간 형](https://docs.python.org/ko/3/library/datetime.html)