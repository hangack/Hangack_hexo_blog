---
title: Kaggle_Survey03-A - value_counts error size 0 [pandas]
categories:
  - 연습
  - 파이썬
  - Kaggle_Survey 2021
tags:
  - 파이썬
  - code
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
date: 2021-12-06 01:11:21
---


[Kaggle_Survey03 - Treemap 시각화 [plotly]](https://hangack.github.io/2021/12/05/Codding/Python/kaggle_survey/kaggle-survey03/)에서 넘어왔다.

## 오류 식별

```python
df21_Ch = df21_ChJp[df21_ChJp.Q3.isin(["China"])]
df21_Jp = df21_ChJp[df21_ChJp.Q3.isin(["Japan"])]


## Q7(Program_Language): 칼럼번호 8~20 - others
df21_Jp_PL = pd.DataFrame()
df21_Jp_PL['Program_Language'] = [df21_Jp[col][1:].value_counts().index[0] for col in df21_Jp.columns[7:20]]
df21_Jp_PL['counts'] = [df21_Jp[col][1:].value_counts().values[0] for col in df21_Jp.columns[7:20]]


## Q7(Program_Language): 칼럼번호 8~20 - others
df21_Ch_PL = pd.DataFrame()
df21_Ch_PL['Program_Language'] = [df21_Ch[col][1:].value_counts() .index[0] for col in df21_Ch.columns[7:20]]
df21_Ch_PL['counts'] = [df21_Ch[col][1:].value_counts() .values[0] for col in df21_Ch.columns[7:20]]



## 제거된 나라 칼럼과 value를 각각 삽입 및 통합
df21_Jp_PL.insert(0, 'Country',  'Japan')
df21_Ch_PL.insert(0, 'Country',  'China')

df21_PL_JnC = pd.concat([df21_Jp_PL,df21_Ch_PL], ignore_index=True)
```


    ---------------------------------------------------------------------------

    IndexError                                Traceback (most recent call last)

    <ipython-input-5-89d86f0a4d0b> in <module>
         11 ## Q7(Program_Language): 칼럼번호 8~20 - others
         12 df21_Ch_PL = pd.DataFrame()
    ---> 13 df21_Ch_PL['Program_Language'] = [df21_Ch[col][1:].value_counts() .index[0] for col in df21_Ch.columns[7:20]]
         14 df21_Ch_PL['counts'] = [df21_Ch[col][1:].value_counts() .values[0] for col in df21_Ch.columns[7:20]]
         15 
    

    <ipython-input-5-89d86f0a4d0b> in <listcomp>(.0)
         11 ## Q7(Program_Language): 칼럼번호 8~20 - others
         12 df21_Ch_PL = pd.DataFrame()
    ---> 13 df21_Ch_PL['Program_Language'] = [df21_Ch[col][1:].value_counts() .index[0] for col in df21_Ch.columns[7:20]]
         14 df21_Ch_PL['counts'] = [df21_Ch[col][1:].value_counts() .values[0] for col in df21_Ch.columns[7:20]]
         15 
    

    E:\Sadness\anaconda3\lib\site-packages\pandas\core\indexes\base.py in __getitem__(self, key)
       4295         if is_scalar(key):
       4296             key = com.cast_scalar_indexer(key, warn_float=True)
    -> 4297             return getitem(key)
       4298 
       4299         if isinstance(key, slice):
    

    IndexError: index 0 is out of bounds for axis 0 with size 0


### 결측 column 식별 및 제거

***IndexError**: index 0 is out of bounds for axis 0 with size 0
오류가 식별됐다.
아마 China, Program_Language의 특정 응답이 없어서 발생한거같다.

N/A 개수를 식별해보자


```python
print("df21_Ch\'s rows_num:",len(df21_Ch))
print(df21_Ch.isnull().sum().iloc[7:20])
```

    df21_Ch's rows_num: 814
    Q7_Part_1      76
    Q7_Part_2     729
    Q7_Part_3     599
    Q7_Part_4     588
    Q7_Part_5     546
    Q7_Part_6     602
    Q7_Part_7     728
    Q7_Part_8     810
    Q7_Part_9     809
    Q7_Part_10    783
    Q7_Part_11    645
    Q7_Part_12    814
    Q7_OTHER      787
    dtype: int64
    

Q7_Part_12 이 녀석이 문제였다.
 - 행 개수는 814개고 Part_12의 N/A 개수도 814개이다.

위 식별 과정의 시행 횟수가 많아진다면 if 문을 사용한 define을 사용해도 되겠지만 일단은 수동으로 제거하자.


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