---
title: python 불
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
date: 2021-11-01 16:21:23
---
## 불 자료형 (bool)
#### 참(Ture), 거짓(False) 2가지 값만 가진다.


```python
# 따옴표로 감싸지 않아도 변수 지정이 된다.
a = True #참
b = False #거짓
```


```python
type(a)
```




    bool




```python
type(b)
```




    bool




```python
a = 1 == 1  # '=' : 할당 , '==' : equal , '!=' : 같지 않다.
print(a)
```

    True
    

### 자료형의 참과 거짓
#### 문자형이나 리스트, 튜플 등은 비어 있으면 거짓(False)가 되고, 비어 있지 않으면 참(True)이 된다. 숫자에서는 그 값이 0이 될 때 거짓이 된다.

#### [문자열] 
    "python" = Ture
    "" = False
#### [리스트]
    [1,2,3] = Ture
    [] = False

#### [튜플]
    (1,2,3) = Ture 
    () = False

#### [딕셔너리] 
    {1,2,3} = Ture 
    {} = False

#### [숫자형] 
    0이 아닌 수 = Ture 
    0 = False



```python
# bool 자료형 활용 예시
# while 조건문:
#  수행할 문장

a=[1,2,3,4]
while a:                  # a가 참이 동안
    print(a.pop())              # 리스트 마지막 요소를 하나씩 꺼낸다
```

    4
    3
    2
    1
    


```python
# 예시 2

if []:                  #만약 [ ] 가 참이면,
    print("Ture")             # '참' 문자열 출력
else:                   # 만약 [ ] 가 거짓이면,
    print("False")            # '거짓' 문자열 출력
    
if [1,2,3]:      
    print("Ture") 
else:                
    print("False")  
```

    False
    Ture
    

