---
title: pyspark 설치
categories:
  - 연습
  - 파이썬
  - pyspark
tags:
  - 파이썬
  - pyspark
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
thumbnail: /thumbnails/CS/spark.svg
date: 2022-02-14 09:11:31
---

# pyspark

대용량 data를 관리하기 위한 유사 SQL 라이브러리

## 사전 준비

- python 설치
- java 설치
- spark 다운로드
- winutils 다운로드

### python 설치

파이썬 혹은 아나콘다를 설치한다.
python 버전 3 이상으로 설치한다.

 - https://www.python.org/downloads/
 - [아나콘다 설치](https://hangack.github.io/2021/11/01/Codding/Python/basic/Python0_download/)


### java 설치

나의 경우 java가 설치되어있고 `JAVA_HOME` 환경변수까지 설정되있기에 그대로 사용했으나 아니라면 오라클에 로그인하고 java를 설치한다.

 - https://www.oracle.com/java/technologies/downloads/#jdk17-windows

이후 `JAVA_HOME` 환경 변수를 추가해준다.

![JAVA_HOME](/images/2202/pyspark-설치/JAVA_HOME.png)

시스템 변수, 사용자 변수 중 원하는 영역에 추가해준다.
난 여러 계정을 사용하지 않으니 그냥 사용자 변수에 넣어줬다.


### Spark 다운로드

Spark tgz 압축파일을 다운받는다.
- [spark](https://spark.apache.org/downloads.html)

![SPARK](/images/2202/pyspark-설치/Spark.png)

원하는 경로에 압축 풀고 위와 동일하게 환경 변수를 설정해준다.

![SPARK-경로](/images/2202/pyspark-설치/Spark-경로.png)
![SPARK_HOME](/images/2202/pyspark-설치/SPARK_HOME.png)


### winutils 다운로드

위에서 받은 spark 버전과 동일 버전의 `winutils.exe`를 받아준다.
 - [winutils](https://github.com/cdarlint/winutils)

winutils용 폴더를 만들고 bin 파일 아래에 넣어준다.

![winutils-경로](/images/2202/pyspark-설치/winutils-경로.png)

hadoop 환경변수도 설정한다.

![HADOOP_HOME](/images/2202/pyspark-설치/HADOOP_HOME.png)


### Path 설정

마지막으로 path 값에

 - %JAVA_HOME%\bin
 - %SPARK_HOME%\bin
 - %HADOOP_HOME%\bin
을 넣어준다.

![path](/images/2202/pyspark-설치/Path.png)


## pyspark 실행

CMD(혹은 Anaconda Prompt)를 열어서 pyspark 설치한다.
```shell
> pip install pyspark
```

```shell
> pyspark
```
![pyspark](/images/2202/pyspark-설치/pyspark.png)


# 외부링크
 - [PySpark란 무엇입니까?](https://databricks.com/kr/glossary/pyspark)
 - [Spark Installation on Windows 10](https://dschloe.github.io/python/python_edu/00_settings/spark_installation_windows_10/)
 - [WINDOWS에 PySpark 설치](https://ahnty0122.tistory.com/22)