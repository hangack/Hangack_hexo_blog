---
title: 파이참 가상환경 생성
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
date: 2021-12-09 14:13:12
---

## 가상환경

라이브러리를 불러오다보면 의존성 패키지의 과거 버전이 필요할 때가 있다.
모든 패키지에 대응할 수는 없으니 파이썬이나 해당 패키지를 재설치 혹은 Downgrade를 진행해야 할 것이다.
위 문제를 해결할 수 있는 방법이 여러 파이썬을 생성해 각각 환경에 맞는 패키지를 설치해 따로 불러오는 방법으로 **가상환경**이라 한다.

### 가상환경 생성

#### 설정에서 생성하기

프로젝트를 생성하고 코드 작업을 진행하다 버전 에러가 났을 때,

Files - Settings - Project: <dir> - Python Interpreter 에서 `Add...` 를 눌러 추가할 수 있다.

![](\images\2112\pycharm-venv\env-setting1.png)

가장 기본적인 Venv를 설치할 수 있다. anaconda 설치가 됐다면 conda 환경도 추가할 수 있지만, 기본적인 파이썬 Venv 설치를 진행할 예정.
파이썬 exe 경로와 가상환경 dir 경로를 잘 확인해주자

![](\images\2112\pycharm-venv\env-setting2.png)


#### 프로젝트와 같이 생성하기

보통의 경우는 파이참에서 프로젝트를 생성하며 가상환경 설치를 진행할 것이다.

![](\images\2112\pycharm-venv\env-setting2-2.png)


#### 터미널에서 생성하기

파이참같은 개발환경을 사용하지 못하고 리눅스 등 환경의 터미널에서 생성해야할 경우는 [venv — 가상 환경 생성](https://docs.python.org/ko/3.8/library/venv.html)를 참조한다.


## 패키지 설치

파이썬 가상환경을 생성했다면 사용할 패키지를 설치하면 된다.

정상적으로 설치했다면 문제 없겠지만 어느 파이썬을 참조하고 있는지 터미널에서 확인해보자.

```shell
 # window
$ where python
 # mac, linux .ect
$ which python
```

![](\images\2112\pycharm-venv\where-python.png)


가상환경을 참조하지 못하고 있다면 아래 명령어로 (venv) 강제 진입해보자.

```shell
 # window
$ source ./venv/Scripts/activate
 # mac, linux .ect
$ source ./venv/bin/activate
```


### 설정 interpreter에서

파이참 같은 경우엔 Python Interpreter - install 버튼을 선택해 설치할 패키지와 버전을 선택할 수 있다.

![](\images\2112\pycharm-venv\env-setting4.png)


### requirements.txt

버전을 일일히 기억하고 있기도 뭐하고 설치할 패키지가 많다면 하나하나 설치하는 것도 일이다.

[pycaret](https://github.com/pycaret/pycaret/blob/master/requirements.txt)같은 패키지를 보면 `requirements.txt`로 관리한다.

텍스트 파일에 원하는 패키지와 버전을 입력했다면 pip 명령어로 한번에 설치를 진행할 수 있다.

```shell
$ pip install -r requirements.txt
```


## Jupyter `ipynb`에서 가상환경 사용

가상환경 이름과 표시될 이름을 설정해준다.

난 각각 <dir 이름>과 <파이썬버전(dir 이름)>으로 설정했다.

```shell
ipython kernel install --user --name python_ml --display-name "Python3(python_ml)"
```

정상적으로 등록됐다면 jupyter 환경으로 접속하면 된다.

```shell
$ jupyter lab
$ jupyter notebook
```

주피터 랩을 추천한다.


## 외부링크
 - [venv — 가상 환경 생성](https://docs.python.org/ko/3.8/library/venv.html)