---
title: Hexo Blog Category 사용하기
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
date: 2021-11-21 8:45:32
---
  
# Category
 
<center><img src="\images\2111\Heox_blog_Category\category.png" alt="ㅏㅏ 이것이 Category란 것이다"></center>


# Hexo Category 설정하기

Hexo를 처음 사용한다면 Front-matter 영역에는 기본적으로 title, date, tags만 나와있을 것이다.

순서는 상관 없으니 `categories:`를 추가하자.
참고로 `categories`와 `tags`는 `-` 로 관리할 수 있다.
```yml
title: {{ title }}
date: {{ date }}
categories:
 - 
tags:
 - 
```

※ 태그와 카테고리의 가장 큰 차이점: 카테고리는 하위 `-`로 하위 카테고리가 생성되지만, 태그는 하위 태그의 개념이 없다.


## scaffolds로 post 기본설정하기

포스팅이 한두개도 아니고 포스팅을 할 때마다 `categories:`를 넣어주는건 너무나도 귀찮은 방식이다.

`\scaffolds\post.md`를 원하는 형식으로 수정하면 `hexo new`명령어로 post를 생성할 때 불러오는 기본 양식을 바꿀 수 있다.

만약 [Hexo draft](https://hangack.github.io/2021/11/16/Blog/hexo-post-private/)로 신규 post를 관리한다면 `draft.md`를 수정해주면 된다.



# 외부링크
 - [Hexo Front-matter](https://hexo.io/ko/docs/front-matter.html)