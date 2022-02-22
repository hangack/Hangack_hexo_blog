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
  
# 크롤링 문제 발생

[G2G](https://www.g2g.com/) 페이지를 크롤링하면서 원하는 html 구문이 [requests](https://docs.python-requests.org/en/latest/) 방식으로는 스크래핑이 안되서 이유를 찾아봤다.
g2g 페이지는 javascript를 활용, 동적 페이지로 구성된 녀석이라 페이지를 열어서 활성된 html 구문을 가져와야 원하는 정보를 받아올 수 있는 경우였다.


# Selenium

직접 페이지를 열기 위한 라이브러리 [selenium](https://www.selenium.dev/)의 파이썬(or 아나콘다) 설치를 진행한다.
```shell
$ pip install selenium
$ conda install selenium
```
나의 경우 venv 환경을 이용할 예정이라 venv 경로에서 bash를 이용해 `pip install` 해줬다.


## 브라우저 webdriver 설치

selenium을 받으면 끝이 아니라 selenium으로 html 구문을 받아오기 위해 webdriver를 받아와서 지정해줘야한다.

- [Chrome(old)](https://sites.google.com/a/chromium.org/chromedriver/downloads), [Chrome(new)](https://sites.google.com/chromium.org/driver/)
- [Firefox](https://github.com/mozilla/geckodriver/releases)
- [Edge](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/)
- [Safari](https://webkit.org/blog/6900/webdriver-support-in-safari-10/)

사용중인 os 기준으로 driver를 다운받으면 되지만, chrome의 경우 chrome 버전에 맞춰서 받아주자.

난 비교적 깔린 확장프로그램이 적어 가벼운 Firefox로 진행했다.


## 사용하기


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


## 브라우저 종료

driver 명령어만 이용하면 url을 직접 넣어줘야하지만,
클릭, 새창에서 열기 등 다양한 명령어를 사용할 수 있다. 필요할 때 찾아볼 예정이다.

페이지 크롤링이 끝났고, 브라우저가 열려있을 필요 없다면 종료해주면 된다.

```python
driver.close()  # 탭 닫기
driver.quit()   # 창 닫기
```


## 로딩 대기

코드 실행 대기를 생각하면 `time` 모듈의 `sleep()`함수를 사용해 주어진 시간 동안 무조건 대기를 진행할 수 있다.

하지만 우리가 원하는건 무조건적인 대기가 아니라 html 코드를 불러오기 위해 브라우저 로딩이 끝날 때까지만 코드를 대기시키는 방법이다.


### Implicit Waits,암시적 대기

옵션 설정하듯 대기시간을 한번 설정하면 전역 적용된다.
bs4같은 모듈이 아닌 driver 라이브러리를 활용해 특정 요소를 찾을 때 활용할 수 있다.

```python
from selenium import webdriver

driver.implicitly_wait(10) # seconds

driver.get(URL)
driver.find_element_by_id(Elements)
```


### Explicit Waits, 명시적 대기

특정 조건이 만족할 때까지 지정된 시간 동안 대기하고, timeout된 경우 TimeoutException이 발생한다.

`expected_conditions` 함수의 조건이 만족할 때까지 기다리는 코드를 사용할 수 있다.

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

wait = WebDriverWait(driver, 30)
# 특정 요소를 찾을 수 있을 때까지
element = EC.presence_of_element_located((By.CLASS_NAME , "offers-bottom-attributes.offer__content-lower-items"))
wait.until(element)
```

동적 페이지의 경우 하나의 URL에서 구조가 바뀌는 경우도 있다.

이런 경우 클릭이 가능할 때까지 기다리는 함수를 사용할 수 있다.

```python
# 클릭이 가능할 때까지
element = EC.element_to_be_clickable((By.XPATH, '//a[@href="#!-1"]'))
```

아래의 조건들을 활용할 수 있다.

 - `title_is`
 - `title_contains`
 - `presence_of_element_located`
 - `visibility_of_element_located`
 - `visibility_of`
 - `presence_of_all_elements_located`
 - `text_to_be_present_in_element`
 - `text_to_be_present_in_element_value`
 - `frame_to_be_available_and_switch_to_it`
 - `invisibility_of_element_located`
 - `element_to_be_clickable`
 - `staleness_of`
 - `element_to_be_selected`
 - `element_located_to_be_selected`
 - `element_selection_state_to_be`
 - `element_located_selection_state_to_be`
 - `alert_is_present`

`try` ~ `finally` 구문을 활용하면 true인 경우 다음 단계로 넘어가는 코드를 활용할 수 있다.


## 외부링크
 - [Selenium with Python](https://selenium-python.readthedocs.io/)
 - [Python Selenium 사용법](https://greeksharifa.github.io/references/2020/10/30/python-selenium-usage/)
 - [G2G javascript crawling](https://stackoverflow.com/questions/68355161/an-error-occurred-while-parsing-the-page-python)