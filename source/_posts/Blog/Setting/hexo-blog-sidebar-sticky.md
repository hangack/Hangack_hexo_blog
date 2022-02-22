---
title: hexo blog sidebar 트래킹과 post 개별 설정
categories:
  - 블로그
  - 설정
tags: 
  - 블로그
  - 설정
  - hexo
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
thumbnail: /thumbnails/CS/hexo.svg
date: 2021-11-22 20:42:59
---
  

# toc

[Hexo toc(Katalog) 사용하기](https://hangack.github.io/2021/11/22/Blog/Setting/hexo-blog-toc/)에서 toc(Katalog)를 적용해 봤다.


# sidebar sticky

하지만 sidebar가 트래킹되지 않아 불편하다.
현재 사용하는 icarus테마는 `_config.theme.yml`에서 다양한 옵션을 제공한다. 그 중 `sidebar - left(or right) - sticky`옵션이 트래킹 옵션이다.

위젯 박스를 왼쪽만 사용하고 있으니 
```yml
sidebar:
    # Left sidebar configurations
    left:
        # Whether the sidebar sticks to the top when page scrolls
        sticky: true
```
로 설정하면 언제 어디서나 sidebar가 트래킹된다.

그렇다 어디서든 언제언제까지나 트래킹되는게 문제다.

원하는 방식은 특정 post를 읽을 때만 트래킹되는 방식이었으니 _config.theme.yml의 sticky 값은 다시 `false`로 돌려놓자.


# post 개별 설정

우리에겐 scaffolds 디렉토리 내 post 기본 양식 설정과 `_config.theme.yml`에서 가져올 위젯 및 sidebar의 yml 양식이 있다.

그리고 이전 포스트에서 링크한 [Hexo Front-matter](https://hexo.io/ko/docs/front-matter.html)에선 
```yaml
---

---
```
내부 양식이 `yaml`이라 한다.

넣을 코드와 코드를 넣을 공간이 준비되었고 작성한 양식을 불러올 방법도 있으니 우리는 `draft.md`와 `post.md`를 수정하기만 하면 된다.
~~설정 전에 작성한 포스트가 많다면..야 너두?~~

toc 트래킹만 사용한다면 아래 코드를 넣어주면 된다.
```yaml
---
sidebar:
  left:
    sticky: true
widgets:
  - type: toc
    position: left
    index: false
toc: true
---
```

개별 설정의 단점은 _config의 모든 설정을 불러오지는 않기 때문에 각종 옵션을 넣는다면
```yaml draft.md
---
title: {{ title }}
date: {{ date }}
categories:
 - 
tags:
 - 
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
---
```
Wa!


# 외부링크
 - [Hexo Front-matter](https://hexo.io/ko/docs/front-matter.html)