---
title: python 입출력
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
date: 2021-11-02 15:48:13
---
## 입력
input: input 에 입력되는 모든 것을 문자열로 취급한다 (내부입력 : 메모리로부터 자료를 읽어옴)


```python

a = input()  # input 함수의 출력 타입 'str'

print(a)
print(type(a))

a = int(a)   # type : str -> int
print(a)
print(type(a))   
# 일단 str 타입으로 받아들인 후 type 전환을 통해 변수 가공
print(10+a)
```

    3
    3
    <class 'str'>
    3
    <class 'int'>
    13
    


```python
# 프롬프트 값을 띄워서 사용자 입력받기

number = input("숫자를 입력하세요 : ")
```

    숫자를 입력하세요 : 3
    


```python
print(number)
```

    3
    


```python
# split: value 나누기
a,b = input('숫자 두개를 입력하세요: ').split()
a = int(a)
b = int(b)

print(a+b)
```

    숫자 두개를 입력하세요: 5 7
    12
    


```python
# sep(separator): 변수 사이값(구분) 지정
print(1920,1000,sep=' * ')
```

    1920 * 1000
    


```python
# end: print 끝 값 임의로 지정(default: \n)
for i in range(2,5):
    for j in range(1,5):
        print(i*j,end='')       ## end = ''  이 문장에 끝은 \n이 아닌 '' 내부 문자로 대신한다.
    print()
```

    2468
    36912
    481216
    

## 출력
print : 입력 자료형을 출력 (내부출력)


```python
a = 123
print(a)

a = "Python"
print(a)

a = [1,2,3]
print(a)

a = "이번달은 %d 월 입니다." %11
print(a)

a = "오늘은 %d 월 %d 일 입니다." %(11,11)
print(a)

a = "시험 성적은 %3.1f점 입니다." %85.2345  ## 기말test :
print(a)

```

    123
    Python
    [1, 2, 3]
    이번달은 11 월 입니다.
    오늘은 11 월 11 일 입니다.
    시험 성적은 85.2점 입니다.
    


```python
print("Life" + "is" + "too stort")
print("Life" "is" "too stort")       # 큰 따옴표 문자열 연산은 + 와 동일
print("Life " "is " "too stort")
print("Life", "is", "too stort")     # 문자열 띄어쓰기는 콤마(,)로 가능
```

    Lifeistoo stort
    Lifeistoo stort
    Life is too stort
    Life is too stort
    


```python
# 한 줄에 결과값 출력하기

for i in range(10) :
    print(i, end=' ')
```

    0 1 2 3 4 5 6 7 8 9 

