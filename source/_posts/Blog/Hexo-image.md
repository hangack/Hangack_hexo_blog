---
title: Hexo 블로그 Local 경로 이미지 삽입하기
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
date: 2021-11-19 14:31:41
---
  
markdown 문법으로 이미지를 삽입한다면 아래 링크를 참조
[Markdown 하이퍼링크 이미지 넣기](https://hangack.github.io/2021/11/09/Codding/MarkDown/Markdown-href-img/)

### ※ hexo URI

hexo blog에서 post를 작성할 때 기본 path URI를 알아두면 편리하게 주소를 입력할 수 있다.
hexo URI는 기본적으로 `source` 폴더이므로 source 이후의`(/경로/파일.확장자)`만 입력해서 Local 주소를 넣을 수 있다.

Hexo에서 지정한 default 이미지 폴더는 `/source/images`이다.

Hexo 기본 경로를 따른다면 
```markdown
![alt](/images/dir/file_name.extension)
```
으로 삽입하면된다.

## 외부링크
 - [Hexo Asset Folders](https://hexo.io/ko/docs/asset-folders.html)