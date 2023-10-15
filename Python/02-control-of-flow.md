# Control of flow
# INDEX
1. 조건문
    1. if
    2. else
    3. elif
    4. 조건표현식
2. 반복문
    1. while
    2. for
        - sequence형 데이터 반복
        - dictionary 반복
    3. break
    4. continue
    5. else
    6. match

## 1. 조건문(`if`)
- if문은 반드시 참/거짓을 판단할 수 있는 조건식과 함께 사용
- 조건식이 참인 경우 : 이후의 문장 실행
- 조건식이 거짓인 경우 : else: 이후의 문장을 실행

### 1-1. `if` <조건식> : 
    if의 조건식이 참인 경우 실행하는 코드
        - if num % 2 == 1:
            print('홀수입니다.')
        - if num % 2:
            print('홀수입니다.')
        - 0, 1이 자동형변환이 일어나 `True`, `False`로 변환됨

### 1-2. `else`:
    if의 조건식이 거짓인 경우 실행하는 코드

### 1-3. `elif`
- else + if를 의미하며 깔끔한 코드 작성 가능
![elif](../assets/elif.jpg) 

if <조건식>:

    if 조건이 참인 경우 실행

elif <조건식>:
    
    elif 조건이 참인 경우 실행

...

else:

    위의 조건식에 하나도 부합하지 않는 경우 실행

### 1-4. `조건표현식`
- ***True value if <조건식> else false value***
- 기존의 if와 동일한 의미
- `if`와 `else` 사이의 조건식 만족시 `True value` 수행, 불만족시 `False value` 수행

## 2. 반복문
### 2-1. while
```python
while <조건식>:
    실행할 코드
```
- 조건 만족시 아래 코드 실행, 불만족시 밖으로 빠져나옴
- 빠져나올 조건을 넣지 않으면 무한루프 생성됨

### 2-2. for

```python
for variable in sequence:
    실행할 코드
```
- 정해진 범위 내의 반복
- `일의 양`을 정해주는 개념 

#### 2-2-1. sequence형 데이터 반복
- sequence 자료형인 `List`/`Range`/`Tuple`/`String` 사용, 자료형 내부를 한바퀴 돌고 정지
- 자료형의 범위를 초과해서 동작할 수 없음
    - IndexError: list assignment index out of range 발생
- 자료가 계속 추가되는 경우 `len()` 함수 사용해 코드 작성 
    - for i in range(len(menus)):
- ***enumerate*** 
    - 리스트의 원소에 순서값을 부여
    - 데이터와 인덱스 값을 포함하는 `enumerate` 객체 반환(`tuple` 형태)    
        - for item in enumerate(menus):
        - (0, '라면')

#### 2-2-2. dictionary 반복
- 원칙적으론 시퀀스 자료형(`List`/`Tuple`/`Range`/`String`)만 반복구문 가능하지만 `Dictionary`도 다음과 같은 상황에 반복 가능

1. for key in dict:
        
        ex. for key in blood_type:
                print(blood_type[key])
- `print(info[key])`를 통해 `value`를 함께 출력 가능

2. for key in dict.keys():

        ex. for key in blood_type.keys():
                print(key)
- `dict.keys()`를 통해 `dictionary`의 `key`만 가져올 수 있음

3. for value in dict.values():

        ex. for value in blood_type.values():
                print(value)        
- `dictionary`의 `value`만 가져옴

4. for key, value in dict.items():
        
        ex. for key, value in blood_type.items():
                
- `dictionary`의 `key-value` 쌍을 가져옴

#### 2-3. break
- 특정 조건 만족시 반복문 종료함

#### 2-4. continue
- 특정 조건 불만족시 반복문을 종료하는 것이 아닌 다음 반복을 실행함

#### 2-5. else
- 끝까지 반복이 진행됐지만 `break`를 만나지 않은 경우

### 2-6. match
```
match value:
    case 조건:
        실행할코드
    case 조건:
        실행할코드
    case _:
        실행할코드
```
- if문처럼 특정 값이나 조건에 따라 결과 출력