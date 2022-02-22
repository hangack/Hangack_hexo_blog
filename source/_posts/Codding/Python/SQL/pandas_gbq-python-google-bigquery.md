---
title: pandas_gbq python과 google bigquery 연동하기
categories:
  - 연습
  - 파이썬
  - SQL
tags:
  - 파이썬
  - GBQ
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
thumbnail: /thumbnails/CS/gbq.svg
date: 2022-02-16 18:49:23
---

[GCP 엑세스키 발급받기](https://hangack.github.io/2022/02/16/Codding/GCP/BigQuery/GCP-accesskey/)를 선행

# 라이브러리 설치

## google-cloud-bigquery

python과 google bigquery를 연동하기 위한 라이브러리

```shell
$ pip install google-cloud-bigquery
```

## pandas-gbq

dataframe을 gbq에 업로드하기 위한 라이브러리

```shell
$ pip install pandas-gbq
```

# GBQ 연동

```python
from google.oauth2 import service_account

## json 파일 내용
credentials = service_account.Credentials.from_service_account_info(
    {
        "type": "",
        "project_id": "",
        "private_key_id": "",
        "private_key": "",
        "client_email": "",
        "client_id": "",
        "auth_uri": "",
        "token_uri": "",
        "auth_provider_x509_cert_url": "",
        "client_x509_cert_url": ""
    }
)

## json 파일 경로를 사용하고 싶으면 `from_service_account_file` 함수를 사용하면된다
credentials = service_account.Credentials.from_service_account_file("URL.json")
```

업로드 하고싶은 dataframe(`df`)을 만들어두자.

`pandas.to_gbq`로 연동하면 브라우저 창을 통해 쿠키를 받아야하므로 `pandas_gbq`를 사용한다.

```python
import pandas_gbq

project_id = "project_id"
table_name = "data_set_name.table_name"

pandas_gbq.context.credentials = credentials
pandas_gbq.context.project = project_id
```



## dataframe 업로드

`if_exists` 요소의 기본값 = "fail"
 - fail: 테이블이 존재하면 `pandas_gbq.gbq.TableCreationError` 발생
 - replace: 테이블이 있는 경우 다시 만들고 데이터 삽입
 - append: 테이블에 데이터 삽입(테이블이 없는 경우 테이블 생성)

```python
pandas_gbq.to_gbq(df, table_name, project_id=project_id, if_exists="append")
```


## bigquery data 받아오기


```python
import pandas as pd

query = "SELECT * FROM `data_set_name.table_name`"
readdf = pd.read_gbq(query=query, project_id=project_id, credentials=credentials, dialect='standard')
```

# 외부링크
 - [API Reference: pandas_gbq](https://pandas-gbq.readthedocs.io/en/latest/api.html#pandas_gbq)
 - [pandas.to_gbq](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.to_gbq.html)
 - [pandas.read_gbq](https://pandas.pydata.org/docs/reference/api/pandas.read_gbq.html)