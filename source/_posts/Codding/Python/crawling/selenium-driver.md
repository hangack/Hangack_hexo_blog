---
title: selenium 사용하기
categories:
  - 연습
  - 파이썬
  - crawling
tags:
  - 파이썬
  - code
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
date: 2022-01-16 23:33:47
---
  
## 크롤링 문제 발생

[G2G](https://www.g2g.com/) 페이지를 크롤링하면서 원하는 html 구문이 [requests](https://docs.python-requests.org/en/latest/) 방식으로는 스크래핑이 안되서 이유를 찾아봤다.
g2g 페이지는 javascript를 활용, 동적 페이지로 구성된 녀석이라 페이지를 열어서 활성된 html 구문을 가져와야 원하는 정보를 받아올 수 있는 경우였다.


## Selenium

직접 페이지를 열기 위한 라이브러리 [selenium](https://www.selenium.dev/)의 파이썬(or 아나콘다) 설치를 진행한다.
```shell
$ pip install selenium
$ conda install selenium
```
나의 경우 venv 환경을 이용할 예정이라 venv 경로에서 bash를 이용해 `pip install` 해줬다.


### 브라우저 webdriver 설치

selenium을 받으면 끝이 아니라 selenium으로 html 구문을 받아오기 위해 webdriver를 받아와서 지정해줘야한다.

- [Chrome](https://sites.google.com/a/chromium.org/chromedriver/downloads)
- [Firefox](https://github.com/mozilla/geckodriver/releases)
- [Edge](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/)
- [Safari](https://webkit.org/blog/6900/webdriver-support-in-safari-10/)

사용중인 os 기준으로 driver를 다운받으면 되지만, chrome의 경우 chrome 버전에 맞춰서 받아주자.

난 비교적 깔린 확장프로그램이 적어 가벼운 Firefox로 진행했다.


### 사용하기


위에서 다운받은 webdriver를 압축해제 해주고 받은 브라우저에 맞춰서 driver를 지정해주자.

```python
from selenium import webdriver

driver = webdriver.Firefox(executable_path="webdriver 경로.exe")
url = "https://www.g2g.com/categories/new-world-coins"
driver.get(url)
html = driver.page_source
```
일반 [Firefox](https://www.mozilla.org/ko/firefox/new/)와 [Nightly 버전](https://www.mozilla.org/ko/firefox/channel/desktop/)이 같이 깔려있어서 그런지 Firefox Nightly 버전으로 열렸다.



불러온 html 구문을 BeautifulSoup, Scrapy와 같은 크롤링 라이브러리 명령어에 가져올 수 있다.

```python
from bs4 import BeautifulSoup

soup = BeautifulSoup(html)
```


#### tip

driver 명령어만 이용하면 url을 직접 넣어줘야하지만,
클릭, 새창에서 열기 등 다양한 명령어를 사용할 수 있다. 필요할 때 찾아볼 예정이다.


페이지 크롤링이 끝났고, 브라우저가 열려있을 필요 없다면 종료해주면 된다.

```python
driver.close()  # 탭 닫기
driver.quit()   # 창 닫기
```

## 외부링크
 - [Python Selenium 사용법](https://greeksharifa.github.io/references/2020/10/30/python-selenium-usage/)
 - [G2G javascript crawling](https://stackoverflow.com/questions/68355161/an-error-occurred-while-parsing-the-page-python)