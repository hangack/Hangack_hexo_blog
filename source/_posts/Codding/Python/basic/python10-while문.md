---
title: python while문
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
date: 2021-11-01 16:29:16
---
## While 문 (조건과 반복의 콤비네이션)
조건이 참인 동안에 while 문 아래의 문장이 반복 수행된다.


```python
# while 문의 기본 구조

"""

while <조건문>:
    <수행 문장1>
    <수행 문장2>
    <수행 문장3>
    ...


"""

treehit = 0

while treehit <10:                 ## 조건이 ture 일 경우에 실행된다. -> fulse일 경우 중단
    treehit = treehit + 1
    print("나무를 %d번 찍었습니다" %treehit)
    if treehit == 10: print("나무가 넘어갑니다")
```

    나무를 1번 찍었습니다
    나무를 2번 찍었습니다
    나무를 3번 찍었습니다
    나무를 4번 찍었습니다
    나무를 5번 찍었습니다
    나무를 6번 찍었습니다
    나무를 7번 찍었습니다
    나무를 8번 찍었습니다
    나무를 9번 찍었습니다
    나무를 10번 찍었습니다
    나무가 넘어갑니다
    


```python
prompt = """
    1. Add
    2. Del
    3. List
    4. Quit
    
    Enter number:"""

```


```python

num = 0
while num != 4:
    print(prompt)
    num = int(input())
```

    
        1. Add
        2. Del
        3. List
        4. Quit
        
        Enter number:
    1
    
        1. Add
        2. Del
        3. List
        4. Quit
        
        Enter number:
    1
    
        1. Add
        2. Del
        3. List
        4. Quit
        
        Enter number:
    3
    
        1. Add
        2. Del
        3. List
        4. Quit
        
        Enter number:
    2
    
        1. Add
        2. Del
        3. List
        4. Quit
        
        Enter number:
    4
    

quit 의미의 4를 입력하지 않으면 계속 prompt를 출력하는 형식
여기서 input()은 사용자의 입력을 받는 함수


```python
# while 문 :커피머신

coffee = 3

while True:       ## while 문 무한반복 문구
    money = int(input())
    if money >= 300 and coffee != 0: ##커피를 뽑기에 충분한 돈인지 판단
        coffee = coffee - 1
        if money > 300:
            print("커피")
            print("거스름돈 %d원" %(money - 300))
        else : print("커피")
    elif money < 300 :
        print("잔액부족")
    elif coffee == 0 :
        print("재고부족")
        break     ##if 특정조건이면 while을 빠져나가자 (break) <-> continue
```

    1000
    커피
    거스름돈 700원
    10
    잔액부족
    300
    커피
    301
    커피
    거스름돈 1원
    500
    재고부족
    


```python
# 홀수만 출력하는 while 문
a=0
while a<10:
    a=a+1
    if a%2==0:continue
    print(a)
print("")

x= list(range(1,10,2))
print(list(range(5)))
for i in range(5):
    print(x[i])
print("")

a=1
while True:
    print(a)
    a=a+2
    if a> 10:
        break
```

    1
    3
    5
    7
    9
    
    [0, 1, 2, 3, 4]
    1
    3
    5
    7
    9
    
    1
    3
    5
    7
    9
    
