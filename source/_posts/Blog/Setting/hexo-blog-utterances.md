---
title: 블로그 댓글 utterances 사용하기
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
date: 2021-11-24 06:17:54
---


## utterances 세팅  

[utterances](https://utteranc.es/)에 들어가서 설명을 읽어보는게 좋다.

### github repo 생성

사용하기 위해 개인 github에 comment용 **public** repository를 생성한다.

<center><img src="\images\2111\hexo_blog_utterances\new repo.png"></center>

굳이 repo를 생성하고 싶지 않다면 userID.github.io repo를 사용해도 된다.


### app 설치

[utterances app](https://github.com/apps/utterances)에 들어가서 github에 app을 설치하자.
나는 comment가 들어갈 repo인 `hangack_blog_comment`만 지정했다.


### 요소 설정하기

`repo: `박스에 위에서 생성한 개인 `userID/repoName`을 입력한다.

<center><img src="\images\2111\hexo_blog_utterances\issue mapping.png"></center>

**Blog Post ↔️ Issue Mapping** 방식은 현재 상황엔 별로 중요하지 않지만 개인 세팅에 따라 반드시 특정 세팅을 지정할 필요도 있을 것이다.

1. pathname
 - 포스트의 URI로 issue가 생성된다. URI가 바꼈을 때 문제가 될지도?
2. URL
 - URL 기준으로 생성
3. title
 - 포스트 제목
4. og:title
 - open_graphic 제목
5. Specific issue number
 - 이슈 번호를 생성해서 작성된다.
6. specific term
 - 포스트 제목에 기입된 특정 단어를 기준으로 작성된다.

## 댓글 위젯 넣기

### utterances에서 제안된 방식

테마 등 설정을 전부 끝냈다면 **Enable Utterances** 분류에 script 코드가 생겼을 것이다.

```html
<script src="https://utteranc.es/client.js"
        repo="userID/repoName"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>
```

이 코드를 post마다 넣어주면된다.

hexo의 경우엔 post.md 혹은 draft.md로 불러올 수 있겠지


### hexo icarus에서

icarus에서는 utterances 타입을 지원하기에 `_config.theme.yml`에 comment 항목을 찾아서 아래 형식대로 기입하자.

```yml
comment:
    type: utterances
    repo: userID/repoName
    issue_term: pathname
    theme: github-light
    crossorigin: anonymous
```

### 어? 안되잖아?

`utterances.json` 파일을 뜯어봤더니 crossorigin 요소에 대한 처리 방식이 없었다.

반면, `utterances.js` 파일에선 `"crossorigin": "anonymous"`로 기본값을 지정했기에 문제없다 판단하고 요소를 제거

```yml
comment:
    type: utterances
    repo: userID/repoName
    issue_term: pathname
    theme: github-light
```

댓글댓글단다


## 외부링크
 - [disqus에서 utterances로 바꾸기](https://chinsun9.github.io/2021/06/08/blog-comment-migration-from-disqus-to-utterances/)
 - [utterances 적용](http://astrod.github.io/etc/2018/05/28/utterances-%EC%A0%81%EC%9A%A9/)