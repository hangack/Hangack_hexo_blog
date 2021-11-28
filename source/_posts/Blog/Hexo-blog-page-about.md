---
title: Hexo 블로그 about 페이지 생성하기
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
date: 2021-11-17 10:01:26
---

icarus 테마를 사용하다가 상단의 About이 있지만 경로를 찾지 못해 about 페이지를 만들어봤다.

hexo에서는 특정 경로를 어느 페이지에서든 진입할 수 있게 테마 옵션에서 navbar를 지원한다.

icarus 테마는 기본적으로 about 페이지 경로가 설정되어있지만 `_config.theme.yml`에서 표시할 장소에 `About(text): /about(경로)`을 추가한다.
```yml
# Page top navigation bar configurations
navbar:
    # Navigation menu items
    menu:
        Home: /
        Archives: /archives
        Categories: /categories
        Tags: /tags
        About: /about
```

이런식으로 menu바 설정을 했으면 해당 URI에 대응할 수 있는 경로를 만들어줘야한다.

`source`경로 아래에 원하는 경로를 만들어주는 `page` layout을 이용해서 about 경로를 생성하자.
```shell
$ hexo new page about
```

위 명령어가 정상 작동되었으면 `/about` 경로가 생성되고 그 아래 `index.md` 파일도 따라 왔을것이다.
index.md가 about에 대한 page로 포스트 작성하듯 원하는 내용을 작성하면된다.


## 외부링크
 - [How to add route for Hexo?](https://stackoverflow.com/questions/29167023/how-to-add-route-for-hexo)