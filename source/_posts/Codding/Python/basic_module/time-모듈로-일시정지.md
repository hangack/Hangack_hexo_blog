---
title: time 모듈로 일시정지
categories:
  - 연습
  - 파이썬
  - 모듈
tags:
  - 파이썬
  - time
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
date: 2022-02-02 22:22:22
---
  
python 내장 함수인 `time` 모듈을 사용하면 시간 관련 추출이나 간섭을 할 수 있다.

그 중 이번에 내가 사용할 함수는 `sleep()` 함수로 지정한 시간 단위만큼 프로그램 실행 중간에 딜레이를 줄 수 있다.

특히 이번에 크롤링 중인 페이지가 동적페이지에 하나의 URL에서 클릭으로 HTML 코드만 바뀌는 옵션이 들어가 selenium만으로 크롤링하면 때때로 에러가 발생했다.

```python
import time

time.sleep(3)
```
을 사용하면 코드 중간에 3초간 딜레이 줄 수 있다.


# 외부링크
 - [time — 시간 액세스와 변환](https://docs.python.org/ko/3/library/time.html)