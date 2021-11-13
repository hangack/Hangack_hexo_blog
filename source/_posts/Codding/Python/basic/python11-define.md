---
title: python 함수(define)
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
date: 2021-11-02 15:45:01
---
## 함수
반복적으로 사용되는 가치 있는 부분을 한 뭉치로 묶어 불필요한 반복을 줄일 수 있다.
'어떤 입력값을 주었을 때 어떤 결과값을 돌려준다.' 라는 식의 함수를 작성하는 것이 유리하다.


```python
# 파이썬 함수 구조
"""
def 함수 이름(매개변수들):
    수행할 문장1
    수행할 문장2
    ...

    return 결과값

"""
```




    '\ndef 함수 이름(매개변수들):\n    수행할 문장1\n    수행할 문장2\n    ...\n\n    return 결과값\n\n'




```python
# 함수

def add(a,b):         ## a 와 b는 add라는 함수를 작동시키기 위한 변수
    return a+b       ## 함수 이름은 ad고 입력으로 2개의 값을 받으며, 결과값은 2개의 입력값을 더한 값이다.



# 메인 프로그램

a=3
b=4
c=add(a,b)
print(c)

# Or

result=add(a=3,b=4)
print(result)

# Or

result=add(b=3,a=4)    ## 변수 이름만 맞추면 변수 순서가 바뀌어도 작동된다.
print(result)
```

    7
    7
    7
    


```python
# 입력값이 없는 함수

def say():
    return 'Hi'
```


```python
a=say()
print(a)
```

    Hi
    


```python
# retrun(결과값)이 없는 함수
def add(a,b):
    print("%d + %d = %d"%(a,b,a+b))
```


```python
add(3,4)
```

    3 + 4 = 7
    


```python
# 입력값이 몇 개가 될지 모를 때는?

# 여러 개의 입력값을 받는 함수

def add_many(*arg):       # '*' 는 임의의 여러 변수 지정
    result=0
    for i in arg:
        result=result+i   # *arg에 입력받는 모든 값을 더한다.
    return result
```


```python
result = add_many(1,2,3,4,5)
print(result)
```

    15
    


```python
# 사칙 연산 선택 가능

def add_mul(choice, *args) :
    if choice =='add':          ## choice 매개변수가 add 일 경우
        result = 0
        for i in args:
            result = result+i
    elif choice =='mul':    ## choice 매개변수가 mul 일 경우
        result = 1
        for i in args:
            result = result*i
    return result
```


```python
result = add_mul('add',1,2,3,4)
print(result)

result2 = add_mul('mul',1,2,3,4)
print(result2)
```

    10
    24
    


```python
# 함수의 결과값은 항상 하나  # 함수 결과값은 언제나 하나이기에 오류가 나는 것이 아니라 (7,12)라는 하나의 튜플 값으로 돌려준다.
def add_mul (a,b):
    return a+b,a*b

result = add_mul(3,4)
print(result)
```

    (7, 12)
    


```python
# 매개변수에 초기값 미리 정하기

def sayself(name,old,man=True):        ## 초기값 "Ture(or something)" 의 경우 변수 가장 끝에 지정하지 않으면 에러가 발생한다.
    print("이름 %s" %name)
    print("나이 %d" %old)
    if man:
        print("남성")
    else:
        print("여성")
```


```python
sayself("박응",27,True)
```

    이름 박응
    나이 27
    남성
    


```python
sayself("박선",27,False)
```

    이름 박선
    나이 27
    여성
    


```python
sayself("박응",27)           ## 초기값이 True로 설정되어있다.
```

    이름 박응
    나이 27
    남성
    

### 함수에서 매우 중요한 부분


```python
# 함수 안에서 선언한 변수의 효력 범위

a = 1                # 함수 밖의 변수 a
def vartest(a):     # 여기서 a는 함수 안에서 a라서 함수 안에서만 작동한다. 함수 밖과는 다른 셀이다.
    a=a+1
    
vartest(a)          # 여기서 입력값 a는 함수 바깥 a=1을 입력한다는 의미
print(a)            # 함수에서 a+1 = 2 가 되었지만 retrun도 없고 함수 안에서의 a만 a=2이 되었다. 메인 셀에서 a는 여전히 1이다.
```

    1
    


```python
# 함수 안에서 함수 밖의 변수를 변경하는 법

a = 1                
def vartest(a):     
    a=a+1
    return a            # 메인 프로그램 지정변수에 결과값을 돌려준다.
    
a = vartest(a)          # 결과값을 지정변수 a에 대입
print(a)            
```

    2
    


```python
# lambda (한줄 함수)
'lambda 매개변수1,매개변수2, ...: 매개변수를 사용한 표현식'

add = lambda a,b: a+b
result=add(3,4)
print(result)
```

    7
    


```python
#1 for문, while문, if문 등 제어문을 사용하여 1부터 100까지의 숫자를 출력
a=0
while a<100:
    a=a+1
    print(a,end=' ')
print()
    
for i in range(0,100):print(i+1,end=" ")
```

    1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 100 
    1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 100 


```python
#2 A학급에 총 10명의 학생이 있다. 이 학생들의 중간고사 점수는 다음과 같다.
#      [ 70, 60, 55, 75, 95, 90, 80, 80, 85, 100 ]
#  제어문(반복문)을 사용하여 A학급의 평균 점수를 구하라.

score = [ 70, 60, 55, 75, 95, 90, 80, 80, 85, 100 ]

score_sum = 0

for i in range(0,len(score)):
    score_sum = score_sum + score[i]
    i=i+1
    
score_avg = score_sum/len(score)

print(score_avg)
```

    79.0
    


```python
# 메모리 : 내부 입출력 장치 (Internal I/O) -> 전원과 동시에 소멸
# 하드 : 외부 입력 장치 (External I/O) -> 지속
#file (파일)
```

