---
title: 문자열에서 특정 값을 뽑아내고 input을 받는 함수
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
thumbnail: /thumbnails/CS/python.svg
date: 2021-11-11 07:27:24
---

## Kaggle Survey Data Transformation
[2021 Kaggle Machine Learning & Data Science Survey](https://www.kaggle.com/c/kaggle-survey-2021) 에서 질문지를 나누는 작업 중 여러 part로 다수의 칼럼명을 가진 question number 부분의 [칼럼명을 뽑아내는 함수][Data Transformation]를 찾았고, 이 함수에 대응할 수 있으며 질문의 A,B type을 특정해낼 수 있는 input 함수를 짜봤다.

### 데이터 칼럼명 나누기


```python
import numpy as np
import pandas as pd

from warnings import filterwarnings
filterwarnings('ignore')
```

우선 모든 Question 칼럼명을 추출해낸다.
물론 데이터를 나누는 작업 전에 나눌 데이터와 데이터 명을 학습해야한다.
`kaggle_survey_2021_responses.csv`의 칼럼명 형식은 다음과 같다.
 - `'Q'(num1)`
 - `'Q'(num1)'_Part_'(num2)`
 - `'Q'(num1)'_'(type)'_Part_'(num2)`
 
각각을 Question, sub_Qustion, type_Qustion(sub 포함)으로 볼 수 있다.


```python
#df = pd.read_csv("D:/_Bdata/Codding-base-Python/Python/Python-jupyter/Kaggle Survey - 2021 Analysis - Plotly/kaggle_survey_2021_responses.csv")
df = pd.read_csv("E:/Fear/Univ/Big_data/Training/Github/Codding-base-Python/Python/Python-jupyter/Kaggle Survey - 2021 Analysis - Plotly/kaggle_survey_2021_responses.csv")
df_col_name = df.columns[1:]
df_col_name
```




    Index(['Q1', 'Q2', 'Q3', 'Q4', 'Q5', 'Q6', 'Q7_Part_1', 'Q7_Part_2',
           'Q7_Part_3', 'Q7_Part_4',
           ...
           'Q38_B_Part_3', 'Q38_B_Part_4', 'Q38_B_Part_5', 'Q38_B_Part_6',
           'Q38_B_Part_7', 'Q38_B_Part_8', 'Q38_B_Part_9', 'Q38_B_Part_10',
           'Q38_B_Part_11', 'Q38_B_OTHER'],
          dtype='object', length=368)



### 문자열을 인식해서 input 값을 특정해주는 함수 만들기

questions_count에 대응할 수 있는 input 함수를 짜낸다.


```python
def input_num():
    print("input Question no.: ")
    Qnum = input()
    Qnum_subQ = [s for s in df_col_name if "Q"+Qnum+"_" in s]
    
    if Qnum_subQ == []:
        return "Q"+Qnum+" has not part_Q"
    
    Question_type = None
    if [s for s in Qnum_subQ if ("A"or"B") in s]:
        print("input Q"+Qnum+"'s type")
        Question_type = input().upper()
        
    if Qnum_subQ:
        print("input Q"+Qnum+"'s last part no.: ")
        part_num = input()
    
    
    return questions_count(Qnum,part_num,Question_type)
```

위 함수는
Question number(`Qnum`)을 입력받은 뒤 이전에 정의한 칼럼명을 추출해 낸 `df_col_name` 객체내에서 `"Q"+Qnum+"_"` 문자열이 있는 sub_Question 형식을 찾아낸다.

[Data Transformation][Data Transformation]에서 얻어낸 코드는 `Qnum` 만 있는 경우에 대한 작업이 없으므로 이 경우는 line6 조건문에서 함수를 종료한다.

line 9의 if문에선 `'A' or 'B'` 문자가 들어있는 문자열을 list에서 식별해 해당하는 경우엔 Question_type 객체에 type을 입력 받게 되는 조건문을 작성했다.
이 때, `upper()` 함수를 이용해 소문자로 입력받아도 대문자로 자동변환되게 설정했다.

line 14의 조건문은 sub Question의 마지막 열을 입력받는 조건문으로 사용자가 'kaggle_survey'에서 직접 확인해서 input 값을 정해야한다.

### 칼럼명 리스트로 뽑아내기

[Data Transformation][Data Transformation]에서 가져온 코드로, 원하는 sub_Question들을 뽑아낼 수 있는 함수다.


```python
def questions_count(question_num, part_num, Question_type = False):
    part_questions = []
    
    if Question_type  in ["A","B"]:
        part_questions = ['Q'+question_num+"_"+Question_type+"_Part_"+str(j) for j in range(1,int(part_num))]
        part_questions.append("Q"+question_num+"_"+Question_type+"_OTHER")
    else:
        part_questions = ['Q'+question_num+'_Part_'+str(j) for j in range(1,int(part_num))]
        part_questions.append('Q'+question_num+'_OTHER')
        
    categories = []
    counts = []
    for i in part_questions:
        category = df[i].value_counts().index[0]
        val = df[i].value_counts()[0]
        categories.append(category)
        counts.append(val)
        
    combined_df = pd.DataFrame()
    combined_df['Category'] = categories
    combined_df['Count'] = counts
    
    combined_df = combined_df.sort_values(['Count'], ascending = False)
    return combined_df
```

`part_question` List를 만들어서 칼럼명을 저장하는데, `Question_type`이 입력되었을 경우와 아닌경우로 조건문이 나뉜다.
 - type이 있는 경우: `"Q(num)_(type)_Part_(part_num)"`
 - type이 없는 경우: `"Q(num)_Part_(part_num)"`

csv 파일을 보면 알 수 있지만, sub_qustion의 마지막 칼럼은 `Q(num)_OTHER`로 구성된다.
위 예외에 대응하기 위해 append함수를 이용해서 list에 `Q(num)_OTHER` 값을 추가한다.

남은 작업은 기존 df에서 칼럼명과 칼럼에 응답한 합을 구하기 위해` value_counts`함수의 `index`와 `values`를 사용해서 만든 dataframe을 반환하면 Data Transformation 작업이 끝난다.


```python
input_num()
```

    input Question no.: 
    1
    




    'Q1 has not part_Q'




```python
input_num()
```

    input Question no.: 
    7
    input Q7's last part no.: 
    12
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Python</td>
      <td>21860</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SQL</td>
      <td>10756</td>
    </tr>
    <tr>
      <th>4</th>
      <td>C++</td>
      <td>5535</td>
    </tr>
    <tr>
      <th>1</th>
      <td>R</td>
      <td>5334</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Java</td>
      <td>4769</td>
    </tr>
    <tr>
      <th>3</th>
      <td>C</td>
      <td>4709</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Javascript</td>
      <td>4332</td>
    </tr>
    <tr>
      <th>10</th>
      <td>MATLAB</td>
      <td>2935</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Other</td>
      <td>2575</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Bash</td>
      <td>2216</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Julia</td>
      <td>305</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Swift</td>
      <td>242</td>
    </tr>
  </tbody>
</table>
</div>




```python
input_num()
```

    input Question no.: 
    27
    input Q27's type
    a
    input Q27's last part no.: 
    11
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Category</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Amazon Web Services (AWS)</td>
      <td>3721</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Google Cloud Platform (GCP)</td>
      <td>3142</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Microsoft Azure</td>
      <td>2450</td>
    </tr>
    <tr>
      <th>3</th>
      <td>IBM Cloud / Red Hat</td>
      <td>572</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Oracle Cloud</td>
      <td>454</td>
    </tr>
    <tr>
      <th>7</th>
      <td>VMware Cloud</td>
      <td>390</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Other</td>
      <td>337</td>
    </tr>
    <tr>
      <th>5</th>
      <td>SAP Cloud</td>
      <td>290</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Salesforce Cloud</td>
      <td>275</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Alibaba Cloud</td>
      <td>259</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Tencent Cloud</td>
      <td>172</td>
    </tr>
  </tbody>
</table>
</div>



## 외부 링크
 - [Data Transformation][Data Transformation]
[Data Transformation]: https://www.kaggle.com/j2hoon85/for-newbie-let-s-do-data-transformation
 - [리스트에서 특정 문자열을 포함한 원소 뽑아내기][list 특정 문자열]
 [list 특정 문자열]: https://lapina.tistory.com/108

## 기억이 안날 때는 응애..
 - [python 함수](https://hangack.github.io/2021/11/02/Codding/Python/basic/python11-define/)
 - [python 입출력](https://hangack.github.io/2021/11/02/Codding/Python/basic/python12-%EC%9E%85%EC%B6%9C%EB%A0%A5/)
 - [python if문](https://hangack.github.io/2021/11/01/Codding/Python/basic/python7-%EC%A0%9C%EC%96%B4%EB%AC%B8/)
 - [python 비교연산자](https://hangack.github.io/2021/11/01/Codding/Python/basic/python8-%EB%B9%84%EA%B5%90%EC%97%B0%EC%82%B0%EC%9E%90/)
 - [python for문](https://hangack.github.io/2021/11/01/Codding/Python/basic/python9-for%EB%AC%B8/)
 - [python list_명령어](https://hangack.github.io/2021/11/01/Codding/Python/basic/python2-list/)
