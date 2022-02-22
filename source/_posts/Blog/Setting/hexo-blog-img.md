---
title: hexo blog img(avatar, favicon, logo) 변경하기
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
date: 2021-11-23 11:59:56
---

# Hexo 이미지 변경

hexo blog에서 사용하는 avatar, favicon, logo 등을 변경하는 방법은 간단하게 `public\img` 경로의 파일명을 그대로 이미지만 교체해주면 된다.

<img src="/images\2111\Hexo_blog_img/public.png" alt="public">

## `Hexo clean`의 경우 문제점

하지만 블로그 관리 초기라 설정을 변경하거나 이미지를 교체하는 등 파일 첨삭이 있을 때마다 `$ hexo clean` 명령어를 남발하는데,
clean은 캐쉬 파일인 public 폴더를 통으로 삭제하는 명령어다.

그럼 캐쉬를 지울 때마다 img 내의 이미지들을 수정해줘야 한다.

난 이런 번거로운 일은 못한다.

그렇기에 `$ hexo g`의 작동방식을 알아야한다.
generate는 불러올 theme와 user의 config를 유지한 채, user의 source 디렉토리에서 UnderBar( `_` ) 표시된 경우나 `_posts`같은 특수한 경우를 제외하고 public 폴더에  그대로 붙여넣는 특징이 있다.

그럼 해결법은 간단하다. `source\img`경로를 만들어서 원하는 파일을 `_config.theme.yml`에서 설정한 파일명 그대로 넣어두면 끝이다.

<img src="/images\2111\Hexo_blog_img/source.png" alt="source">


## _config.theme.yml 설정 변경

경로를 수정하기 전에 각각의 이미지가 어떤 요소를 뜻하는지 알아야한다.

_config.theme.yml을 직접 뜯어보는걸 권장하지만 간단히 내가 설정한 4놈을 icarus 기준으로 설명하자면,
 - avatar: 블로그 좌측에 표시된 블로거의 아바타
 - favicon: 브라우저 열린 page 바에 표시되는 블로그 아이콘
 - logo: 블로그 상단의 대각선으로 Han-Gack
 - og_image: open_graph에 걸리는 이미지
   - open_graph: 외부 사이트에서 링크됐을 때 정보를 알려주기 위해 설정하는 옵션, 이미지 파일명이 기본값이랑 다르다면 `head - open_graph` 탭의 `image`를 설정하면 된다.
   
명칭에 대한 정보를 알았으니 yml 파일에서 파일명과 확장자명에 주의하며 사용할 옵션 위주로 수정하면된다.


