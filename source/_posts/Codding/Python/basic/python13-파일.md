---
title: python 파일
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
date: 2021-11-02 15:49:29
---
## 파일 생성
### 파일 객체 = open(파일 이름, *파일 열기 모드)
#### [파일 열기 모드]
r : 읽기 모드
w : 쓰기 모드
a : 추가 모드 (파일의 마지막에 새로운 내용을 추가할 때 사용)  , append


```python
# open 명령어 : 파일에 작업을 한다.

f = open("새파일.txt", 'w')     # w 모드로 파일을 열면 기존 파일의 내용을 전부 지우고 처음부터 작업한다. 추가 입력은 a
f.close     # 작업 이후 반드시 close로 파일과 연결을 끊어줘야 함
```




    <function TextIOWrapper.close()>




```python
# 파일 쓰기 모드로 출력값 입력

f = open("새파일.txt", 'w')
for i in range(1,11): # 1부터 10까지 i에 대입
    data = "%d번째 줄입니다. \n" %i       #formatted str         # \n은 줄바꿈 기호
    f.write(data)      # data를 파일 객체 f에 입력
f.close()
```

### 프로그램 외부에 저장된 파일을 읽는 방법


```python
# readline 함수

f = open("새파일.txt", 'r')
line = f.readline()   # 파일의 첫 줄을 읽는다.
print(line)
f.close()
```

    1번째 줄입니다. 
    
    


```python
f = open("새파일.txt", 'r')
while True:
    line = f.readline()
    if not line: break         # line(str) 인 경우 공백이면 fulse , 글자인 경우 true
    print(line)
f.close()
```

    1번째 줄입니다. 
    
    2번째 줄입니다. 
    
    3번째 줄입니다. 
    
    4번째 줄입니다. 
    
    5번째 줄입니다. 
    
    6번째 줄입니다. 
    
    7번째 줄입니다. 
    
    8번째 줄입니다. 
    
    9번째 줄입니다. 
    
    10번째 줄입니다. 
    
    


```python
f = open("새파일.txt", 'r')
lines = f.readlines()
f.close()
print(lines)
for i in range(1,11):
    print(lines[i-1])
```

    ['1번째 줄입니다. \n', '2번째 줄입니다. \n', '3번째 줄입니다. \n', '4번째 줄입니다. \n', '5번째 줄입니다. \n', '6번째 줄입니다. \n', '7번째 줄입니다. \n', '8번째 줄입니다. \n', '9번째 줄입니다. \n', '10번째 줄입니다. \n']
    1번째 줄입니다. 
    
    2번째 줄입니다. 
    
    3번째 줄입니다. 
    
    4번째 줄입니다. 
    
    5번째 줄입니다. 
    
    6번째 줄입니다. 
    
    7번째 줄입니다. 
    
    8번째 줄입니다. 
    
    9번째 줄입니다. 
    
    10번째 줄입니다. 
    
    


```python
# read 함수 사용하기
f = open("새파일.txt", 'r')
data = f.read()
print(data)
print(type(data))
f.close()
```

    1번째 줄입니다. 
    2번째 줄입니다. 
    3번째 줄입니다. 
    4번째 줄입니다. 
    5번째 줄입니다. 
    6번째 줄입니다. 
    7번째 줄입니다. 
    8번째 줄입니다. 
    9번째 줄입니다. 
    10번째 줄입니다. 
    
    <class 'str'>
    

### 파일에 새로운 내용 추가하기


```python
f = open("새파일.txt", 'a')
for i in range(11,20): 
    data = "%d번째 줄입니다. \n" %i     
    f.write(data)   
f.close()
```

### write문과 함께 사용하기


```python
f = open("foo.txt",'w')
f.write("Life is too short")
f.close()
```


```python
# with 문
with open("foo.txt",'w') as f:
    f.write("Life is too short")        # 자동으로 close 되는 문장
```

