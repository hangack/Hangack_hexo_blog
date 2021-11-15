---
title: Hexo 포스트 비공개로 설정하기
categories:
  - 블로그
tags: 
  - 블로그
  - hexo
date: 2021-11-16 02:37:18
---

## dash( _ ) 사용하기

dash( `_` )를 title 앞에 붙여주면 hexo에서 private post로 인식하고 배포하지 않는다.
![MAE-MSE-RMSE.md: 비공개](/images/2111/private_post/dash.png)


## _drafts 폴더로 관리

`scaffolds` 폴더에 new post로 생성되는 포스트의 기본 [layout]을 저장할 수 있다.
`_config`의 default값은 `post`로 아래 명령어에 [layout]을 지정하지 않는다면 new post는 `post` layout으로 생성된다
```shell
$ hexo new [layout] <title>
```

`draft` layout으로 new post를 생성하면 `_drafts` 폴더에 post가 생성되는데, post title 앞에 dash가 없더라도 private post로 인식된다.
layout을 `draft`로 지정하면 `_drafts` 폴더 하위에 new post가 생성된다.
```shell
$ hexo new draft <title>
```


### 외부링크
 - [Hexo 명령어](https://hexo.io/ko/docs/commands.html)