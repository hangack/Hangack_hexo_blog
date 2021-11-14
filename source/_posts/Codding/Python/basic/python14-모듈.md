---
title: python 모듈
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
date: 2021-11-02 15:55:05
---
## 모듈
함수나 변수를 모아 놓은 파이썬 파일 (파일명(.py) = 모듈명
다른 파이썬 프로그램에서 불러와 사용할 수 있게끔 나든 파이썬 파일
여러 모듈을 묶어서 편리하게 관리하기 위해 패키지(디렉토리) 안에 넣어둘 수 있다.
패키지 내부 모듈 안의 특정 함수를 사용하기 위해서는 '패키지.모듈명.특정함수명' 형태로 사용한다.
불러들이는 명령어 : import


아래의 [matplotlib](https://matplotlib.org/stable/users/installing.html)는 외부 모듈로 cmd 창을 통해 따로 다운받아야한다.

```python
import matplotlib.pyplot as plt   # matplotlib (패키지)  pyplot (모듈)      # A as B  -> 변수 A를 B로 설정
#여기서 plt는 object 이다.   /    object(객체)는 .을 찍을 수 있다.

plt.plot([1,2,3,4])
```




    [<matplotlib.lines.Line2D at 0x23bdd9b5880>]




    
![그래프 예시](/images/2111/Python0/python14.png)
    




```python
# import '모듈 이름' : 모듈 불러오는 명령어

import math            # math 는 객체  - . 을 찍을 수 있다.
# 수학 작업을 할 때 :  math library(파이썬 내장) 혹은 numpy library(외부 다운로드)
n = math.factorial(5)
print(n)
```

    120
    


```python
%%writefile my_module.py
my_variable = 10
def my_factorial(n) :
    x=1
    for i in range(1,n+1):
        x=x*i
    return(x)
```

    Overwriting my_module.py
    


```python
import my_module as math_lib        ## 원하는 이름으로 변경
print(math_lib.my_variable)
```

    10
    


```python
# from '모듈 이름' import '함수 이름' : factorial 함수만 import

from math import factorial             ## math.factorial -> factorial
n = factorial(5)/factorial(3)
print(n)
```

    20.0
    


```python
# 여러 함수를 import

from math import (factorial, acos, pi, sin)
n = factorial(3) + acos(1)
print(n)


# 모든 함수를 import, * : 모든 것

from math import *
n = sqrt(5) + fabs(-12.5)   ## sqrt : 루트 / fabs : 절대값
print(n)
```

    6.0
    14.73606797749979
    

### 모듈 만들기


```python
%%writefile mod1.py

def add(x,y):
    return x+y

def sub(x,y):
    return x-y
```

    Overwriting mod1.py
    


```python
import mod1
i = mod1.add(3,4)
print(i)
```

    7
    


```python
from mod1 import *
i = add(3,4)
print(i)
```

    7
    


```python
i = mod1.sub(4,2)
print(i)
```

    2
    


```python
%%writefile mod2.py

PI = 3.141592

def add(x,y):
    return x+y

# 모듈에 변수 포함 가능
```

    Overwriting mod2.py
    


```python
import mod2
print(mod2.PI)
```

    3.141592
    

