# 함수(Function)

## 함수의 선언과 호출
- 함수의 선언
```python
def func_name(parameter1, parameter2):
    code1
    code2
    return value
```
- 함수의 호출(실행)
```python
func_name(parameter1, parameter2)
```

## 함수의 return
- ***값 반환*** & ***함수 종료***
- `return`이 없다면 -> None 반환
    - `print`와의 차이 : print는 값을 콘솔에 출력해 보여주는 함수로서 값 반환하지 않음
    - print(func(1)) 일 때, func(1)의 값을 콘솔에 출력함과 동시에 func(1)의 값이 사라지며 print(None)으로 바뀜 -> None 출력
- 하나의 객체만 반환
    - return 1, 2 -> tuple인 (1, 2) 출력 
    - jupyter notebook은 return이 구현된 함수 여러 개 실행시 마지막 함수의 값을 return함

## 함수의 인수
### 위치인수
- 입력된 인수를 순서에 맞게 대입함(위치로 판단)

### 기본값
```python
def greeting(name='익명'):
```
- *optional parameter*
- 위처럼 변수 옆에 기본값을 설정해두면 함수 호출시 parameter를 필수로 입력하지 않아도됨
- optional parameter는 마지막 위치에 입력
```python
def greeting(name='익명', age):
    return f'{name}님은 {age}살입니다.'

    -> 오류 발생
```

### 키워드 인자
- 함수 호출시 원하는 위치에 직접적으로 특정인자 전달
- optional parameter가 앞에 있어도 작동 가능
```python
def greeting(age, name='익명'):
    return f'{name}님은 {age}살입니다.'

print(greeting(name='홍길동', age=20))
```

### 가변인자 리스트
- 함수 선언시 임의 개수의 인자를 받도록 함
- 인자 앞에 * 붙여 작성
```python
def my_print(*words):
    print(words)
```
- 여러 인자를 받아 하나의 튜플로 묶어 출력

### 정의되지 않은 키워드 인자 처리하기
```python
def func(**kwargs):
    code
    ...
```

```python
def fake_dict(**kwargs):
    for key, value in kwargs.items():
        print(f'{key}는 {value}입니다.')
```
- 이 때 fake_dict(korean = '안녕', english = 'hello') 입력시 값이 정의되지 않았지만 `key`에 korean과 english가, `value`에 '안녕'과 'hello'가 입력됨

### dictionary를 인자로 넣기(unpacking)
```python
def sign_up(id, pw, pw_confirmation):
    if pw == pw_confirmation:
        print(f'{id}님 회원가입이 완료되었습니다.')
    else:
        print('비밀번호가 일치하지 않습니다.')

account = {
    'id': 'hansol',
    'pw': '123',
    'pw_confirmation': '123' 
}
sign_up(**account)
```
- sign_up 함수 선언 후 -> 인자에 넣을 값들을 dictionary 형태로 account에 저장 -> `**account` 입력해 실행

### lambda 표현식
- `lambda` parameter: expression
```python
(lambda x, y: x + y)(1, 2)
```
- x, y:와 x + y 사이에 return이 숨겨져 있다고 이해할 것

### 타입힌트
```python
def my_sum(a: int, b: int) -> int:
    return a + b
```
- 위처럼 인자들의 데이터형태를 알려주는 것
- 실행에 영향을 미치진 않음

### 이름공간(space)
- python에서 사용되는 이름들은 이름공간(namespace)에 저장되어 있음

1. Local scope: 정의된 함수 내부
2. Enclosed scope: 상위 함수
3. Global scope: 함수 밖의 변수 혹은 import된 모듈
4. Built-in scope: python이 기본적으로 가지고 있는 함수 혹은 변수

### 재귀(reculsive)
- 재귀함수는 함수 내부에서 자기자신을 호출하는 함수 의미
```python
def factorial(n):
    if n <= 1:
        return 1
    else:
        return factorial(n-1) * n

print(factorial(5))
```
- factorial 안에 factorial 함수가 또 존재하며 n = 1까지 파고들어감
