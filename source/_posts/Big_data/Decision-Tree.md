---
title: 의사결정트리(Decision Tree)에 대한 간단 설명
categories:
  - 빅데이터
tags:
  - 빅데이터
  - 정의
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
date: 2021-11-04 14:58:39
---

## 간단 설명
의사결정트리는 여러 객체가 모인 집단에서 절차적 "Yes"||"No" 혹은 간단한 문답문을 이용해 원하는 특성을 가진 객체를 분류해내는 과정이다.

주변에서 한가지 예시를 살펴본다면 법률로 경차를 정의해서 고속도로 / 보험 등 각종 형식으로 혜택을 주는 경우가 있다.
돈과 관련된 문제인 만큼 경차를 분류하는 기준은 필수가 된다.

한국에서의 경차를 보자면
- 배기량 1,000cc 이하
- 길이 3.6m 이하
- 너비 1.6m 이하
- 높이 2.0m 이하

인 자동차로 정의한다.

## 그러면 의사결정트리는 어떻게 만들어질까?
우선 나라마다 정의한 경차에 대한 포멧이 다르기 때문에 간단한 문답문을 이용해 어느 나라의 포멧을 불러올지 결정한다.

<img src="/images/2111/Dicision Tree Basic/car0.png" alt="국가포멧">

다음으로 배기량이나 차량의 크기같은 포멧이 만족하는지 하나씩 Y/N 문답을 절차적으로 진행한다. 효율성에 관해선 다음에 설명하고 이번 포스팅에선 배기량부터 순차적으로 진행한다.

<img src="/images/2111/Dicision Tree Basic/car1.png" alt="배기량">
<img src="/images/2111/Dicision Tree Basic/car4.png" alt="높이">

위와 같은 의사결정트리(Decision Tree) 과정을 통해 한국의 법률에서 경차로 정의되는 차량을 나눌 수 있다.
객체의 종류가 적다면 큰 문제는 없겠지만, 차량 객체 각각에 대한 데이터를 가지고 있고 법률적인 포멧이 있다면 수 많은 차량에 대한 포멧을 컴퓨터 작업을 통해 간단히 나눌 수 있을 것이다.


## 추가정보
- [Matlab utube](https://youtu.be/IFGP0mqdL5w)
- [Minsuk Heo 허민석 utube](https://youtu.be/n0p0120Gxqk)
  - [엔트로피](https://youtu.be/UPKugq0fK04)
- [심화 및 수식 설명](https://bkshin.tistory.com/entry/%EB%A8%B8%EC%8B%A0%EB%9F%AC%EB%8B%9D-4-%EA%B2%B0%EC%A0%95-%ED%8A%B8%EB%A6%ACDecision-Tree)