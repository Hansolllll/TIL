# 00. jupyter 설치

# 01. intro
- `ctrl` + `enter` : 지금 셀 실행
- `shif` + `enter` : 지금 셀 실행 $ 아래로 이동
- `alt` + `enter` : 지금 셀 실행 & 아래에 새로운 셀 추가
- 셀 타입 변경 
    - `markdown` : `M`
    - `raw` : `R`
    - `code` : `C`

## 1. 변수
- 변수 이름 `=` 값
- 어떤 이름이든 무관
- 영어, 숫자, `_` 이용
- 키워드 사용불가

### 1.1 number
- 크게 정수형(`int`)과 소수형(`float`)으로 나뉨
- 허수(j)를 사용가능(이 때 type은 `complex`)
    - c = 1 - 4j 
    - c.imag = -4 (허수부분의 계수)
    - c.real = 1.0 (실수부분의 계수)

### 1.2 boolean
- `True`, `False`로 이루어진 타입

### 1.3 None
- 데이터 없음 

### 1.4 String
- `'`, `"`를 이용해 문자열 표현
- ```과 ``` 사이에 여러줄의 문자열 작성 가능
- `\n`은 줄바꿈, `\t`는 탭 의미

**String interpolation(문자열 보간)**
- `%-formatting`
    - print('홍길동은 %s살입니다.'% age)
- `str.format()`
    - print('홍길동은 {}살입니다.'.format(age))
- `f-string`
    - print(f'홍길동은 {age}살입니다.')

## 2. 연산자
### 2.1 산술연산자
- `+`, `-`, `*`, `/` : 사칙연산
- `**` : 거듭제곱
- `//`, `%` : 나눈 몫, 나머지
    - divmod(a,b) : a를 b로 나눈 몫과 나머지

### 2.2 비교연산자
- `<`, `<=`, `>`, `>=` : 초과, 이상, 미만, 이하
- `==`, `!=` : 같거나 같지않음

### 2.3 논리연산자
- `and` : 양쪽 모두 `True`일 때, `True` 반환
- `or` : 양쪽 모두 `False`일 때, `False` 반환
- *단축평가*
    - `0`은 `False`, `0`이외 값은 `True`로 처리
    - 단축평가(A and B)  
        - `A가 True`일 때 `B 반환` 
        - `A가 False`일 때 `A 반환` 
    - 단축평가(A or B)
        - `A가 True`일 때 `A 반환` 
        - `A가 False`일 때 `B 반환`

### 2.4 복합연산자
- `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, `**=`
- `a 연산자 b`로 사용하며, a와 b의 연산값을 a에 덮어씀

### 2.5 기타연산자
- *`concatenation`*
    - 문자열이나 리스트를 연결
- `in`
    - `a in b`의 형태로 사용되며 `True`, `False` 값으로 결과 반환

*연산자 우선순위*

0. `()`
1. `**`
2. `*`, `/`
3. `+`, `-`
4. `비교연산자`, `is`, `in`
5. `not`
6. `and`, `or`

## 3. 형변환
### 3.1 암시적 형변환
- `int` & `int` 연산 -> `int` 출력
- `float` & `int` 또는 `float` & `float` 연산 -> `float` 출력

### 3.2 명시적 형변환
- `str()` : 문자열로 변환  
- `int()` : 숫자형으로 변환
- `bool()` : 참/거짓형으로 변환

## 4. 시퀀스(sequence) 자료형
- 데이터 `순서`대로 `나열`된 자료 구조
- ***List / Tuple / Range / String***

### 4.1 List
- 선언 : 변수이름 = [valu1, value2, value3]
- 접근 : 변수이름[index]
- 수정 : `변수이름[index] = value4`

### 4.2 Tuple
- 선언 : 변수이름 = (value1, value2, value3)
- 접근 : 변수이름[index]
- List와 유사하지만 *수정불가능(immutable)* 하다.

### 4.3 Range
- `range(n)` : `0부터 n-1`까지 범위
- `range(n, m)` : `n부터 m-1`까지 범위
- `range(n, m, s)` : n부터 m-1까지의 범위, `+s(step의 약자) 만큼 증가`

### 4.4 String 
- 기본 데이터 구조 참고

## 5. 시퀀스 데이터가 아닌 자료구조 
### 5.1 set
- 수학에서의 집합과 동일(중복 없음)
- 선언 : 변수이름 = {value1, value2, value3}

### 5.2 dictionary
- 여러 쌍의 `key`와 `value`로 구성
- `key` : `immutable한 모든 값` 사용가능
(불변값 : string, integer...)
- `value` : `모든 데이터` 가능(list, dict도 가능)
- 선언 : 변수이름 = {key1: value1, key2: value2}
- 접근 : 변수이름[key]

***
*자료구조*
- 시퀀스 자료형
    1. [List] : mutable
    2. (Tuple) : immutable
    3. range() : immutable
    4. 'String' : immutable
    
- 시퀀스가 아닌 자료형
    1. {Set} : mutable
    2. {Dic: tionary} : mutable
***