---
title: Kaggle_Survey02 - Bar 시각화 [plotly]
categories:
  - 연습
  - 파이썬
  - Kaggle_Survey 2021
tags:
  - 파이썬
  - code
  - plotly
  - pandas
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
thumbnail: /thumbnails/CS/plotly.svg
date: 2021-12-03 00:19:33
---
  

## 이전 포스팅들과 동일 과정

```python
import pandas as pd
import plotly.graph_objects as go 

colors = ['#FF0000','#FFBB00','#ffff00','#00FF00','#0000FF','#9C009C']
```
```python
df = pd.read_csv("https://raw.githubusercontent.com/hangack/project-green/main/Kaggle_Survey-2021/data/kaggle-survey-2021/kaggle_survey_2021_responses.csv", dtype='unicode')
#df = pd.read_csv("../input/kaggle-survey-2021/kaggle_survey_2021_responses.csv")
```
```python
df_ChJp = df[df.Q3.isin(["Japan","China"])]

df_Ch = df_ChJp[df_ChJp.Q3.isin(["China"])]
df_Jp = df_ChJp[df_ChJp.Q3.isin(["Japan"])]
```
```python
def indiQ_value_counts(dataframe, indi_Qnum):
    df = dataframe[indi_Qnum][1:].value_counts()
    return df
```
```python
df_Jp_age = indiQ_value_counts(df_Jp, 'Q1')
df_Ch_age = indiQ_value_counts(df_Ch, 'Q1')
```


## Age [plotly: Bar]

01에 이어 이번에도 두 나라의 값을 비교할 예정이니 아예 처음부터 데이터를 합쳐서 표현한 그래프를 뽑아내겠다.
- [plotly.graph_objects.Bar](https://plotly.com/python-api-reference/generated/plotly.graph_objects.Bar.html)
- [Bar Charts in Python](https://plotly.com/python/bar-charts/)

```python
Bar_C = go.Bar(name='China',
               x=df_Ch_age.index,
               y=df_Ch_age.values
              )
Bar_J = go.Bar(name='Japan',
               x=df_Jp_age.index,
               y=df_Jp_age.values
              )
```
```python
fig = go.Figure(data=[Bar_C,
                      Bar_J])

fig.update_layout(title='Age: Japan & China',
                  xaxis_title="Age", yaxis_title='Counts'
                 )

fig.show()
```
![Bar1](\images\2112\kaggle-survey02\bar1.png)

bar chart에서 stack 형식을 사용하거나 group과 stack을 동시에 사용하지 않는 이상 하나의 plot에 여러 bar data를 넣으면 default는 group 형식으로 뽑힌다.

### index 정렬

나이 순으로 출력하고 싶었지만, `value_counts` 할 때 원본 dataframe의 요소 순서로 index가 들어가버렸다.

그래서 `value_counts`된 dataframe을 `sort_index`를 사용해 오름차순 정렬한다.

```python
df_Ch_sortAge = df_Ch_age.sort_index()
df_Jp_sortAge = df_Jp_age.sort_index()
```

![Bar2](\images\2112\kaggle-survey02\bar2.png)

### 60-69 구간에 더미값 추가

정렬은 문제없어 보였지만 70+와 60-69 순서가 이상하다.

```python
df_Ch_sortAge
```
    18-21    206
    22-24    274
    25-29    159
    30-34    109
    35-39     39
    40-44     14
    45-49      8
    50-54      1
    55-59      2
    70+        1
    Name: Q1, dtype: int64

아무래도 China에 60-69 구간에 해당하는 value가 없어서 index 추가가 안된거같다.

index가 전부 있는 Japan을 앞 순서로 바꿔도 되겠지만, 그냥 China `60-69` index를 추가하고 임의로 값 `0`를 넣겠다.

```python
df_Ch_sortAge.loc['60-69'] = 0
df_Ch_sortAge = df_Ch_sortAge.sort_index()
```

![Bar3](\images\2112\kaggle-survey02\bar3.png)


## 외부링크
- [plotly.graph_objects.Bar](https://plotly.com/python-api-reference/generated/plotly.graph_objects.Bar.html)
- [Bar Charts in Python](https://plotly.com/python/bar-charts/)