---
title: Hexo blog markdown 수식 표현 mathjax
categories:
  - 블로그
  - 설정
tags:
  - 블로그
  - 설정
  - hexo
  - 수식
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
thumbnail: /thumbnails/CS/mathjax.png
date: 2021-11-13 15:14:52
---

분명 MarkDown math tutorial대로 수식을 작성하고 Ipython notebook에서도 정상적으로 출력되는걸 확인했지만,
Hexo post는 아래처럼 읽어내지를 못한다.
![으아악 아니야!](/images/2111/Hexo_mathjax/hexoNotMath.png)

## Hexo plugin 설치

다른 블로그 모듈을 사용하는 방법도 있지만, Hexo를 설치했으니 그대로 사용하기 위해 우선 구글링으로 해결해본다.
검색 결과 hexo에서 사용하는 랜더링 모듈에 수식표현 문법이 포함되어 있지 않아서 발생하는 문제였다.


### 기본 renderer 교체

Hexo의 기본 renderer인 marked를 제거하고 mathjax를 지원하는 kramed로 교체한다.

```shell
$ npm uninstall hexo-renderer-marked --save
$ npm install hexo-renderer-kramed --save
```

설치가 완료되면 `..\node_modules\hexo-renderer-kramed\lib\renderer.js`에서 `formatText` 함수의 반환값을 변경해준다.
```js
// Change inline math rule
function formatText(text) {
  // Fit kramed's rule: $$ + \1 + $$
    return text;
//    return text.replace(/`\$(.*?)\$`/g, '$$$$$1$$$$');  // (: default)
}
```

### mathjax 설치

kramed 랜더러에 설정값을 넣어줄 mathjax 랜더러를 설치한다.

```shell
$ npm install hexo-renderer-mathjax --save
```

마찬가지로 `..\node_modules\hexo-renderer-mathjax\mathjax.html`에서 스크립트 source url을 교체한다.
```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.2/MathJax.js?config=TeX-MML-AM_CHTML"></script>
<!-- <script src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script> --> <!--: default -->

```

## Mathjax 활성

이제 사용하고 있는 `_config.theme.yml`에서 `mathjax`를 활성화 시켜주면된다.

```yaml
    mathjax:
        enable: true
    # mathjax: false    # : default
```

markdown 문법을 사용할 예정이라 문법 추가 설정은 하지 않는다.

## 예제
[오...](https://hangack.github.io/2021/11/15/Codding/MarkDown/markdown-%EC%88%98%EC%8B%9D-%EB%84%A3%EA%B8%B0/)

## 외부링크

 - [hexo-math](https://github.com/hexojs/hexo-math)
 - [Hexo 블로그-mathjax](https://hyeshinoh.github.io/2018/10/24/hexo_mathjax_00/)