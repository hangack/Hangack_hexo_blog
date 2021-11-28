---
title: pythone 튜플
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
thumbnail: /thumbnails/CS/python.svg
date: 2021-11-01 16:17:35
---
## 튜플(tuple)
#### 튜플은 리스트와 달리 수정이 불가능하다.
#### 리스트는 []로 둘러싸지만 튜플은 ()로 둘러싼다.
#### 리스트는 값의 생성, 삭제, 수정이 가능하지만 튜플은 불가능하다.
#### 프로그램이 실행되는 동안 그 값이 항상 변하지 않기를 바를 때 사용한다.


```python
reset -f
```


```python
t1 = ()
t2 = (1,) # 요소가 1개일 경우 반드시 콤마(,)를 넣어야한다.
t3 = (1,2,3)
t4 = 1,2,3 # 괄호 생략 가능
t5 = ('a','b',('ab','cd')) # 튜플 내부에 튜플 삽입 가능. 단, 리스트는 변경 가능 변수이므로 삽입할 수 없다.
```


```python
whos
```

    Variable   Type     Data/Info
    -----------------------------
    t1         tuple    n=0
    t2         tuple    n=1
    t3         tuple    n=3
    t4         tuple    n=3
    t5         tuple    n=3
    


```python
# 인덱싱
t1 =(1,2,'a','b')
print(t1[0])
print(t1[3])
# 슬라이싱
print(t1[1:])
# 덧셈
t2 =(3,4)
print(t1+t2)
# 곱셈
print(t2*3)
```

    1
    b
    (2, 'a', 'b')
    (1, 2, 'a', 'b', 3, 4)
    (3, 4, 3, 4, 3, 4)
    

