---
title: python 비교연산자
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
thumbnail: /thumbnails/CS/python.svg
date: 2021-11-01 16:26:37
---
## 비교 연산자

        <   작다
        >   크다
        ==  같다
        !=  같지 않다
        >=  크거나 같다
        <=  작거나 같다
비교 연산 결과는 반드시 bool(참 or 거짓)이 되야한다.
        
        x or y     둘 중 하나만 참이면 된다.
        x and y    둘 모두 참일 경우
        not x      x가 거짓이면 참이다


```python
# ex
1>3 and 2<4  ## false and ture
```




    False




```python
True and False or True or False and True   ## 연산은 왼쪽부터 수행한다.
```




    True




```python
not False
```




    True




```python
not False or not True
```




    True




```python
1 or 0 or -1       ## 0 : 거짓(0) , 0 이외 : 참(1 혹은 다른 수)
```




    1




```python
bool(5)         ## bool 값으로 변경
```




    True



### x in s , x not in s

x in list,튜플,문자열 / x not in list,튜플,문자열
: list,튜플,문자열 안에 x가 있는가?


```python
1 in [1,2,3]      ## 존재하면 ture 하지 않으면 false
```




    True




```python
'a' not in ['a','b']
```




    False




```python
't' in 'pythone'    ## 문자열 같은 경우 해당 문자가 존재하는가로 결정
```




    True




```python
pocket = ['phone','money','card']

if ('money' in pocket) or ('card' in pocket):        ## 괄호 설정으로 확실히하기
    print("택시")
else:
    print("보도")
```

    택시
    


```python
pocket = ['phone','money','card']

if not ('money' in pocket) or not ('card' in pocket):
    print("보도")
else:
    print("택시")
```

    택시
    


```python
# elif (else if)   elif 문 사용 수에 제한은 없다.

pocket = ['phone','card']

if 'money' in pocket: print("택시 by money")    ## 수행문이 1줄일 경우 줄이기 가능
elif 'card' in pocket: print("택시 by card")
else: print("보도")
```

    택시 by card
    

