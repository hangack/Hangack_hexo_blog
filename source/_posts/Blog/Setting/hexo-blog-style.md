---
title: hexo blog CSS 스타일 변경하기 (Feat. icarus theme)
categories:
  - 블로그
  - 설정
tags: 
  - 블로그
  - 설정
  - hexo
  - css
  - js
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
thumbnail: /thumbnails/CS/css3.svg
date: 2021-11-28 12:54:52
---
  

# 블로그 스타일 세부설정을 위한 icarus theme 폴더

이전 포스팅인 [블로그 테마 세부설정을 위한 clone theme](https://hangack.github.io/2021/11/25/Blog/Setting/hexo-blog-clone-theme/)를 보고오자.


# Chrome DevTools

HTML? 몰?루 하던 시절엔 왜째서 기본 탑재된지 이해가 안가던 툴, 브라우저에서 `F12`를 누르면 어김없이 등장하는 코드뭉치 박스를 기억할 것이다.

오늘 만큼은 이놈을 유용하게 사용할 수 있겠다.

![문제의 그 BOX](\images\2111\hexo_blog_CSS\devtools.png)

DevTools 위에 나오는 코드 뭉탱이(`Elements`)가 해당 페이지의 구성 요소들의 배치 형식, 아래 나오는 `Styles` 박스가 `Elements`에서 클릭한 요소의 CSS stlye로 보면된다.

사실 위 2개만 알면 건물을 새로 짖는게 아닌 이상 인테리어 수정 방법은 다 배운 셈이다.


## 수정하고픈 요소 찾기

DevTools에서는 친절하게도 임의 요소에 마우스를 올려두기만 해도 어느 영역에 대한 `Class`인지 화면에 표시해준다.

![요소 식별](\images\2111\hexo_blog_CSS\find class.png)

팁이 있다면 DevTools 좌측 상단의 "Select an element in the page to inspect it - Ctrl+Shift+C" 버튼을 눌러보자

<center><img src="\images\2111\hexo_blog_CSS\mouse.png"></center>


식별된 요소가 포함된 class들을 기억하자.

내가 수정할 요소는 `nav: pagination` / `ul: pagination-list is-hidden-mobile` / `a: pagination-link is-current`인거같다.

`pagination.stly` 파일 안에서 `pagination` 요소와 `pagination-link.is-current` 하위 요소를 찾을 수 있었다.
중간의 ul은 moblie 모드에서는 숨기는 옵션? js로 설정하는 예외인거같다.

![style](\images\2111\hexo_blog_CSS\change option.png)

article의 img 요소처럼 style 커스텀 값이 없다면 부모 객체 아래에 직접 넣어주면 된다.


## 스크롤바 스타일 변경

집에서 쓸 때는 마우스 사이드 버튼에 `page up/down`을 할당하고 써서 몰랐는데, 외부에서 블로그에 접속하니 사이드바가 쥐꼬리만한게 너무 불편했다.

궁금하면 [icarus](https://ppoffice.github.io/hexo-theme-icarus/)에서 desktop mode로 직접 확인 ㄱㄱ

`Elements`에서 스크롤바를 정상적으로 식별할 수 없었지만, html 전체 요소 `style`에서 `-wibkit-scrollbar`라는 놈을 찾을 수 있었다.

쓸일이 있을진 모르겠지만 주석처리 해놓자.

```javascript .\include\style\base.styl
/* ---------------------------------
 *+desktop()
 *    ::-webkit-scrollbar
 *        width: 8px
 *        height: 8px
 *
 *    ::-webkit-scrollbar-track
 *        border-radius: 3px
 *        background: rgba(0,0,0,0.06)
 *        box-shadow: inset 0 0 5px rgba(0,0,0,0.1)
 *
 *    ::-webkit-scrollbar-thumb
 *        border-radius: 3px
 *        background: rgba(0,0,0,0.12)
 *        box-shadow: inset 0 0 10px rgba(0,0,0,0.2)
 *
 *    ::-webkit-scrollbar-thumb:hover
 *        background: rgba(0,0,0,0.24)
 * --------------------------------- */
```