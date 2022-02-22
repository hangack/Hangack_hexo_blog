---
title: 파이썬 라이브러리 math와 numpy
categories:
  - 연습
  - 파이썬
  - 모듈
tags:
  - 파이썬
  - numpy
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
sidebar:
  left:
    sticky: true
toc: true
thumbnail: /thumbnails/CS/numpy.svg
date: 2021-11-02 15:55:07
---
  

[파이썬 모듈 기초](https://hangack.github.io/2021/11/02/Codding/Python/basic/python14-%EB%AA%A8%EB%93%88/)
## 내장 라이브러리 Math
파이썬에는 기본적으로 수학 관련 작업을 위해 자주 사용되는 Math 내장 라이브러리가 존재한다.


```python
import math    # math 라이브러리를 불러오는 명령어.
            ''' 라이브러리 명령어는 [라이브러리명(혹은 as로 지정한 임의의 명칭)].[명령어]로 사용할 수 있으며.
                명령어 자동완성(혹은 명령어 목록)은 tap 키로 사용 및 확인 가능하다.
            '''
```

math 라이브러리는 수학 연산을 도와주는 라이브러리로 삼각함수부터 1~N까지 값을 곱해주는 factorial 함수 등 다양한 작업이 가능한 기본 함수들을 제공한다.


```python
print(math.cos( (300 / 180) * math.pi ))
print(math.factorial(4))
```

    0.5000000000000001
    24
    

파이썬에서 기본적으로 제공하는 List 형식의 행은 사용할 수 있으나 Math 라이브러리가 추가해주는 method 및 상수는 기본적인 식과 pi 등의 상수 뿐으로 다차원 연산으로 인해 행렬이 필요한 vector나 선형대수 등의 작업 형식에 대해선 복잡해지는 불편함이 있다.

## 외부 라이브러리 Numpy
위 문제를 해결해주는 라이브러리가 C언어 기반으로 만들어진 Numpy 외부 라이브러리로 작업 공간에서 행렬 형식의 변수를 사용할 수 있게 도와준다.

[numpy 명령어 튜토리얼](https://numpy.org/doc/stable/user/quickstart.html)


```python
import numpy as np
print(np.__version__)
```

    1.20.1
    
