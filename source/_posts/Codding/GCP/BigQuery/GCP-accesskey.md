---
title: GCP 엑세스키 발급받기
categories:
  - 연습
  - Google Cloud
  - bigquery
tags:
  - GCP
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
thumbnail: /thumbnails/CS/gcp.svg
date: 2022-01-27 16:38:47
---

# Google Cloud Platform

Python 코드에서 Bigquery로 data를 보내기 위해 [GCP](https://cloud.google.com/?authuser=1) 엑세스 키가 필요해졌다.

google cloud 콘솔에 접속하자.


## Service Account 생성

콘솔에서 엑세스 키를 발급받을 프로젝트를 선택하자.

 - 다음으로 [탐색 메뉴] - [IAM 및 관리자] - [서비스 계정]에 접속한다.
 - [+ 서비스 계정 만들기]를 클릭해서 서비스 계정을 만들고 프로젝트 엑세스 권한을 설정하면된다.

![JAVA_HOME](/images/2202/pyspark-설치/JAVA_HOME.png)
![계정 생성](/images/2202/GCP-key/권한.png)


## Service Account Key 발급받기

 - 생성된 계정의 [작업] - [키 관리]로 이동한다.
 - [키 추가] - [새 키 만들기] - [JSON]으로 발급받아서 사용하면 된다.


## python GCP 연동하기
 - [pandas_gbq python과 google bigquery 연동하기](https://hangack.github.io/2022/02/16/Codding/Python/SQL/pandas_gbq-python-google-bigquery/)


# 외부링크
 - [Python BigQuery 연동하기](https://wooiljeong.github.io/python/python-bigquery/)