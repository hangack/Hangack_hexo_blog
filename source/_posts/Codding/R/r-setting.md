---
title: Rstudio 처음 세팅하기
categories:
  - 연습
  - R
tags:
  - R
  - Rstudio
  - Rtools
  - 설정
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
thumbnail: /thumbnails/CS/Rstudio.png
toc: true
date: 2021-12-01 06:35:30
---
  

## Rstudio 기본 설치 프로그램
  
 - Rstudio는 [R 언어](https://cran.r-project.org/bin/windows/base/)를 사용하는 프로그램이니 R 언어팩을 설치한다.

 - 사용할 작업 환경인 [Rstudio](https://www.rstudio.com/products/rstudio/download/#download)도 받아주고,

 - [Rtools](https://cran.r-project.org/bin/windows/Rtools/)를 설치하면 R의 기본적인 Package 세트와 C/C++과 같은 의존성 세팅을 불러올 수 있다.


### Rstudio 기본 세팅

나는 memo 앱을 사용할 때도 자동 줄바꿈을 사용하는 편이기에 `Soft-wrap`를 체크했다.

![Soft-wrap R source files](\images\2112\R-download\soft-warp.png)

윈도우 환경이라면 언어 인코딩 방식을 `UTF-8`로 변경하는걸 추천한다.

![default text encoding](\images\2112\R-download\encoding.png)


### R Script

R studio 상단의 files 탭에서 project 경로를 생성하거나 py 혹은 ipynb 처럼 R Script, Rmd 파일창을 열 수 있다.

![new](\images\2112\R-download\files.png)



## Rtools path 설정

R Script 등을 열었다면 Rtools의 경로를 지정해준다.

```R
write('PATH="${RTOOLS40_HOME}\\usr\\bin;${PATH}"', file = "~/.Renviron", append = TRUE)
```

R은 PL/SQL처럼 동작한다. 원하는 명령어를 작성하고 해당 열에서 `Ctrl+Enter` 해주면 된다.


이후 Path값을 다시 불러오기 위해 R을 재시작한다. 나의 경우 R restart로 해결안되서 Rstudio 자체를 재실행했다.
그냥 깔끔하게 Rstudio를 껏다키는걸 추천한다.


## 패키지 불러오기

```R
install.packages("Package_Name")
#혹은
install.packages("Package_Name", dependencies = TRUE)
```


패키지 함수를 사용하려면 다른 프로그램 언어들처럼 file에서 package를 import 해줘야한다.

```R
library(Package_Name)
```

만약 콘솔에 사용하려는 패키지가 없다고 나온다면 `install.packages("패키지명")`를 해주자.

특수한 경우에 대한 오류는 [R 패키지 리스트](https://cran.r-project.org/web/packages/available_packages_by_date.html)에서 [stringi](https://cran.r-project.org/web/packages/stringi/index.html)처럼 시스템 기본 요구사항이 들어있는 경우다.

![stringi](\images\2112\R-download\stringi.png)

일반적인 경우는 Rtools 설치에서 해결됐을테니 크게 신경쓸 필욘 없다.



## 외부링크
 - [R language](https://cran.r-project.org/bin/windows/base/)
 - [R 패키지 리스트](https://cran.r-project.org/web/packages/available_packages_by_date.html)
 - [Rstudio](https://www.rstudio.com/products/rstudio/download/#download)
 - [Rtools](https://cran.r-project.org/bin/windows/Rtools/)

### 튜토리얼
 - [R for data science](https://r4ds.had.co.nz/)에서 기본적인 시각화(ch.03) 및 기초 문법(ch.05)을 확인할 수 있다.
 - [ggplot2 extensions - gallery](https://exts.ggplot2.tidyverse.org/gallery/)에서는 고-급 그래프 예제를 가져올 수 있다.
 - [R cheatsheets](https://www.rstudio.com/resources/cheatsheets/)