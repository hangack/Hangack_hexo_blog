---
title: 'Kaggle_Survey00 - dtype Warning 해결하기 [pandas]'
categories:
  - 연습
  - 파이썬
  - Kaggle_Survey 2021
tags:
  - 파이썬
  - code
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
thumbnail: /thumbnails/CS/pandas.svg
date: 2021-11-18 12:17:46
---
  

```python
import pandas as pd
```

```python
#df = pd.read_csv("D:/_Bdata/Codding-base-Python/Python/Python-jupyter/Kaggle Survey - 2021 Analysis - Plotly/kaggle_survey_2021_responses.csv")

df = pd.read_csv("E:/Fear/Univ/Big_data/Training/Github/Codding-base-Python/Python/Python-jupyter/Kaggle Survey - 2021 Analysis - Plotly/kaggle_survey_2021_responses.csv")

#df = pd.read_csv("../input/kaggle-survey-2021/kaggle_survey_2021_responses.csv")
```

    E:\Sadness\anaconda3\lib\site-packages\IPython\core\interactiveshell.py:3165: DtypeWarning: Columns (0,195,201,285,286,287,288,289,290,291,292) have mixed types.Specify dtype option on import or set low_memory=False.
    has_raised = await self.run_ast_nodes(code_ast.body, cell_name,
    

cvs datasat을 불러오는데 위와 같이 `DtypeWarning` 이라는 경고가 출력되었다.

## DtypeWarning 해결하기

### filterwarnings
경고 그 자체가 원하는 작업은 아니지만 문제가 발생하지 않는 이상 user는 경고를 무시해도 상관없다.

권장하지 않지만 거슬린다면 `warnings` 모듈의 경고 필터 `ignore`를 사용해 경고 출력을 무시할 수 있다.


```python
from warnings import filterwarnings
filterwarnings('ignore')
```

### low_memory

하지만 근본적인 해결은 아니므로 terminal이 제안한 방식인 `low_memory=False` 를 넣어 해결할 수 있다.


```python
df = pd.read_csv("csv url", low_memory=False)
```

위 방식은 각 column마다 data type을 추측하는 방식으로 옵션명(낮은 메모리)처럼 작업량이 data 크기에 비례해 증가한다.

방대한 데이터를 처리해야되서 Dtype 추측 방식이 부담된다면?

### dtype 형식 지정

불러올 file의 문자 형식을 알고 있다면 `dtype`을 지정해 warning을 해결하고 memory 가용량도 줄일 수 있다.


```python
df = pd.read_csv("csv url", dtype='unicode')
```

## 외부링크
 - [warnings — 경고 제어](https://docs.python.org/ko/3/library/warnings.html)
 - [DataFrame의 칼럼](https://wikidocs.net/46751)