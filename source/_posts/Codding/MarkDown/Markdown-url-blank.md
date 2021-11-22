---
title: Markdown 이미지파일 URL 경로에 띄어쓰기가 있는 경우
categories:
  - 연습
  - 마크다운
tags:
  - 마크다운
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
date: 2021-11-16 10:27:25
---
  

[Markdown 이미지 삽입](https://hangack.github.io/2021/11/09/Codding/MarkDown/Markdown-href-img/) 포스팅처럼 md 어법으로 이미지를 삽입하다가 한가지 난관에 부딛혔다.


<center><img src="\images\2111\md url blank\url.png" alt="공백"></center>

image url에 공백이 들어간 것.

※ 현재 hexo 랜더러를 kramed로 변경한 상태라 아래처럼 공백도 인식한다.
 - 마찬가지로 hexo 기본 내장 tag 플러그인 어법으로 블로그 포스트는 해결 가능

![우린 답을](\images\2111\md url blank\interstellar poster.png)
```markdown
![우린 답을](\images\2111\md url blank\interstellar poster.png)
```


하지만 ipynb 형식 등 개발환경에서 md 셀을 사용할 때는


<center><img src="\images\2111\md url blank\ipy.png" alt="jupyter"></center>

여전히 발생하는 문제다.


html처럼 `&nbsp;`를 공백 대신 넣어보기도 하고 cmd 마냥 `""`로 묶는 등 코랄을 했지만 markdown 어법으로는 해결하지 못했다.

markdown이 html 어법도 지원하는걸 기억하고 html img 태그로 해결했다.

<img src="\images\2111\md url blank\interstellar poster.png" alt="찾을 것">

```
<img src="\images\2111\md url blank\interstellar poster.png" alt="찾을 것">
```

html 어법을 사용하면 md로 구현 가능한 하이퍼링크 `<a href=""></a>` tag는 당연하고
가운데 정렬(`<center></center>`)부터 이미지 크기 변경이 가능한 img 태그 `size` 요소 등 풍부한 표현이 가능하다.
