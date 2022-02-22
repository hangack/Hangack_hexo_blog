---
title: plotly 동적 그래프 웹페이지에 삽입하기
categories:
  - 블로그
tags: 
  - 블로그
  - python
  - plotly
  - html
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
date: 2021-11-30 06:20:51
---
  

# plotly에 그래프 업로드

[Kaggle_Survey01: Pie [Plotly]](https://hangack.github.io/2021/12/02/Codding/Python/kaggle_survey/kaggle-survey01/)에서 작성한 plotly chart는 동적 그래프라 이미지로 사용하긴 아쉽고 github page의 ipynb에서도 동작하지 않는다.

그래프를 끌어오기 위해 plotly 홈페이지 저장환경을 이용할 예정이다.


## chart_studio 설치

우선 사용할 작업환경에 [chart_studio](https://plotly.com/python/getting-started-with-chart-studio/) 라이브러리를 설치해주자.

```shell
$ pip i chart_studio
```

※ jupyter 로컬 작업환경을 사용한다면 anaconda prompt로 설치


`chart_studio`는 plotly 그래프를 plotly 홈페이지에 업로드하고 원한다면 html iframe 태그로 변환까지 해주는 녀석이다.

## plotly Access Key

[plotly](https://chart-studio.plotly.com/feed/#/) 개인 공간에 업로드 할 예정이니 plotly 회원가입을 진행하자.

[profile] - [API keys] 에서 Access key를 얻어온다.

![API key](\images\2111\plotly-iframe\access key.png)


위에서 설치한 라이브러리를 import하고 API key를 사용해 계정에 접근하자

```python
import chart_studio
chart_studio.tools.set_credentials_file(username='유저명', api_key='접근키')
```


성공적으로 연동했다면 저장할 figure 객체와 저장될 파일명을 넣어준다.

```python
chart_studio.plotly.plot(fig, filename = '파일명', auto_open=True)
```
    'https://plotly.com/~hangack/1/'

out된 url에 들어가보면 그래프가 업로드 되었을거다.


# 웹페이지에 그래프 끌어오기

원래 목적이었던 웹페이지에서 그래프를 사용해보자.


## html iframe

iframe(inline frame) html 형식을 수작업으로 작성해도 되겠지만 `chart_studio` 모듈 내 라이브러리에서도 변환할 수 있다.

```python
chart_studio.tools.get_embed('https://plotly.com/~hangack/1/#/')
```
    '<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plotly.com/~hangack/1.embed" height="525" width="100%"></iframe>'


```html
<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plotly.com/~hangack/1.embed" height="525" width="100%"></iframe>
```

iframe(inline frame): 

<iframe id="igraph" scrolling="no" style="border:none;" seamless="seamless" src="https://plotly.com/~hangack/1.embed" height="525" width="100%"></iframe>


## hexo tag plugin iframe

hexo 환경에서 작성중이라면 기본 plugin인 [tag](https://hexo.io/ko/docs/tag-plugins.html) 문법으로도 iframe을 삽입할 수 있다.

```
{% iframe https://plotly.com/~hangack/1.embed %}
```

{% iframe https://plotly.com/~hangack/1.embed %}



# 외부링크
- [Plotly 그래프 깃헙 블로그에 올리기](https://dschloe.github.io/python/python_edu/03_datavisualisation/ch_plotly_html/)