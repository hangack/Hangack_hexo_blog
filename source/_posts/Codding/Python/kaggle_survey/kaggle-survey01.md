---
title: "Kaggle_Survey01: Pie 시각화 [plotly]"
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
thumbnail: /thumbnails/CS/plotly.svg
toc: true
date: 2021-12-02 11:17:39
---

# dataset 구조 확인하기

```python
import pandas as pd
import plotly.graph_objects as go 

colors = ['#FF0000','#FFBB00','#ffff00','#00FF00','#0000FF','#9C009C']
```
```python
df = pd.read_csv("https://raw.githubusercontent.com/hangack/project-green/main/Kaggle_Survey-2021/data/kaggle-survey-2021/kaggle_survey_2021_responses.csv", dtype='unicode')
#df = pd.read_csv("../input/kaggle-survey-2021/kaggle_survey_2021_responses.csv")
```

Columns 구조는 [문자열에서 특정 값을 뽑아내고 input을 받는 함수](https://hangack.github.io/2021/11/11/Codding/Python/kaggle_survey/Data-Transformation-input-num/) 포스트에서 확인했으므로 넘어간다.


# 비교 대상 선정하기

2021 kaggle_survey 분석을 계속 진행한다.

베이스는 2021년 기준 survey 응답 count 수가 비슷한 일본과 중국을 선정했다.
한국 넣으려다 응답수가 낮아 방향을 바꿨다

`kaggle_survey_2021_responses`의 모든 row를 사용할 필요 없으므로 Q3(country) 응답에 Jp(Japan), Ch(China)인 요소만 추출한다.

```python
df_ChJp = df[df.Q3.isin(["Japan","China"])]

df_Ch = df_ChJp[df_ChJp.Q3.isin(["China"])]
df_Jp = df_ChJp[df_ChJp.Q3.isin(["Japan"])]
```


# Gender [plotly: Pie]

일단 간단히 비교할 수 있는 Gender(Q2)와 Age(Q1) 중 Q2를 Pie 그래프로 시각화할 예정이다.

간단한 Pie 그래프를 사용할 예정이고, 간단한 그래프인 만큼 pie 요소 option을 만질 여지가 많다.
따라서 `express`가 아닌 `graph_objects` 모듈로 작업했다.
- [plotly.graph_objects.Pie](https://plotly.com/python-api-reference/generated/plotly.graph_objects.Pie.html)
- [Pie Charts in Python](https://plotly.com/python/pie-charts/)

plotly.graph_objects.Pie를 사용해서 만든 그래프를 Figure 형식으로 지정하고 fig_j 객체에 저장한다.

아래 코드는 필수 요소인 `lables`와 `values`만 넣은 결과다.

```python
fig_j = go.Figure(data=[go.Pie(labels=df_Jp['Q2'][1:].value_counts().index, 
                               values=df_Jp['Q2'][1:].value_counts().values
                              )
                       ]
                 )

fig_j.show()
```
![Pie1](\images\2112\kaggle-survey01\pie1.png)


## 대응하는 value_counts 함수 만들기

앞으로 많은 그래프를 그려낼거고 `df_Jp['Q2'][1:].value_counts()` 형식이 반복된다.

`df_Jp['Q2'][1:].value_counts()`을 객체로 만들어서 넣어도 되겠지만, 이번 작업에서 사용할 df은 `df_Jp`&`df_Ch` 2개로 dataframe 객체의 변동이 있고, 칼럼명도 Q1,Q2로 변동이 있다.
위 조건에 부합하는 간단한 함수 하나 만들겠다.

```python
def indiQ_value_counts(dataframe, indi_Qnum):
    df = dataframe[indi_Qnum][1:].value_counts()
    return df
```
```python
df_Jp_gen = indiQ_value_counts(df_Jp, 'Q2')
df_Ch_gen = indiQ_value_counts(df_Ch, 'Q2')
```


## subplots: 그래프 figure 합치기

japan과 china 함수를 각각의 figure로 보기엔 불편하다.
subplost를 이용해 하나의 fig로 합칠 예정이다.
- [plotly.subplots.make_subplots](https://plotly.com/python-api-reference/generated/plotly.subplots.make_subplots.html)
- [Subplots Types](https://plotly.com/python/subplots/)

```python
from plotly.subplots import make_subplots
```
```python
Pie_J = go.Pie(labels=df_Jp_gen.index, 
               values=df_Jp_gen.values
              )

Pie_C = go.Pie(labels=df_Ch_gen.index, 
               values=df_Ch_gen.values
              )
```
```python
fig = make_subplots(rows=1, cols=2,specs=[[{"type": "domain"},{"type": "domain"}]])

fig.add_trace(Pie_J,row=1,col=1)
fig.add_trace(Pie_C,row=1,col=2)

fig.show()
```
![Pie1](\images\2112\kaggle-survey01\pie2.png)


## text, color 커스텀

커스텀 색상이나 타이틀 등 텍스트를 넣어 간단한 시각적 커스텀을 입혀보자

```python
Pie_J = go.Pie(labels=df_Jp_gen.index, 
               values=df_Jp_gen.values,
               title='Japan',
               textinfo ='label,percent'
              )

Pie_C = go.Pie(labels=df_Ch_gen.index, 
               values=df_Ch_gen.values,
               title='China',
               textinfo ='label,percent'
              )
```
```python
fig = make_subplots(rows=1, cols=2,specs=[[{"type": "domain"},{"type": "domain"}]])

fig.add_trace(Pie_J,row=1,col=1)
fig.add_trace(Pie_C,row=1,col=2)

fig.update_layout(title_text='Gender')
fig.update_traces(marker=dict(colors=colors[1:]))

fig.show()
```
![Pie1](\images\2112\kaggle-survey01\pie3.png)


## 시각 요소 커스텀

Trace의 title이 Pie 외부에 위치하는게 맘에들지 않는 부분을 수정하기 위해 시각 효과에서 legend를 제거하는 등 각종 요소 값을 변경한다.

```python
Pie_J = go.Pie(labels=df_Jp_gen.index, 
               values=df_Jp_gen.values,
#               pull=[0,0,0.2,0.2,0.2],    ## 중앙에서 n% 떨어진 위치 할당
               title='Japan',
               textinfo ='label,percent',
               hole=0.3
              )

Pie_C = go.Pie(labels=df_Ch_gen.index, 
               values=df_Ch_gen.values,
#               pull=[0,0,0.2,0.2,0.2],
               title='China',
               textinfo ='label,percent',
               hole=0.3
              )
```
```python
fig = make_subplots(rows=1, cols=2,specs=[[{"type": "domain"},{"type": "domain"}]])

fig.add_trace(Pie_J,row=1,col=1)
fig.add_trace(Pie_C,row=1,col=2)

fig.update_layout(title_text='Gender',
#                  showlegend=False,    ## ledend(lable 목록) 시각적으로 제거
                  margin=dict(t=0, b=0, l=0, r=0)
                 )
fig.update_traces(marker=dict(colors=colors[1:]))


fig.show()
```
<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plotly.com/~hangack/1.embed" height="525" width="100%"></iframe>


# 외부링크
- [plotly.graph_objects.Pie](https://plotly.com/python-api-reference/generated/plotly.graph_objects.Pie.html)
- [Pie Charts in Python](https://plotly.com/python/pie-charts/)
- [plotly.subplots.make_subplots](https://plotly.com/python-api-reference/generated/plotly.subplots.make_subplots.html)
- [Subplots Types](https://plotly.com/python/subplots/)