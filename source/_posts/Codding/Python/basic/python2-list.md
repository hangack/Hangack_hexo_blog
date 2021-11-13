---
title: python 리스트
categories: 
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
date: 2021-11-01 16:11:09
---
## 리스트(list)
### 여러개의 자료를 하나의 변수에 담기 위한 자료형. 순서가 존재한다.
##### c 언어 배열과 동일하게 첫번째 자료의 할당 번호는 '0'번이다.
##### 반면 list의 자료형의 형태는 자유롭다. (실수 정수 문자형 동일한 리스트에서 사용 가능)


```python
a = [1,3,5,7,9]
```


```python
print(a)
print(a[0],a[3]) #변수_이름[요소_번호]
```

    [1, 3, 5, 7, 9]
    1 7
    


```python
b= a[2]
```


```python
whos
```

    Variable   Type    Data/Info
    ----------------------------
    a          list    n=5
    b          int     5
    c          str     my_note
    


```python
a
```




    [1, 3, 5, 7, 9]




```python
#리스트에서 자료를 뽑아내는 방식 1: 인덱싱  /  2: 슬라이싱
a[0:2] #  #:#의 의미는 0 <= x < 2
```




    [1, 3]




```python
b=a[0:2]
print(b)
```

    [1, 3]
    


```python
a=[1, 3.5 , "n o t e", [1,2,3]]
a
```




    [1, 3.5, 'n o t e', [1, 2, 3]]




```python
whos
```

    Variable   Type    Data/Info
    ----------------------------
    a          list    n=4
    b          list    n=2
    c          str     my_note
    


```python
# 덧셈
a = [1,2,3]
b = [4,5,6]
print(a+b)
```

    [1, 2, 3, 4, 5, 6]
    


```python
# 곱셈 (반복)
print(a*3)
```

    [1, 2, 3, 1, 2, 3, 1, 2, 3]
    


```python
# 리스트 길이 구하기
len(a)
```




    3




```python
# 리스트 요소 수정 <-> 튜플 (Tuple) : 수정될 수 없다.
a = [1,2,3]
a[2] = 4
print(a)
```

    [1, 2, 4]
    


```python

```


```python
## -->>  ### str(   ) 문자로 변경
str(a[2])+"hi"
```




    '4hi'




```python
int(3.6)
```




    3




```python
# 리스트 내의 리스트
a = [['apple','banana','cherry']]

print(a[0])
print(a[0][0])    # 0번 리스트 안의 0번 속성
print(a[0][1][3]) # 0번 리스트 안의 1번 속성의 3번 word
print(a[0][1])
```

    ['apple', 'banana', 'cherry']
    apple
    a
    banana
    


```python
# 리스트 요소 삭제 1
a = [1,2,3,4,5]
del a[2:]  ##슬라이싱에서 끝 값을 비웠을 경우 리스트의 끝 값까지 선택된다.
print(a)

# 리스트 요소 삭제 2
a = [1,2,4,3,5]
a.remove(3)  ## '.' 이후 Tab 키를 누르면 해당 변수에 사용 할 수 있는 명령어 list를 알려준다.
print(a)
```

    [1, 2]
    [1, 2, 4, 5]
    

### a=[1,2,3,4,5] 라고 쓰면, a 변수는 번지수(이름표) / 실제 a 번지에 들어가 있는 내용물 : 객체(Object)

#### 리스트 명령어
URL: [List method](https://docs.python.org/ko/3/tutorial/datastructures.html)


```python
# 리스트 요소 추가 1 (append)
a =[1,2,3]
a.append(4)
print(a)

# 리스트 요소 추가 2 (insert)
a =[1,2,3]
a.insert(0,4)  ## insert(A,B) A번 항목에 B 삽입
print(a)
```

    [1, 2, 3, 4]
    [4, 1, 2, 3]
    


```python
# 리스트 오름차순 정렬 (sort)
a=[1,4,3,2]
a.sort()
print(a)

a=['a','c','b']
a.sort()
print(a)
```

    [1, 2, 3, 4]
    ['a', 'b', 'c']
    


```python
# 리스트 뒤집기 (reverse)
a=['a','c','b']
a.reverse()
print(a)
```

    ['b', 'c', 'a']
    


```python
# 해당자료는 리스트에서 몇번째 자료인가? (index)
a=[1,2,3]
print(a.index(3))
z=[1,2,3,'haha']
(z.index('haha'))
```

    2
    




    3




```python
# 리스트에서 끄집어내자: 팝: (pop) --- 구조적으로 변화시킨다
a=[1,2,3,4]
a.pop()
print(a)
print(a.pop())
print(a)
```

    [1, 2, 3]
    3
    [1, 2]
    


```python
a=[1,2,3,4]
a.pop(2)
```




    3




```python
# 지정된 값이 몇개인지 (count)
a=[1,2,3,1]
a.count(1)
```




    2




```python
# 확장 (extend)
a=[1,2,3]
a.extend([4,5,3])
print(a)
```

    [1, 2, 3, 4, 5, 3]
    

