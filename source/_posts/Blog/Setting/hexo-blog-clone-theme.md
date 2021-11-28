---
title: 블로그 테마 세부설정을 위한 clone theme
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
date: 2021-11-25 05:35:36
---

## 문제 발생

테마 스타일 커스텀을 하려 봤더니 Hexo v5 이후 방식인 npm으로 _config.icarus만 불러왔던 [방식](https://hangack.github.io/2021/11/02/Blog/Setting/Hexo-blog-theme/)이 내 발목을 잡았다.

theme를 처음부터 다시 받아야할까?

_태초마을인가 그릉가?_

## 테마 폴더 끌어오기

그럴필욘 없고 themes 디렉토리에 테마 세부 설정을 위한 패키지만 받아오면 된다.

과거에 설정했던 [테마 깃허브](https://github.com/ppoffice/hexo-theme-icarus)에 들어가서 Clone url을 받는다.

다음으로 `\themes\` 경로에 `$ git clone`하면되지만, [themes 폴더에 icarus 테마깔기](https://chinsun9.github.io/2020/11/12/%EC%BB%A4%EC%8A%A4%ED%85%80-%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83/)에서 좋은 제안을 발견했다.
```shell
$ git clone --depth 1 https://github.com/ppoffice/hexo-theme-icarus.git
```

마지막으로 테마명을 일치시키기 위해 불러온 hexo-theme-icarus 디렉토리를 icarus로 변경해줬다.

가장 답답했던 페이지 가로축 범위 조정도 [hexo icarus 테마에 커스텀 레이아웃, 스타일(css) 적용하기](https://chinsun9.github.io/2020/11/12/%EC%BB%A4%EC%8A%A4%ED%85%80-%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83/)에서 적용법을 확인할 수 있었다.



## 외부링크
 - [hexo icarus 테마에 커스텀 레이아웃, 스타일(css) 적용하기](https://chinsun9.github.io/2020/11/12/%EC%BB%A4%EC%8A%A4%ED%85%80-%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83/)
