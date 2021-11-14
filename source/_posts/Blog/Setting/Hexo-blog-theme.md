---
title: Hexo 테마변경(Feat. icarus)
categories:
  - 블로그
  - 설정
tags: 
  - 블로그
  - 설정
  - hexo
date: 2021-11-02 18:22:56
---

[Hexo 블로그 만들기](https://hangack.github.io/2021/11/01/Blog/Setting/Hexo-blog/)

## 테마 선택

[hexo themes](https://hexo.io/themes/)에서 다양한 오픈소스 테마를 얻을 수 있다.
게임을 하더라도 바닐라 버전을 좋아해서 깔끔한 테마를 원했고, 설정을 조금 변경한다면 [icarus 테마](https://ppoffice.github.io/hexo-theme-icarus/)가 깔끔한데다 업데이트도 활발하다고 생각한다.


## icarus 시작하기

icarus에서 지원하는 여러 테마중에 [바닐라 Icarus](https://ppoffice.github.io/hexo-theme-icarus/uncategorized/getting-started-with-icarus/#install-npm)로 설정할 예정이다.

테마를 설치하면서 Error 메세지를 보고 해당하는 hexo 랜더러 플러그인을 npm으로 설치해줘도 문제없지만,
에러 메세지에 알러지가 있다면
```shell
$ npm install --save bulma-stylus@0.8.0 hexo-renderer-inferno@^0.1.3
```
위 명령어로 우선 CSS 프레임워크 `bulma-stylus`와 `inferno` 랜더러 플러그인을 받아오자.

icarus 테마 페이지에서 install via NPM 탭 명령어로 icarus 테마 기본설정을 설치한다
```shell
$ npm install -S hexo-theme-icarus
```

이카루스 테마를 설치했으면 `_config.yml`의 `Extensions` 영역의 `theme` 값을 변경해준다.
```yml
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: icarus
```

`hexo s`로 local에서 적용을 확인하고 `hexo g -d`로 적용, 배포를 진행하면된다.