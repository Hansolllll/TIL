# 모듈
- `import` 이용해 외부 파일/함수 불러옴 

# 패키지
```python
myPackage/
    __init__.py
    math/
        __init__.py
        fibo.py
        fomula.py
```
- __init__.py 파일 꼭 있어야 함
- `from` a `import` b : a 파일에서 b 함수 불러옴
- `import *` : 골라서 불러오는 게 아닌 모두 불러오기
- 기존에 존재하는 변수나 함수와 불러오는 함수의 이름이 충돌하는 경우 `as`를 이용해 이름을 바꿔서 불러올 수 있음
    - from myPackage.math import fomula as f

## 파이썬 내장 패키지
### math 
- `.ceil()` : 올림처리
- `.floor()` : 내림처리
- `.sqrt()` : 루트
- `.factorial` : 팩토리얼

### random
- `.random()`: 난수 반환 & 실행시마다 다른 값
- `.randint()`: () 범위 내의 임의의 정수 반환
- `.seed()`: ()안의 수를 기반으로 랜덤하게 계산된 숫자 반환 & 반복해도 같은 값
- `.shuffle()`: 리스트 내부 값을 무작위 정력
- `.choice()`: 무작위 복원추출
- `.sample(population, k)`: 범위 안에서 k개 데이터 추출

### datetime
- `.now()`: 현재 시각 반환 & 객체 자체가 출력 기능
- `.today()`: 현재 날짜 및 시간 변환 & print 통과시 데이터 형태가 보기 쉽게 바뀜
- `.utcnow`: utc(coordinated universal time) 기준 현재 시각 반환
- `.strftime()`: 괄호 안의 형태로 데이터 보여줌
- now의 정보확인기능
    - `now.year`: 현재 해 
    - `now.day`: 현재 일
    - `now.weekday()`: 현재 요일(0 ~ 6 / 월 ~ 일)
