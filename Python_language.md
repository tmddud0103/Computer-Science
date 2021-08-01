# 파이썬 언어

## is , == 차이

### is와 ==의 차이

- `is`는 변수가 같은 `Object(객체)`를 가리키면 True
- `==`는 변수가 같은 `Value(값)`을 가지면 True

### ‘is’의 예시

- a와 b는 같은 리스트 객체를 가리킨다.
- a와 b는 같은 객체이기 때문에 True
- a와 c는 값은 같지만 다른 객체이기 때문에 False

```python
>>> a = [1,2,3]
>>> b = a
>>> c = [1,2,3]
>>> a is b
True
>>> a is c
False
```

### ’==’의 예시

- a와 b는 같은 리스트 객체를 가리킨다.
- a와 b는 값들을 가진 리스트이기 때문에 True
- a와 c는 값들을 가진 리스트이기 때문에 True

```
>>> a = [1,2,3]
>>> b = a
>>> c = [1,2,3]
>>> a == b
True
>>> a == c
True
```

### 결론: is는 값을 비교하는 것이 아닌 레퍼런스를 비교

### 값이 같다면 ==, 인스턴스 데이터 저장공간도 같다면 is



## list append(), extend() 차이

> insert 까지

array.append(x) 

```python
>>> nums = [1, 2, 3] 
>>> nums.append(4) 
[1, 2, 3, 4] 
>>> nums.append([5, 6]) 
[1, 2, 3, 4, [5, 6]] # 리스트가 하나의 객체로 추가되었음
```



array.extend(iterable) 

```python
>>> nums = [1, 2, 3]
>>> nums.extend([4, 5])
[1, 2, 3, 4, 5]  #리스트로 주어진 [4, 5]의 요소가 각각 추가 되었음

>>> a = [10]
>>> nums.extend(a) 
[1, 2, 3, 4, 5, 10]
```



array.insert(i, x)

```python
>>> nums = [1, 2, 3]
>>> nums.insert(0, [10, 20])  # 0번째(맨앞에) 추가
[[10, 20], 1, 2, 3]

>>> nums.insert(-1, 100)  # 끝에서 1번째 전에 추가
>>> print(nums)
[[10, 20], 1, 2, 100, 3]  # 리스트 맨 끝에 저장되지 않음
```

**1) append 함수**

array.append(x) 형태 

x를 arry의 맨 끝에 객체로 추가 

x가 iterable 자료형이더라도 전체를 하나의 객체로 해서 요소로 추가

**2) extend 함수**

array.extend(iterable) 형태로 사용

iterable의 각 요소를 하나씩 array의 끝에 요소로 추가

append 함수와 다른 점은 괄호 안에 iterable 자료형만 추가 가능

**3) insert 함수**

array.insert(i, x) 형태

원하는 위치 i에 x를 삽입, 값 x는 객체로 추가

append 함수와 마찬가지로 iterable 자료형이더라도 하나의 요소로 삽입