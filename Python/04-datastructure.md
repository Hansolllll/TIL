# 데이터 스트럭쳐
# INDEX
1. 메소드
    1. 문자열 메소드
    2. 리스트 메소드
    3. 딕셔너리 메소드
    4. 세트 메소드
2. 기타 함수
    1. map
    2. fliter
    3. zip

# 1. 메소드(method)
- 메소드 : 객체 안에 들어있는 함수

## 1-1. 문자열 메소드(string method)
- 문자열은 `immutable`하므로 수정 불가
- 원문 수정하고 싶다면 재할당 

- `.capitalize()`
    - 맨 앞 글자를 대문자로 변환

- `.title()`
    - 각 음절 첫글자만 대문자로 변환

- `.upper()`
    - 대문자로 변환

- `.lower()`
    - 소문자로 변환

- `.strip([chars])`
    - [ ] 기입시 내부 문자를 지우고, 미기입시 공백(문자열 좌우 공백)을 지움
    - `.lstrip()`
    - `.rstrip()`
- `.replace(old, new[, count])`
    - old를 찾아서 new로 변환(count만큼)
- `.find(x)`
    - 찾는 문자의 위치를 반환
    - 여러 곳에 위치한 경우 첫 위치 반환
    - 없으면 -1 반환
    - 공백 포함
- `.index(x)`
    - .find와 유사하지만 찾는 문자 없을 경우 오류발생
    - 공백 포함
- `.split(x)`
    - x를 기준으로 분할, x입력 안하면 공백을 기준으로 분할
- `.count(x)`
    - 문자열 내부의 x 갯수 반환



```python
a = hi hEllo hi

a.capitalize() 
-> Hi hEllo hi

a.title()
-> Hi HEllo Hi

a.upper()
-> HI HELLO HI

a.lower()
-> hi hello hi

a.strip('hi')
-> hEllo

a.replace('h', '!', 2)
-> !i !Ello hi

a.find('i')
-> 1

a.index('o')
-> 7

a.split()
-> ['hi', 'hEllo', 'hi']

a.count(h)
-> 2
```

## 1-2. 리스트 메소드
- `.append(x)`
    - list에 x 추가
- `.extend(iterable)`
    - list끼리 결합
- `.insert(idx, x)`
    - 특정위치에 데이터 삽입
- `.remove(x)`
    - x위치의 데이터 제거
- `.pop([idx])`
    - 리스트의 마지막 요소 또는 인덱스에 해당하는 데이터를 빼냄
- `.sort()`
    - 리스트 내부 데이터를 크기순 정렬
    - 원본수정, return 없음
    - `.sort(reverse=True)` : 역순
    - `sorted()` : 함수, 메소드X, 원본수정X, 정렬된 데이터 return
- `.reverse()`
    - 리스트 정렬 순서를 뒤집음, 원본수정
    - list slicing 이용해서 비슷한 결과 낼 수 있음


```python
numbers = [1, 3, 2, 4]
a = [100]

numbers.append(10)
-> [1, 3, 2, 4, 10]

numbers.insert(4, 99)
-> [1, 3, 2, 4, 99]

numbers.remove(4)
-> [1, 3, 2]

numbers.pop(0)
-> [3, 2, 4]

numbers.sort()
-> [1, 2, 3, 4]

numbers.reverse()
-> [4, 2, 3, 1]
```

### list copy
- origin list = [1, 2, 3]
- copy_list = origin_list
- 이때, copy 리스트의 데이터를 수정하면 origin_list도 함께 수정됨(데이터가 저장된 같은 주소를 사용하므로)
- `deepcopy` 사용 권장

### list comprehension
```python
result = []

for number in numbers:
    result.append(number ** 3)
print(result)
```

```python
result2 = [ number ** 3 for number in numbers ]
```
- 위 아래 모두 같은 의미
- comprehension에서 for 뒷부분에 대해 앞부분을 수행
- 조건문은 for 뒤에 붙이며 조건이 and로 묶이면 이어서 작성
```python
result = [char for char in words if char not in vowels if char.isupper()]
```

## 1-3. 딕셔너리 메소드
- `.pop(key[, default])`
    - 해당하는 key의 value pop
    - 원본 수정
- `.update(key=value)`
    - 딕셔너리 내부 데이터 수정
- `.get(key[, default])`
    - 해당하는 key와 value를 가져옴
    - 원본수정 X
    - 해당하는 값 없으면 none 반환

### dict comprehension


```python
for number in numbers:
    result[number] = number ** 3

for k, v in dust.items():
    if v >= 50:
        result[k] = v
```

```python
result2 = {number: number ** 3 for number in range(1, 11) }

result2 = {k : v for k, v in dust.items() if v >= 50}
```
- 위와 아래가 의미하는 것은 동일함

## 1-4. 세트 메소드
- `.add()`
    - 데이터 추가후 정렬되지 않은 데이터가 나옴(인덱스 접근 불가)
    - 하나의 데이터 중복 불가
- `.update()`
    - 괄호 안에 하나의 값만 넣을 경우, 시퀀스 형태 데이터를 하나 하나 잘라서 요소 업데이트
    - 여러 개의 값 업데이트
- `.pop`
    - 무작위의 요소를 pop

```python
fruits = {'apple', 'banana', 'melon'}

fruits.add('watermelon')
-> {'watermelon', 'melon', 'apple', 'banana'}

fruits.update('grape')
-> {'p', 'e', 'banana', 'watermelon', 'apple', 'melon', 'g', 'a', 'r'}

fruits.update({'grape', 'orange'})
-> {'p', 'e', 'banana', 'watermelon', 'apple', 'orange', 'melon', 'g', 'a', 'r', 'grape'}

fruits.pop()
-> {'p', 'banana', 'watermelon', 'apple', 'orange', 'melon', 'g', 'a', 'r', 'grape'}
```
# 2. 기타 함수
## 2-1. map(function, itrerable)
- `function`을 `iterable`에 적용
```python
def cube(x):
    return x ** 3
-> cube 함수 정의 후 적용

result2 = map(cube, a)
print(list(result2))
-> [1, 8, 27]
```

## 2-2. filter(function, iterable)
- filter에 들어가는 function은 T/F를 반환해야함
```python
result2 = filter(is_odd, numbers)
print(list(result2))
```
- 이 때 is_odd(함수)의 결과가 `True`인 것만 반환

## 2-3. zip
- 쌍으로 묶어줌
- 대치되는 갯수만큼만 결과 생성
```python
a = [1, 2, 3, 4]
b = [100, 200, 300, 400]

result = zip(a, b)

-> [(1, 100), (2, 200), (3, 300), (4, 400)]
```

# 기타
- ''.join(my_list)
    - my_list 내부의 데이터들을 '' 내부 값을 이용해 연결
```python
my_list = ['hi', 'my', 'name']
print(''.join(my_list))
print('??'.join(my_list))

himyname
hi??my??name
```