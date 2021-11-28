---
title: markdown 수식 넣기
categories:
  - 연습
  - 마크다운
tags:
  - 마크다운
  - 수식
  - mathjax
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
thumbnail: /thumbnails/CS/mathjax.png
date: 2021-11-15 06:23:55
---

## mathjax

Markdown에서는 $x^2$처럼 수식을 사용할 수 있는 mathjax 플러그인이 내장되어있다.

### 블럭 지정

수식을 사용하기 위해 아래와 같이 식 앞 뒤로 $문자를 넣어줘야한다.
```markdown
$math$
```
$math$

아래 처럼 $ 문자를 2개 넣는 경우도 있는데,
```markdown
$$math$$
```
$$math$$
이 경우엔 text 사이에 수식을 삽입하는게 아닌 따로 표현하는 경우에 주로 사용된다.

### 첨자

수학에서 행의 i번째 속성을 가리키거나 x의 n 제곱을 표현할 때 첨자를 주로 사용한다.

```markdown
$x_i^n$
```
$x_i^n$
 - 아래첨자: `_`
 - 위첨자: `^`

### 중괄호

x의 12제곱을 표현하기 위해 단순히 `$x^12$`만 입력하게 된다면

$x^12$처럼 문자 1개만 위첨자로 처리된다.
이를 해결해주는 문법이 중괄호( `{ }` )다.

```markdown
$x^{12}$
```
$x^{12}$

단, 중괄호를 mathjax에서 하나의 문자열로 처리하기 위해 사용되므로 중괄호를 사용하는 식에서는 escape(\\)로 문법 인식이 아닌 문자 인식으로 바꿔줘야한다.

```markdown
$x_5 = [[\{(x_1)+x_2\}+x_3]+x_4]$
```

※ `Hexo`: 중괄호를 표현하기 위해선 `\`를 중첩 사용한다.
[hexo 수식 사용하기](https://hangack.github.io/2021/11/12/Blog/Setting/Hexo-blog-mathjax/)
```markdown
$x_5 = [[\\{(x_1)+x_2\\}+x_3]+x_4]$
```
$x_5 = [[\\{(x_1)+x_2\\}+x_3]+x_4]$


### 행렬 형식

#### 2속성만 넣을 경우
```markdown
$$v{x \choose 0}$$
```
$$v{x \choose 0}$$

#### 기본 형식 array행렬 & 괄호 크기 변경
```markdown
$$
X\Bigg\{
\begin{array}{c}
    x_{1}\\
    x_{2}
\end{array}
$$
```
$$
X\Bigg\{
\begin{array}{c}
    x_{1}\\
    x_{2}
\end{array}
$$

#### P-matrix
```markdown
$$
L=
\begin{pmatrix}
    b_1   & b_2  & b_3  & \cdots & b_{n-1}& b_n\\
    s_1   & 0    & 0    & \cdots & 0      & 0\\
    0     & s_2  & 0    & \cdots & 0      & 0\\
    0     & 0    & s_3  & \cdots & 0      & 0\\
    \vdots&\vdots&\vdots& \ddots & \vdots &\vdots\\
    0     & 0    & 0    & \cdots & s_{n-1}& 0\\
\end{pmatrix}
$$
```
$$
L=
\begin{pmatrix}
    b_1   & b_2  & b_3  & \cdots & b_{n-1}& b_n\\
    s_1   & 0    & 0    & \cdots & 0      & 0\\
    0     & s_2  & 0    & \cdots & 0      & 0\\
    0     & 0    & s_3  & \cdots & 0      & 0\\
    \vdots&\vdots&\vdots& \ddots & \vdots &\vdots\\
    0     & 0    & 0    & \cdots & s_{n-1}& 0\\
\end{pmatrix}
$$

#### B-matrix
```markdown
\begin{bmatrix}
    2 & 1 &-1\\
    1 & 0 & 5\\
   -1 & 3 &-2
\end{bmatrix}
```
$$
\begin{bmatrix}
    2 & 1 &-1\\
    1 & 0 & 5\\
   -1 & 3 &-2
\end{bmatrix}
$$

#### 행렬에 세로 줄 넣기
```markdown
$$
\left[
\begin{array}{ccc|c}
    2 & 1 &-1 & 3\\
    1 & 0 & 5 & 1\\
   -1 & 3 &-2 & 0
\end{array}
\right]
$$
```

$$
\left[ 
\begin{array}{ccc|c}
    2 & 1 &-1 & 3\\
    1 & 0 & 5 & 1\\
   -1 & 3 &-2 & 0
\end{array}
\right]
$$


#### V-matrix
```markdown
$$
\begin{vmatrix}
    a & b\\
    c & d
\end{vmatrix}
=ad-bc
$$
```
$$
\begin{vmatrix}
    a & b\\
    c & d
\end{vmatrix}
=ad-bc
$$

#### 연립 방정식
```markdown
$$
\begin{cases}
    v_1 = 3i+2k\\
    v_2 = 2j+k\\
    v_3 = i+j+k
\end{cases}
$$
```
$$
\begin{cases}
    v_1 = 3i+2k\\
    v_2 = 2j+k\\
    v_3 = i+j+k
\end{cases}
$$


### 특수문자

수식에서 사용되는 곱셈 나눗셈부터 pi ohm과 같은 특수문자를 삽입하기 위해선 중괄호 경우처럼 `\`를 사용해야한다.

```markdown
$$
(\hat i\cdot\hat i)\div n \\
= \frac{\vert\hat i\vert\times\vert\hat i\vert cos\theta}{n}\\
= \frac{\vert\hat i\vert^2\times 1}{n} = \frac 1n
$$
```

$$
(\hat i\cdot\hat i)\div n \\
= \frac{\vert\hat i\vert\times\vert\hat i\vert cos\theta}{n}\\
= \frac{\vert\hat i\vert^2\times 1}{n} = \frac 1n
$$

특수문자는 굉장히 다양하므로 삽입하고자 하는 문자를 LaTex(혹은 Mathjax) 검색어에 붙여 검색하자.