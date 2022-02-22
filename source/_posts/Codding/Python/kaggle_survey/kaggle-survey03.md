---
title: "Kaggle_Survey03: Treemap 시각화 [plotly]"
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
date: 2021-12-05 22:55:24
---

# 기본 설정

## module

treemap으로 많은 요소를 건드리진 않을 예정이니 express 라이브러리를 사용

```python
import pandas as pd
import plotly.express as px
```

## Import data

2021년 자료 외에도 19년 자료를 추가

```python
df21 = pd.read_csv("https://raw.githubusercontent.com/hangack/project-green/main/Kaggle_Survey-2021/data/kaggle-survey-2021/kaggle_survey_2021_responses.csv", dtype='unicode')
df19 = pd.read_csv("https://raw.githubusercontent.com/hangack/project-green/main/Kaggle_Survey-2021/data/kaggle-survey-2019/multiple_choice_responses.csv", dtype='unicode')
#df21 = pd.read_csv("../input/kaggle-survey-2021/kaggle_survey_2021_responses.csv", dtype='unicode')
#df19 = pd.read_csv("../input/kaggle-survey-2019/multiple_choice_responses.csv", dtype='unicode')
```

# Japan & China: Programming_Languages

## 2021 Japan & China total

2021년 Q3(Country) 일본 중국 추출 dataframe

```python
df21_ChJp = df21[df21.Q3.isin(["Japan","China"])]
```

## Split Country

나라별 value_counts를 위해 각 나라로 dataframe 분리

### 2021

[value_counts 오류 식별](https://hangack.github.io/2021/12/06/Codding/Python/kaggle_survey/kaggle-survey03-a/) 결측값 제거

```python
df21_Ch = df21_ChJp[df21_ChJp.Q3.isin(["China"])]
df21_Jp = df21_ChJp[df21_ChJp.Q3.isin(["Japan"])]


## Q7(Program_Language): 칼럼번호 8~20 - others
df21_Jp_PL = pd.DataFrame()
df21_Jp_PL['Program_Language'] = [df21_Jp[col][1:].value_counts().index[0] for col in df21_Jp.columns[7:19]]
df21_Jp_PL['counts'] = [df21_Jp[col][1:].value_counts().values[0] for col in df21_Jp.columns[7:19]]


## 2021 China: Q7_Part12(None) value == 0이므로 결측값 제거
df21_Ch_rmQ07P12 = df21_Ch.drop(['Q7_Part_12'], axis='columns')

## Q7(Program_Language): 칼럼번호 8~20 - others - Q7_Part12(None)
df21_Ch_PL = pd.DataFrame()
df21_Ch_PL['Program_Language'] = [df21_Ch_rmQ07P12[col][1:].value_counts() .index[0] for col in df21_Ch_rmQ07P12.columns[7:18]]
df21_Ch_PL['counts'] = [df21_Ch_rmQ07P12[col][1:].value_counts() .values[0] for col in df21_Ch_rmQ07P12.columns[7:18]]


## 제거된 나라 칼럼과 value를 각각 삽입 및 통합
df21_Jp_PL.insert(0, 'Country',  'Japan')
df21_Ch_PL.insert(0, 'Country',  'China')

df21_PL_JnC = pd.concat([df21_Jp_PL,df21_Ch_PL], ignore_index=True)
```

## 2019 Japan & China total

2019년 Q3(Country) 일본 중국 추출 dataframe

```python
df19_ChJp = df19[df19.Q3.isin(["Japan","China"])]
```

### 2019

2021년과 동일 과정

```python
df19_Ch = df19_ChJp[df19_ChJp.Q3.isin(["China"])]
df19_Jp = df19_ChJp[df19_ChJp.Q3.isin(["Japan"])]


## Q18(Program_Language): 칼럼번호 83~95 - others & other(text)
df19_Jp_PL = pd.DataFrame()
df19_Jp_PL['Program_Language'] = [df19_Jp[col][1:].value_counts().index[0] for col in df19_Jp.columns[82:93]]
df19_Jp_PL['counts'] = [df19_Jp[col][1:].value_counts().values[0] for col in df19_Jp.columns[82:93]]


## 2019 China Q18_Part11(None) 결측값 제거
df19_Ch_rmQ18P11 = df19_Ch.drop(['Q18_Part_11'], axis='columns')

## Q18(Program_Language): 칼럼번호 83~95 - others & other(text) - Q18_Part11(None)
df19_Ch_PL = pd.DataFrame()
df19_Ch_PL['Program_Language'] = [df19_Ch_rmQ18P11[col][1:].value_counts() .index[0] for col in df19_Ch_rmQ18P11.columns[82:92]]
df19_Ch_PL['counts'] = [df19_Ch_rmQ18P11[col][1:].value_counts() .values[0] for col in df19_Ch_rmQ18P11.columns[82:92]]



df19_Jp_PL.insert(0, 'Country',  'Japan')
df19_Ch_PL.insert(0, 'Country',  'China')

df19_PL_JnC = pd.concat([df19_Jp_PL,df19_Ch_PL], ignore_index=True)
```

## Split year{Country}

다른 csv인 2019자료와 2021자료 통합


```python
df21_PL_JnC.insert(0, 'year',  '2021')
df19_PL_JnC.insert(0, 'year',  '2019')

df_PL_JnC_21n19 = pd.concat([df21_PL_JnC,df19_PL_JnC], ignore_index=True)
```

Program_Language의 19년도 21년도 통합 value_counts의 정렬(연도 - 언어 - 나라)

values는 Program_Language의 value_counts

## Programming_Languages [treemap]

이전 언급처럼 treemap으로 많은 요소를 건드리진 않을 예정이니 express 라이브러리를 사용했다.

path 요소의 순서는 부모자식 순서로 dataframe 칼럼 순서에 제한되지 않는다. -> path 요소 조정으로 순서를 맘대로 바꿀 수 있다.

color 기준: country

```python
fig = px.treemap(df_PL_JnC_21n19, path=[px.Constant("2019n2021"),'year','Program_Language','Country'],
                values='counts', color='Country',
                  color_discrete_map={'(?)':'lightgrey', 'China':'gold', 'Japan':'darkblue'})

fig.data[0].textinfo = 'label+percent parent+value'

fig.update_layout(margin = dict(t=0, l=0, r=0, b=0))

fig.show()
```

<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plotly.com/~hangack/12.embed" height="525" width="100%"></iframe>


color 참조 값을 counts로 넣었을 때는 plotly.express 설정대로 colorbar가 나온다.

color 기준: counts

```python
colors = ['#D2691E','#E19B50','#E6C17B','#F0CB85','#F5D08A','#FFEFD5']
```
```python
fig = px.treemap(df_PL_JnC_21n19, path=[px.Constant("2019n2021"),'year','Program_Language','Country'],
                values='counts', color='counts', color_continuous_scale=colors)

fig.data[0].textinfo = 'label+percent parent+value'

fig.update_layout(margin = dict(t=0, l=0, r=0, b=0))

fig.show()
```

<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plotly.com/~hangack/14.embed" height="525" width="100%"></iframe>
