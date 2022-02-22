---
title: unique 요소만 포함하는 set
categories:
  - 연습
  - 파이썬
  - 기초
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
date: 2022-02-07 15:45:16
---
  
특정 집합을 만들다보니 같은 값이 저장되지 않는 리스트를 만들 필요가 생겼다.
set() 형식을 사용하면 unique한 객체만 포함하는 집합을 만들 수 있다.

단, 사용하려면 `set()`으로 객체를 초기화 해야한다.

```python
set = set([1,1,1,1,2,3,10,10,31])
print(set)
```
    {1, 2, 3, 10, 31}

dictionary와 동일한 `{`, `}`로 사용되지만 dictionary와 다르게 key가 없는 list 형식이다.

# 외부링크
 - [set(집합)](https://wikidocs.net/16044)