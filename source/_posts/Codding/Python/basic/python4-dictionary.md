---
title: python 딕셔너리
categories:
  - 연습
  - 파이썬
  - 기초
tags:
  - 파이썬
date: 2021-11-01 16:19:58
---
## 딕셔너리 (Dictionary)
#### '이름'='홍길동, '생일'='n월n일'과 같이 대응 관계를 나타낼 수 있는 자료형 (연관배열, 해시)
#### {key1:Value1, key2:Value2, key3:Value3} --> {} 로 둘러싸여 있고, 쉼표로 구분
#### 열쇠(key)가 있어야 값(value)을 얻는다.


```python
reset -f
```


```python
dict = {'name':'pei','birth':'1118'}
```


```python
whos
```

    Variable   Type    Data/Info
    ----------------------------
    dict       dict    n=2
    


```python
a = {'a':[1,2,3]} # Value에 리스트도 넣을 수 있다.
```


```python
# 딕셔너리 추가
a = {1:'a'}
print(a)

a[2] = 'b' # a[ 2 ]에서 2는 몇번째 요소의 의미가 아니라 key 값을 의미한다.
print(a)

a[3] = [1,2,3]
print(a)

a['name'] = 'pay'
print(a)
```

    {1: 'a'}
    {1: 'a', 2: 'b'}
    {1: 'a', 2: 'b', 3: [1, 2, 3]}
    {1: 'a', 2: 'b', 3: [1, 2, 3], 'name': 'pay'}
    


```python
# 삭제 del
del a['name']
print(a)
```

    {1: 'a', 2: 'b', 3: [1, 2, 3]}
    


```python
# 딕셔너리 주의사항 : key 값이 중복될 경우 기존 값을 대체한다.
a={1:'a',1:'b'}
print(a)
```

    {1: 'b'}
    


```python
# 딕셔너리 관련 함수

# key 리스트 생성
a = {'name':'pey','phone':'01012345678','birth':'1118'}
print(a.keys()) #딕셔너리의 key 만을 모아 딕셔너리(dict_keys)로 만듦
print(list(a.keys()))
```

    dict_keys(['name', 'phone', 'birth'])
    ['name', 'phone', 'birth']
    


```python
# Value 리스트 만들기 (values)
print(a.values())
# key, value 쌍 얻기 (items)
print(a.items())
# key, value 쌍 모두 지우기 (clear)
print(a.clear())
```

    dict_values(['pey', '01012345678', '1118'])
    dict_items([('name', 'pey'), ('phone', '01012345678'), ('birth', '1118')])
    None
    


```python
# key로 value 얻기 (get)
a = {'name':'pey','phone':'01012345678','birth':'1118'}
print(a.get('name'))
a['name'] ## get 대체로 index를 이용 가능
```

    pey
    




    'pey'



