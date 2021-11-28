---
title: python 자료형
categories: 
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
thumbnail: /thumbnails/CS/python.svg
date: 2021-11-01 16:07:15
---
## 파이썬의 자료형


```python
int_data = 3 #정수형 자료(integer data)
```

### float = 실수


```python
float_data = 3.14 #실수형 자료(floating point data)
```


```python
float_data2 = 3
```


```python
float_data2 = 3.
```

### string = 문자형


```python
complex_data = 1+5j
```


```python
str_data1 ='hello world'
```

### list [ ] 변경 가능 / tuple ( ) 변경 불가 / dict {}


```python
list_data = [1,2,3,4,5,6,7,8,9,10] #list data type
```


```python
tuple_data = (1,2,3,4,5,6,7,8,9,10) #tuple data type
```


```python
dict_data = {0:'toy',1:'book'} #dictionary data
```


```python
whos
```

    Variable       Type       Data/Info
    -----------------------------------
    complex_data   complex    (1+5j)
    dict_data      dict       n=2
    float_data     float      3.14
    float_data2    float      3.0
    int_data       int        3
    list_data      list       n=10
    str_data1      str        hello world
    tuple_data     tuple      n=10
    


```python
#정수형
a=123
a=-1123
a=0
#실수형
a=1.2
a=4.24E10   #4.12*10^10
a=4.24e10   #4.12*10^10
b=4.24e-10  #4.12*10^(-10)
```


```python
whos
```

    Variable       Type       Data/Info
    -----------------------------------
    a              float      42400000000.0
    b              float      4.24e-10
    complex_data   complex    (1+5j)
    dict_data      dict       n=2
    float_data     float      3.14
    float_data2    float      3.0
    int_data       int        3
    list_data      list       n=10
    str_data1      str        hello world
    tuple_data     tuple      n=10
    


```python
reset
```

    Once deleted, variables cannot be recovered. Proceed (y/[n])? y
    


```python
whos
```

    Interactive namespace is empty.
    


```python
a=3
b=4
print(a+b) #사칙연산 : +, -, *, /     
print(7%3) # 제곱(^) : **    # 나머지 : %
```

    7
    1
    

### 문자열


```python
a= "hello 'my' world"
b= 'hello "my" world' #동일한 따음표가 내부에 있으면 오류가 발생한다.
```


```python
whos
```

    Variable   Type    Data/Info
    ----------------------------
    a          str     hello 'my' world
    b          str     hello "my" world
    


```python
a= """
P
""
'O'
""
"""
print(a)
```

    
    P
    ""
    'O'
    ""
    
    


```python
a="my"
b="note"
c=a+"_"+b
print(c)
```

    my_note
    


```python
print((c+"/")*5)
```

    my_note/my_note/my_note/my_note/my_note/
    


```python
print(len(a)) # len = Lenth(길이)
```

    2
    

