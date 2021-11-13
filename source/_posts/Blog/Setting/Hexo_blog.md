---
title: github 블로그 만들기(Hexo)
categories: 
  - 블로그
  - 설정
tags: 
  - 블로그
  - 설정
  - hexo
date: 2021-11-01 12:24:46
---
## Hexo 설치
### Node.js 설치
터미널로 hexo 언어를 설치하기 위해 툴을 받아올 nodejs를 설치한다.
이 때, 버그 활발히 픽스가 진행중인 신버전보다 구버전 넘버를 권장한다.

Node.js: https://nodejs.org/en/


node를 설치할 때 path 설정(시스템 환경 변수)은 필수로 체크하며, 프로그램의 각종 오류를 c/c++로 해결하는 패치를 배포하기 때문에 chocolatey; c/c++ 환경 변수 설정도 체크하는걸 권장한다.
(chocolatey 설정이 좀 오래 걸리더라)

node가 정상적으로 동작하는걸 확인하기 위해 다음 명령를 터미널에 입력해 설치된 node.js의 버전을 확인할 수 있다.
```
$ node -v
```

###
각종 노드 명령어 확인은 다음 명령어로 확인할 수 있다.
```
$ npm
```
###
노드의 동작을 확인했으면 node.js 명령어를 이용해 원래 목적이었던 Hexo 언어를 설치한다
```
$ npm install -g hexo-cli
```
hexo 툴을 이용해 블로그 관리 툴을 불러와서 임의의 디렉토리명으로 저장한다.
```
$ hexo init 디렉토리명(myblog)
```
(hexo툴로 불러온 디렉토리명은 myblog로 통일해서 부르겠다)

myblog 디렉토리로 진입하거나 Pycharm 등의 편집 프로그램을 통해 진입한 뒤 git bash에 다음 명령어를 입력한다.
```
$ npm install
$ npm install hexo-server --save
$ npm install hexo-deployer-git --save
```
서버 생성과 배포를 위한 툴이 설치되었으니 서버 작동의 확인을 위해
```
$ hexo server
```
를 입력한 뒤 나오는 http 로컬 주소로 진입한다.
myblog를 github에 백업하려면 myblog repository를 생성하여 백업을 진행한다.

### Hexo 블로그 배포하기
로컬 주소가 정상 작동되는게 확인됐으면 블로그를 온라인으로 배포해야하는데, 이 역할을 github에 특정 repository를 생성하여 진행한다.
repository 명은 [**유저아이디.github.io**]으로 생성한다.

github.io repository를 만들었으면 해당 repository에 블로그 형식을 저장하고 배포 주소를 설정해야한다.
_config.yml 파일에 진입해서 URL 정보와 깃허브 연동 주소를 설정한다.
```
#URL
url: https://유저아이디.github.io
```
```
# Deployment
deploy:
  type: git
  repo: https://github.com/유저아이디/유저아이디.github.io.git
  branch: main
```
변경된 항목대로 서버를 생성하기 위해
```
$ hexo generate
```
를 입력하고
```
$ hexo server
```
로 정상 적용되었는지 로컬에서 확인한다.
정상적으로 적용되었다면 사이트 배포를 위해
```
$ hexo deploy
```
명령어를 사용해 사이트를 배포한다.
사이트 주소는 위 #URL에서 입력한 [**https://유저아이디.github.io**]와 동일하다.

#


메모:
- https://github.com/hangack/Codding-base/blob/main/Blog_Hexo/20211028.md?plain=1