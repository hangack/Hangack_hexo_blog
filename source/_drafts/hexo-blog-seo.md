---
title: hexo blog 검색 엔진 최적화 및 사이트 등록하기
categories:
  - 블로그
  - 설정
tags: 
  - 블로그
  - 설정
  - hexo
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
thumbnail: /thumbnails/CS/hexo.svg
date: 2021-11-29 06:32:28
---


## 검색이 안되네?

세팅전을 참 오래 구웠지만 정작 중요한 블로그 URL을 검색 엔진에 등록조차 하지 않았다.

![검색이 안되네](\images\2111\hexo_blog_SEO\seo1.png)

내 블로그가 딥웹도 아니고 검색은 되야하지 않겠어?


## Hexo Plugin (SEO)

SEO: [검색엔진 최적화(search engine optimization)](https://ko.wikipedia.org/wiki/%EA%B2%80%EC%83%89_%EC%97%94%EC%A7%84_%EC%B5%9C%EC%A0%81%ED%99%94)

검색 엔진에 등록하기 전에 또 다시 세팅전 좀 구워야겠다.

검색 엔진 최적화를 위해 깔아야하는 플러그인은 총 5개
 - hexo-auto-canonical
 - hexo-autonofollow
 - hexo-generator-seo-friendly-sitemap
 - hexo-generator-feed
 - hexo-generator-robotstxt


### hexo-auto-canonical

canonical: 포스트마다 메타 태그를 생성시켜주는 플러그인으로 검색 엔진이 페이지 제목과 검색어를 잘 연결할 수 있도록 유도한다.

icarus의 경우엔 자동적으로 각 포스트마다 canonical 속성이 추가되있어서 나는 설치하지 않았다.

canonical 속성을 확인하려면 임의 포스트 페이지에 들어가서 DevTools를 열어 `canonical` 속성을 찾아보자.

![canonical](\images\2111\hexo_blog_SEO\canonical.png)

만약 설치가 필요하다면

```shell
$ npm i hexo-auto-canonical
```

설치를 해주고, `autoCanonical` 속성을 추가해야한다.

```ejs layout/common/head.ejs
<%- autoCanonical(config, page) %>
```


### hexo-autonofollow

nofollow: 정보를 수집하는 봇의 외부링크 수집을 막아준다.


```shell
$ npm i hexo-autonofollow
```

설치를 진행하고 _config.yml에 `nofollow` 속성을 추가한다.

```yml _config.yml
nofollow:
  enable: true
  exclude:
    - exclude1.com
    - exclude2.com
```


### hexo-generator-seo-friendly-sitemap

`sitemap.xml` 파일로 크롤링하는 봇이 효율적으로 작업할 수 있도록 유도한다.

```shell
$ npm i hexo-generator-seo-friendly-sitemap
```

```yml _config.yml
sitemap:
  path: sitemap.xml
  tag: false
  category: false
```



### hexo-generator-feed

feed: `Atom1.0`과 `RSS2.0` 같은 피드를 의미하며, 봇이 최신 정보를 쉽게 수집할 수 있도록 유도한다.

```shell
$ npm i hexo-generator-feed
```

```yml _config.yml
feed:
  type: rss2
  path: rss2.xml
  limit: 20
```

### hexo-generator-robotstxt

`robots.txt` 파일을 생성해서 봇에게 블로그 페이지 수집 권한에 대해 알려주는 역할을 한다.

```shell
$ npm i hexo-generator-robotstxt
```

```yml _config.yml
robotstxt:
  useragent: '*'
  allow:
    - /
  sitemap: https://<userID>.github.io/sitemap.xml
```



### 요약

```shell
$ npm install hexo-auto-canonical //ikarus 테마는 생략
$ npm i hexo-autonofollow
$ npm i hexo-generator-seo-friendly-sitemap
$ npm i hexo-generator-feed
$ npm i hexo-generator-robotstxt
```

```ejs ./theme/layout/common/head.ejs [ikarus는 생략]
<%- autoCanonical(config, page) %>
```

```yml _config.yml
nofollow:
  enable: true
  exclude:
    - exclude1.com
    - exclude2.com
sitemap:
  path: sitemap.xml
  tag: false
  category: false
feed:
  type: rss2
  path: rss2.xml
  limit: 20
robotstxt:
  useragent: '*'
  allow:
    - /
  sitemap: https://<userID>.github.io/sitemap.xml
```


### 적용 확인하기

`hexo g` 이후 public 디렉토리 내에 rss, sitemap, robots가 정상적으로 생성됐는지 확인해보자.


## 검색엔진 등록하기

세팅전 열심히 지졌으니 이젠 검색 엔진에 떠먹여주면 끝난다.


### Google

우선 신과 같은 시선에 있는자 **Google**부터 시작하자

[Google Search Console](https://search.google.com/search-console/welcome?utm_source=wmx&utm_medium=deprecation-pane&utm_content=home#utm_source=ko-wmxmsg&utm_medium=wmxmsg&utm_campaign=bm&authuser=0)에 들어가서 블로그 주소를 입력

![Google Search Console](\images\2111\hexo_blog_SEO\google1.png)

소유권 확인을 위한 파일을 다운받고

![Google Search Console](\images\2111\hexo_blog_SEO\google2.png)

해당 파일을 public에 위치시킨 다음 배포(`hexo d`)한다.

난 clean 명령어를 사용하기 때문에 `themes/blog_theme/source` 아래에 위치시켰다.
※ 블로그 post를 작성하는 `source` 아래에 위치시키면 html 파일 뿐 아니라 post 형식도 따라와서 소유확인이 안된다. 주의하자.

소유권이 확인됐으면 속성으로 이동해서 xml 파일들을 제출하면 된다.

다음으로 sitemap 탭에서 주소를 추가하면 되는데,

![Google Search Console](\images\2111\hexo_blog_SEO\google3.png)

URL 입력창에 `sitemap.xml`과 `rss2.xml`을 각각 제출하면 되겠다.

사이트맵 색인에 더럽게 오래걸리니 가져올 수 없음 상태여도 일단 다른 검색 엔진도 설정하고 기다려보자.


### Naver

사실 난 Google 엔진 이외엔 거의 안쓰지만 우리나라 대표 검색 엔진인 네이버엔 나와야겠다.
게다가 구글이랑 인증 및 설정 방식이 비슷하기 때문에 부담도 안된다.

[네이버 웹마스터 도구](https://searchadvisor.naver.com/auth/callback?code=J2ypAGbuKY7szLtgnD&state=0b8403b2b180270c19db493a1264b46911fea612)에 접속해서 google과 똑같이 html로 사이트 소유 인증받으면 된다.

인증 받은 뒤엔 RSS2와 sitemap 주소를 넣어주자.

![naver RSS](\images\2111\hexo_blog_SEO\naverRSS.png)

![naver sitemap](\images\2111\hexo_blog_SEO\naversitemap.png)



내 경우엔 사이트맵 제출이 굉장히 오래걸렸는데, 우선 URL 검사로 sitemap URL을 색인 요청해보자.


## 외부링크
 - [내 github blog 글이 구글 검색에 나오는 법](https://chinsun9.github.io/2020/09/23/%EB%82%B4-github-blog-%EA%B8%80%EC%9D%B4-%EA%B5%AC%EA%B8%80-%EA%B2%80%EC%83%89%EC%97%90-%EB%82%98%EC%98%A4%EB%8A%94-%EB%B2%95/)
 - [[Hexo Blog] 구글 사이트 등록 및 검색엔진 최적화(SEO)](https://msj0319.github.io/2020/02/14/Hexo-Blog-%EA%B5%AC%EA%B8%80-%EC%82%AC%EC%9D%B4%ED%8A%B8-%EB%93%B1%EB%A1%9D-%EB%B0%8F-%EA%B2%80%EC%83%89%EC%97%94%EC%A7%84-%EC%B5%9C%EC%A0%81%ED%99%94-SEO/)
 - [noindex](https://developers.google.com/search/docs/advanced/crawling/block-indexing?visit_id=637745640908544706-4252701127&rd=1)
 - [robots.txt tester](https://support.google.com/webmasters/answer/6062598)
 - [사이트맵 등록 성공, URL 색인 성공](https://julynine2.tistory.com/entry/%EA%B5%AC%EA%B8%80-%EC%84%9C%EC%B9%98-%EC%BD%98%EC%86%94%EC%97%90%EC%84%9C-%EC%82%AC%EC%9D%B4%ED%8A%B8%EB%A7%B5-%EB%93%B1%EB%A1%9D-%EC%84%B1%EA%B3%B5-URL-%EC%83%89%EC%9D%B8-%EC%83%9D%EC%84%B1-%EC%84%B1%EA%B3%B5)