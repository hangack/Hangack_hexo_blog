---
title: BeautifulSoup find와 select
categories:
  - 연습
  - 파이썬
  - crawling
tags:
  - 파이썬
  - code
  - bs4
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
date: 2022-01-20 16:13:46
---


request 혹은 selenium으로 html 코드를 뜯어왔다면 태그를 특정지어서 불러올 데이터를 지정해줘야한다.
이 때, 사용할 수 있는 모듈 중 하나가 BeautifulSoup와 Scrapy다.

# BeautifulSoup

bs4를 설치하고 BeautifulSoup를 사용한다.

```shell
$ pip install beautifulsoup4
```

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(html)
```

기본적으로 태그를 식별하는 방법은 `find`와 `select`가 있다.

## find

find의 경우 `tag`의 `id`, `class` 등을 지정해서 찾을 수 있다.

python에서는 `class`가 따로 쓰이므로 class 요소를 지정할 때는 `class_`로 넣어줘야한다.

```python
soup.find("strong")
soup.find("a", class_="cdp_i")
soup.find(class_="cdp_i")
soup.find("div", id="hide")
```

class와 id같은 요소를 지정해서 불러오기 때문에 특정 상황에선 정확도가 높다.


### find_all

`find()`의 경우 하나의 태그 html만 불러올 수 있는대, `find_all()`을 사용하면 조건을 만족하는 모든 html을 list 형식으로 받아온다.

```python
soup.find_all("a")
```


## select

select를 사용하면 `find_all()`처럼 list로 받아올 수 있다.

```python
soup.select("a")
soup.select("a.cdp_i")
soup.select(".cdp_i")
soup.select("div#hide")
```

또한, 중첩 tag를 선택할 수도 있다.

```python
soup.select("div#hide > a.cdp_i")
```
div 태그의 id="hide" 내부의 a 태그의 class="cdp_i"인 html을 불러온다.

select의 경우 메모리 소모량과 수행시간이 find와 비교하면 효율적이다.


### select_one

find의 경우와 반대로 가장 앞의 하나만 불러오기 위해선 `select_one`을 사용하면된다.

```python
soup.select_one("a")
```


# 외부링크
 - [Beautiful Soup Documentation](https://beautiful-soup-4.readthedocs.io/en/latest/#)