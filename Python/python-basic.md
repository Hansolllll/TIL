# basic command
## 0. 설치
- 홈브루 업데이트(`brew update`)
- pyenv 설치(`brew install pyenv`)
- 설치 확인(`pyenv -v`)
- pyenv 사이트에서 set up을 위한 Zsh 코드 복사(`echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc`)
- 터미널 재실행 및 확인(`pyenv version`)
- python 설치(`pyenv install 3.11.5`)(`pyenv global 3.11.5`)
- python 설치 확인(`python -V`)

## 1.  변수, Variable
- 다양한 값 계산 시 정확도를 높이기 위해 사용
- `=`는 `지정연산자`로서 오른쪽 값을 왼쪽 변수에 지정
- 이후 다시 정의하면 값을 덮어씌움

*데이터 종류*
### 1. 숫자(Number)
    - `정수(Integer)` : `음의 정수`, `0`, `양의 정수`
    - `소수(Floating Point)` : python에선 2와 2.0이 다름

### 2. 문자열(String)
    - (큰/작은)따옴표 안의 값

### 3. 참/거짓(Boolean)
    - `True`와 `False`

### 리스트(List)
    - 변수에 다양한 값 저장 시 사용(여러 값 나열)
    - `대괄호([])` 내부에 표시, `쉼표(,)`로 나눔
    - 리스트 내부 값은 `요소`
    - `요소`의 위치는 `인덱스(index)`/`인덱스`를 통해 위치를 받는 걸 `인덱싱(indexing)`
    - 리스트명[순번] 입력 시 순번의 요소 출력됨(0부터 시작)
    - 요소의 덧셈도 가능

### 사전(Dictionary)
    - `key-value` pair를 이용해 작성(key: value,의 반복 나열)
    - 보통 여는 중괄호 - 공백(줄비움) - 닫는 중괄호 구조로 사용
    - key를 통해 value를 받아올 수 있음

### *`List와 Dictionary 차이`*    
- 리스트는 index가 순서대로 매겨지지만 사전은 순서 개념이 없음
- 리스트의 index는 정숫값이지만 사전의 key는 문자열도 가능

## 2. 조건
- `if` 조건부분:
  (들여쓰기) 조건 만족시 수행부분 
- `elif` 조건부분:
  (들여쓰기) 조건 만족시 수행부분  
    - *elif*(else + if) : 처음 if 조건을 만족하지 않는 else 중 if 조건을 만족하는 것
- `else`:
  (들여쓰기) 조건 불만족시 수행부분

## 3. 반복 
- ***`while`*** 
    - 무언가를 반복할 때 사용
    - while + 조건부분:
      (들여쓰기)수행부분 구조
    - `조건이 True일 때 수행, False일 때 정지`

- ***`for`***
    - `while`과 달리 조건부분이 없고 `수행부분`만 있음
    - `for item in list`형태로 쓰며 `list 내부의 각 데이터를 반복`하는 방식
    - 알고리즘 방식에서 반복문은 주로 for문 사용

### 함수(Function)
- 명령을 저장해서 실행
```
print, max, min, return, import...
```

