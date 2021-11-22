---
title: Hexo toc(Katalog) 사용하기
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
    collapsed: true
    depth: 6
  - type: categories
    position: left
sidebar:
  left:
    sticky: true
toc: true
date: 2021-11-22 09:39:47
---

## Katalog? toc?

TOC: Table of contents, 목차

위키 등에서 주로 사용되는 index식 목차이며 클릭 시 해당하는 열로 이동하는 메커니즘이라 인식하면 된다.

### Markdown에서 목차

html에서는 `<h#>`을 사용해서 목차를 표현하지만 md에서 목차 구분은 `#`의 개수로 한다.

기본값으로 # 1개는 post 제목 크기와 동일해, 나는 h2: `##`부터 사용한다.

h4: `####`부터는 기본 text 크기와 구분하기 어려우며 h5는 기본 텍스트와 크기가 같을 것이다.

#### h4
h4

##### h5
h5

###### h6
h6

####### h7
h7

######## h8
h8

테스트로 h8까지 작성해봤는데, hexo에선 h6까지만 인식한다.



## toc 사용하기


Toc을 지원하는 테마를 사용한다면,
Front-matter에 `toc: true`를 넣어줌으로 사용할 수 있다.

```markdown
---
title: {{ title }}
date: {{ date }}
toc: true
---
```
위 Front-matter는 나의 page.md 설정값


### toc 적용 확인

`hexo s`로 local 확인을 하거나 `hexo g -d`로 배포해서 toc 정상 적용되었는지 확인해본다.

<center><img src="\images\2111\blogToc\Katalog1.png" alt="TOC"></center>


### icarus에서 세부 설정

icarus theme는 config에 toc type을 설정할 수 있도록 기본값이 작성되어있다.

Hexo icarus TOC default값
```yml
    # Table of contents widget configurations
    -
        # Where should the widget be placed, left sidebar or right sidebar
        position: left
        type: toc
        # Whether to show the index of each heading
        index: true
        # Whether to collapse sub-headings when they are out-of-view
        collapsed: true
        # Maximum level of headings to show (1-6)
        depth: 3
```

position: Katalog box 위치
index: Katalog box 목차 앞에 숫자를 표현할 지 (ex: `1.2 icarus에서 세부 설정`)
collapsed: 하위목차 간략화
depth: #번째 하위 목차까지 표시

＊2021/11/20 기준 내 설정
```yml
    # Table of contents widget configurations
    -
        # Where should the widget be placed, left sidebar or right sidebar
        position: left
        type: toc
        # Whether to show the index of each heading
        index: false
        # Whether to collapse sub-headings when they are out-of-view
        collapsed: false
        # Maximum level of headings to show (1-6)
        depth: 2
```

depth를 6으로 설정해주면 위에서 test한 h6까지 katalog에 표시될 것


## 외부링크
 - [Hexo Front-matter](https://hexo.io/ko/docs/front-matter.html)
 - [Hexo Helpers](https://hexo.io/ko/docs/helpers.html)