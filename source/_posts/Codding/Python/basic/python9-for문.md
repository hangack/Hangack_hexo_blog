---
title: python for문
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
date: 2021-11-01 16:28:31
---
## FOR 문 (반복문)


```python
# for

test_list = ['one','two','three']

for i in test_list:
    print(i)
```

    one
    two
    three
    


```python
x = [1,'2',3]
for i in x:
    print(i,type(i))
```

    1 <class 'int'>
    2 <class 'str'>
    3 <class 'int'>
    


```python
a = [(1,2),(3,4),(5,6)]

for (first, last) in a:
    print(first,last)
```

    1 2
    3 4
    5 6
    


```python
a = [(1,2),(3,4),(5,6)]

for i in a:
    print(i)
    print(i[0]+i[1])        ## a : 튜플 [ ]
```

    (1, 2)
    3
    (3, 4)
    7
    (5, 6)
    11
    

### formatted print %a

%d : 정수 , %f : 실수 , %s : 문자
    
%#d : # 만큼의 칸을 변수에 할당한다.
%#.?f  : # 만큼의 칸을 할당하고 ?만큼의 소수점 이하 자리를 표현한다. '.'도 #의 칸 수에 해당한다.


```python
# 응용

# '총 5명의 학생이 시험을 보았는대 60점이 넘으면 합격 아니면 불합격'

marks =[90,25,97,45,80]

number = 0
for mark in marks:
    number = number + 1    ## x = x + 1
    if mark >= 60:
        print("%4d번 학생은 합격입니다." % number)           ## 문자열 외부에 % (변수) 지정
    else:
        print("%d번 학생은 불합격입니다." % number)
```

       1번 학생은 합격입니다.
    2번 학생은 불합격입니다.
       3번 학생은 합격입니다.
    4번 학생은 불합격입니다.
       5번 학생은 합격입니다.
    


```python
# range(시작 수, 끝 수) 함수. 단 끝 수는 해당하지 않는다. (시작 수 =< range < 끝 수)
# 시작 수 생략 가능 ex) range(6) == (0,1,2,3,4,5)

add = 0
for i in range(1,11):
    add = add + i
    
print(add)
```

    55
    


```python
marks = [90,25,67,45,80]
for mark in marks:
    if mark >= 60:
        print("%d번 학생 합격" %(marks.index(mark)+1))       ## '+1' index의 경우 0번부터 시작하기 때문에
```

    1번 학생 합격
    3번 학생 합격
    5번 학생 합격
    


```python
marks = [90,25,67,45,80]
for number in range(len(marks)):    ## for number in range(5) -> (0,1,2,3,4)
    if marks[number] < 60:
        continue                   ## 아무 작업을 하지 않고 'for'문으로 돌아간다.
    print("%d번 학생 합격" %(number+1))
```

    1번 학생 합격
    3번 학생 합격
    5번 학생 합격
    


```python
# 2중 루프

for i in range(2,5):
    for j in range(1,5):
        print(i*j)
    print('')
```

    2
    4
    6
    8
    
    3
    6
    9
    12
    
    4
    8
    12
    16
    
    


```python
# 2중 루프

for i in range(2,5):
    for j in range(1,5):
        print(i*j,end=' ')       ## end = ''  이 문장에 끝은 \n이 아닌 '' 내부 문자로 대신한다.
    print('')
```

    2 4 6 8 
    3 6 9 12 
    4 8 12 16 
    


```python
#for 구문  ## range(#1,#2,#3) 를 이용한 리스트 만들기  #1 : 시작값 / #2 : 종료값 / #3 : 간격

result = [x*y for x in range(2,10)
          for y in range(1,10)]

print(result)



range(1,30,2)
print(type(range(1,30,2)))
print(list(range(1,30,2)))    ### range 는 list 와 비슷한 형식이다.

```

    [2, 4, 6, 8, 10, 12, 14, 16, 18, 3, 6, 9, 12, 15, 18, 21, 24, 27, 4, 8, 12, 16, 20, 24, 28, 32, 36, 5, 10, 15, 20, 25, 30, 35, 40, 45, 6, 12, 18, 24, 30, 36, 42, 48, 54, 7, 14, 21, 28, 35, 42, 49, 56, 63, 8, 16, 24, 32, 40, 48, 56, 64, 72, 9, 18, 27, 36, 45, 54, 63, 72, 81]
    <class 'range'>
    [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25, 27, 29]
    

