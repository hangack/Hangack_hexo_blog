---
title: Markdown 하이퍼링크 이미지 넣기
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
date: 2021-11-09 16:27:25
---

## URL 넣기

### URL 단순 입력

단순히 표현하고 싶은 url을 붙여넣으면 아래처럼 해당 text가 url로 링크된다.
엘든링? https://en.bandainamcoent.eu/elden-ring/elden-ring
```markdown
엘든링? https://en.bandainamcoent.eu/elden-ring/elden-ring
```

### URL 삽입

하지만 아래처럼 url 뒤로 띄어쓰기가 없을 경우 `<` , `>`로 묶어줘야 정확한 URL 표시가 가능하다.
엘든링 <https://en.bandainamcoent.eu/elden-ring/elden-ring>엘?든링
```markdown
엘든링 <https://en.bandainamcoent.eu/elden-ring/elden-ring>엘?든링
```
### 텍스트 하이퍼링크

특정 텍스트에 URL을 링크하는 text href를 사용하고 싶을 경우엔 `[text](URL)` 형식으로 작성하면 된다.

[엘?든?링?](https://en.bandainamcoent.eu/elden-ring/elden-ring)
```markdown
[엘?든?링?](https://en.bandainamcoent.eu/elden-ring/elden-ring)
```

### URL 참조

하나의 URL을 여러번 사용해야할 때 참조 URL을 익혀두면 편하다.

[엘든링][ER][엘든링?][ER][엘?든?링][ER][엘?
든?
링?][ER]
[엘든링!][ER]
[22년 2월 25일 대발매][ER]

[ER]: https://en.bandainamcoent.eu/elden-ring/elden-ring

```markdown
[엘든링][ER][엘든링?][ER][엘?든?링][ER][엘?
든?
링?][ER]
[엘든링!][ER]
[22년 2월 25일 대발매][ER]

[ER]: https://en.bandainamcoent.eu/elden-ring/elden-ring
```


### 이미지 삽입

이미지 삽입은 Href 형식 앞에 `!`를 붙여 `![alt](URL)`로 작성한다.

![Elden Ring](https://p325k7wa.twic.pics/high/elden-ring/elden-ring/00-page-setup/eldenring_new.png?twic=v1/cover=800x267/step=10/quality=80)
```markdown
![Elden Ring](https://p325k7wa.twic.pics/high/elden-ring/elden-ring/00-page-setup/eldenring_new.png?twic=v1/cover=800x267/step=10/quality=80)
```


### 이미지 하이퍼링크

그럼 이미지에 링크를 넣는 방법은 어떻게 해야할까?

이미지 표현문을 `[` , `]`로 묶어 text 처럼 표현하고 그 뒤에 href를 작성하면 된다.
ex) `[![alt](URL)](Href)`

[![엘든링 보러가기](https://p325k7wa.twic.pics/high/elden-ring/elden-ring/00-page-setup/eldenring_new.png?twic=v1/cover=800x267/step=10/quality=80)](https://en.bandainamcoent.eu/elden-ring/elden-ring)
```markdown
[![엘든링 보러가기](https://p325k7wa.twic.pics/high/elden-ring/elden-ring/00-page-setup/eldenring_new.png?twic=v1/cover=800x267/step=10/quality=80)](https://en.bandainamcoent.eu/elden-ring/elden-ring)
```

[Hexo local image 삽입하기](https://hangack.github.io/2021/11/18/Blog/Hexo-image/)

## 참조
 - [[LYNMP 도움말] 마크다운(Markdown) 문법 - 링크 삽입](https://lynmp.com/ko/article/title/markdown-link-ua811c9dc59o)