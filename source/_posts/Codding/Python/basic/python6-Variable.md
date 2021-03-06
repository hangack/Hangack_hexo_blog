---
title: python 변수
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
thumbnail: /thumbnails/CS/python.svg
date: 2021-11-01 16:22:01
---
## 변수(Variable), 객체(Object), 자료(Data), 자료형(Data type)
자료는 우리가 컴퓨터 메모리에 입력할 컴퓨터 외부에 존재하는 수, 문자 등을 의미
자료를 컴퓨터에 입력하기 위해서 일정한 규칙이 필요하고 그 규칙은 자료형으로 규정된다.
컴퓨터 외부에 존재하는 자료를 컴퓨터 머리에 입력하는 독특한 방식은 '=' 기호를 쓰고 주로 '변수 = 자료' 형태를 취한다
일단 컴퓨터 메모리에 자료를 입력하면 그 자료는 '자료'라 부르지 않고 파이썬에선 '객체(Object)'라 칭한다.
변수란 컴퓨터 메모리 어딘가에 존재하는 객체가 어디에 있는지를 알려주는 주소 개념이다.
타 프로그래밍 언어인 C나 Java에선 자료형(Data type)이 무엇인지 친절히 알려줘야한다.
반면, 파이썬은 자료를 스스로 살펴보고 자료형이 무엇인지 판단한다. 따라사 그 과정이 필요 없다.
변수를 만들 때는 반드시 '='(assignment) 기호를 사용한다.
예 : a = [1,2,3] 이면, [1,2,3] 값을 가지는 리스트 자료형(객체)은 메모리에 자동생성되고 변수 a는 리스트가 저장된 메모리 주소를 가리킨다.


```python
a = [1,2,3]
id(a)            # id() : 변수가 가리키고 있는 객체의 주고 값을 돌려주는 함수
```




    2456107858688




```python
# 여러 변수 한번에 만들기
a, b  = 1, 2
print(a)
print(b)
```

    1
    2
    


```python
# null 변수 만들기
a = None
print(a)
type(a)
```

    None
    




    NoneType




```python
# 변수에 변수를 할당할 경우
b = a              ## 주소값 공유
print(a)
print(b)
print(id(a))
print(id(b))
```

    None
    None
    140715255699584
    140715255699584
    


```python
# a와 b가 가리키는 객체가 동일한지 묻는 방법 (is)
a is b
```




    True




```python
# * 주의 *
a[1] = 4
print(a)
print(b)
## 주소값 공유란, 자료를 복사하는 것이 아니라 메모리 주소를 서로 공유한다는 것.
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-72-a5aa4d30ec01> in <module>
          1 # * 주의 *
    ----> 2 a[1] = 4
          3 print(a)
          4 print(b)
          5 ## 주소값 공유란, 자료를 복사하는 것이 아니라 메모리 주소를 서로 공유한다는 것.
    

    TypeError: 'NoneType' object does not support item assignment



```python
# [:] 사용

a = [1,2,3]
b = a[:]
a[1] = 4
print(a)
print(b)
## [:]는 리스트 전체를 가리키는 방법이기에 자료를 복사하는 경우다.
a is b
```

    [1, 4, 3]
    [1, 2, 3]
    




    False




```python
#1 자연수 a 홀수 짝수 판별
a = 13
b = a%2
print(b)       # print 값이 0일 경우 짝수, 1일 경우 홀수
```

    1
    


```python
#2 주민등록번호 13자리를 생년월일(YYMMDD)과 그 외 숫자로 분류
a = "0101011234567"
print(a[:6],"-",a[6:])    ## a[:6] : 0 =< print < 6  , a[6:] : 6 =< print 
```

    010101 - 1234567
    


```python
#3 [1,3,5,4,2] 리스트를 [5,4,3,2,1]로 변경 ## 오름차순 내림차순
a = [1,3,5,4,2]
a.sort()
a.reverse()
print(a)
```

    [5, 4, 3, 2, 1]
    

