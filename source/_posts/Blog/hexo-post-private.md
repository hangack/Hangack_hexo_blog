---
title: Hexo 포스트 비공개로 설정하기
categories:
  - 블로그
tags: 
  - 블로그
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
date: 2021-11-16 02:37:18
---

# UnderBar( _ ) 사용하기

UnderBar( `_` )를 title 앞에 붙여주면 hexo에서 private post로 인식하고 배포하지 않는다.
![MAE-MSE-RMSE.md: 비공개](/images/2111/private_post/dash.png)


# _drafts 폴더로 관리

`scaffolds` 폴더에 new post로 생성되는 포스트의 기본 [layout]을 저장할 수 있다.
`_config`의 default값은 `post`로 아래 명령어에 [layout]을 지정하지 않는다면 new post는 `post` layout으로 생성된다
```shell
$ hexo new [layout] <title>
```

`draft` layout으로 new post를 생성하면 `_drafts` 폴더에 post가 생성되는데, post title 앞에 UnderBar가 없더라도 private post로 인식된다.
layout을 `draft`로 지정하면 `_drafts` 폴더 하위에 new post가 생성된다.
```shell
$ hexo new draft <title>
```


# 외부링크
 - [Hexo 명령어](https://hexo.io/ko/docs/commands.html) 