---
title: Jupyter 경로 변경
categories:
  - 연습
  - 파이썬
  - 설정
tags:
  - 파이썬
  - 쥬피터
  - 설정
date: 2021-11-07 10:41:52
---
  
주피터 노트북 혹은 주피터 랩의 기본 경로가 Users에 적용되어있고 간단한 설정으로 경로를 바꿀 수 없기에 메모를 남긴다.

주피터 설정을 변경하기 위해서는 구성을 변경할 수 있는 파일인 config 파일이 필요하다.
하지만 이 congif 파일은 기본적으로 설치되어있지 않기에 아래와 같이 cmd 창에서 jupyter 명령어로 세팅 방식이 적힌 config 파일을 생성해주는걸 권장한다.
```shell
> jupyter notebook --generate-config
```
<img src="/images/2111/주피터 경로 변경/J1.png" alt="config 생성">

그러면 user 경로 .jupyter 디렉토리에 jupyter_notebook_config.py 파일이 생성된다.

<img src="/images/2111/주피터 경로 변경/J2.png" alt="jupyter_notebook_config.py">

버전마다 다르지만 에디터를 이용해 385번줄에 있는
```python
# c.NotebookApp.notebook_dir = ''
```
<img src="/images/2111/주피터 경로 변경/J3.png" alt="c.NotebookApp.notebook_dir">

의 주석 처리를 제거하고 원하는 경로를 입력한다.

이 때, 경로는 리눅스 방식으로 변경해야되니 역슬래쉬(\\)로 경로가 복사되었다면 슬래쉬(/)로 변경하거나 컴퓨터에게 특수문자임을 인식시키기 위해 역슬래쉬를 2번(\\\\) 입력한다.
```python
c.NotebookApp.notebook_dir = 'E:/Fear/Univ/Big_data/Training/Github/Codding-base/Python/Python-jupyter'
```
혹은
```python
c.NotebookApp.notebook_dir = 'E:\\Fear\\Univ\\Big_data\\Training\\Github\\Codding-base\\Python\\Python-jupyter'
```
<img src="/images/2111/주피터 경로 변경/J4.png" alt="경로 입력">

이걸로 주피터 path 경로는 변경되었으나 Jupyter Notebook의 바로가기 path도 설정해야 notebook을 열었을 때 config에서 설정한 path 경로를 참조할 수 있다.
<img src="/images/2111/주피터 경로 변경/J5.png" alt="Jupyter Notebook 경로">


notebook 설정을 열어서 아래 두 경로를 지워 config 설정을 참조하도록 바꿔준다.
```
대상: ~ "%USERPROFILE%/"
시작위치: %HOMEPATH%
```
<img src="/images/2111/주피터 경로 변경/J6.png" alt="path 변경">

지정한 경로에서 잘 열리지만 path 내부에서만 작업하므로 작업환경에서 가장 편한 path를 설정하는걸 권장한다.



### 외부링크
 - [주피터 노트북 환경설정 : 시작폴더 변경방법](https://ooyoung.tistory.com/7)