---
title: ipynb 사용하기; Jupyter & Google Colab
categories:
  - 연습
  - 파이썬
  - 설정
tags:
  - 파이썬
  - 쥬피터
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
date: 2021-11-07 09:54:25
---
  
IPython Notebook은 python 코딩과 html을 지원하고 수식까지 표현 가능한 markdown 텍스트 박스를 동시에 사용해 가독성을 올리기 위해 제안된 방식이다.

## Jupyter
  

기본적으로 로컬환경에서 사용가능한 Jupyter 시리즈가 있다.
![아나콘다](/images/2111/ipynb/ipynb1.png)
주피터는 아나콘다를 설치하면 따라오는 소프트웨어로 [아나콘다 설치 방법](https://hangack.github.io/2021/11/01/Codding/Python/basic/Python0_download/) 포스트를 참조하자.

ipynb 단축키는 커멘트 팔렛트에서 확인 및 수정할 수 있다.
![](/images/2111/ipynb/ipynb2.png)
자주 사용되는 단축키는 
- ctrl+m & m
- d & d
- tab
등 다양하게 있으니 기호에 맞춰 설정하자.

## Google Colab

온라인 환경에선 다양한 플렛폼이 ipynb 환경을 지원하지만 접근성이 좋고 작업 리소스까지 지원해주며 저장공간 연동까지 가능한 [Google Colab](https://colab.research.google.com/)이 대표적이다.
Google 플렛폼이므로 당연히 [google drive](https://drive.google.com/) 연동을 지원하고, [Github](https://github.com/) 업로드도 가능하다.
![](/images/2111/ipynb/ipynb3.png)

유저 작업환경 사양이 좋지않다면 Colab에서 지원하는 하드웨어 가속기를 사용해서 저사양 GPU(혹은 TPU)를 대여할 수 있다.

![수정 - 노트 설정](/images/2111/ipynb/ipynb4.png)

추가로 ipynb는 '[Kaggle](https://www.kaggle.com/) Notebook' 등 다양한 플랫폼에서 작업 가능하다.