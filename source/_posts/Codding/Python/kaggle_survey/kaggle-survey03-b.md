---
title: "Kaggle-Survey03-B: replace가 작동 안함 [pandas]"
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
thumbnail: /thumbnails/CS/pandas.svg
date: 2021-12-06 11:17:40
---

# Japan & China: IDE's

[Program_Language 과정](https://hangack.github.io/2021/12/05/Codding/Python/kaggle_survey/kaggle-survey03/)과 동일

Treemap을 뽑으려니 "Jupyter (JupyterLab, Jupyter Notebooks, etc)"와 "Visual Studio / Visual Studio Code"가 너무 길어 플롯에서 식별하기 난감하다.

각각 "Jupyter"와 "VS / VSCode"로 간략화 하려한다.

## 1차 시도

```python
df_IDEs_JnC_21n19.replace(to_replace = 'Jupyter (JupyterLab, Jupyter Notebooks, etc)', value =  'Jupyter', inplace = True)
df_IDEs_JnC_21n19.replace(to_replace = 'Visual Studio / Visual Studio Code', value =  'VS / VSCode', inplace = True)
```

둘 다 변경되지 않았다.

## 2차 시도

실제 string을 확인해보자.

```python
print(df_IDEs_JnC_21n19.loc[0].tolist())
print(df_IDEs_JnC_21n19.iloc[29].tolist())
```
    ['2021', 'Japan', 'Jupyter (JupyterLab, Jupyter Notebooks, etc) ', 200]
    ['2019', 'China', ' Visual Studio / Visual Studio Code ', 200]

뒤(혹은 앞뒤)로 공백이 들어간 상황임을 알 수 있다.


```python
df_IDEs_JnC_21n19.replace(to_replace = 'Jupyter (JupyterLab, Jupyter Notebooks, etc) ', value =  'Jupyter', inplace = True)
df_IDEs_JnC_21n19.replace(to_replace = ' Visual Studio / Visual Studio Code ', value =  'VS / VSCode', inplace = True)
```

성공적으로 변경됐다.

### 더 간편하게

근대 이럴거면 그냥 요소를 뽑아내서 직접 삽입하는게 편할 듯하다.

```python
df_IDEs_JnC_21n19.replace(to_replace = df_IDEs_JnC_21n19.loc[0,"IDE\'s"], value =  'Jupyter', inplace = True)
df_IDEs_JnC_21n19.replace(to_replace = df_IDEs_JnC_21n19.loc[29,"IDE\'s"], value =  'VS / VSCode', inplace = True)
```

인덱스와 칼럼명을 직접 지정해 뽑아낸 string과 동일한 요소를 모두 변경한다.


## 정규식?

' Visual Studio / Visual Studio Code ' 요소는 실제로는 아니지만 정규 표현식으로 해석할 여지가 있다.
정 방법을 못찾겠다면 `regex` 요소를 `True`로 지정해보는것도 방법이 될 수 있다.

```python
df_IDEs_JnC_21n19.replace(to_replace = 'Jupyter (JupyterLab, Jupyter Notebooks, etc) ', value = 'Jupyter', inplace = True)
df_IDEs_JnC_21n19.replace(to_replace = 'Visual Studio / Visual Studio Code', value = 'VS / VSCode', inplace = True, regex = True)
```

# IDE's Treemap

![IDE's](\images\2112\kaggle-survey03\IDEs.png)


# 외부링크
- [pandas.DataFrame.replace](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.replace.html)