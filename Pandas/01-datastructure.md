# INDEX
1. Series 및 DataFrame
    1. Series
        - 생성
        - 선택
    2. DataFrame
        - 생성
        - 선택
        - 속성

2. Index
    1. Indexing
    2. Fancy indexing
    3. Boolean indexing

3. Value
---

- 라이브러리 불러오기 
```python
import pandas as pd
```
- 데이터 불러오기
```python
df = pd.read_csv('파일명.csv')
```

# 1. Series 및 DataFrame
## 1-1. Series
- 1차원 배열
- index 사용가능

### 생성
- 시리즈로 만들 데이터를 리스트 형태로 넣기
- 기본 데이터타입 지정 가능
- 다양한 타입 입력시 `object`타입으로 생성됨
```python
series_name = Pd.Series(['data_a', 'data_b', 'data_c'], dtype='object' )
```
### 선택
- 한 개의 컬럼만 선택 가능
```python
df['컬럼명']
```

## 1-2. DataFrame
- 2차원 데이터 구조
- 행과 열로 구성
### 생성
```python
pd.DataFrame({
'컬럼명':데이터,
'컬럼명':데이터,
'컬럼명':데이터
})
```
### 선택
- 여러 개의 컬럼 선택 가능(대괄호로 묶어주기)
```python
df[['컬럼명1', '컬럼명2']]
```
### 속성
- `.index`
- `.columns`: 컬럼명 반환
- `.values`: 데이터 값 반환
- `.dtypes`: 컬럼별 데이터타입 반환
- `.T`: 데이터프레임의 행과 열 switch

# 2. Index
- 0 부터 부여되는 `RangeIndex`로 생성
- index 범위 내에서 `indexing` 가능
- 시리즈 생성시, 생성 이후 모두 부여 가능
- 숫자가 아닌 인덱스 사용할 경우(아래 참고)
```python
series_name = pd.Series(['data_a', 'data_b', 'data_c'], index=['a', 'b', 'c'])
```

## 2-1. Indexing
- 기본 숫자형 index와 새로 부여한 index 모두 조회 가능
## 2-2. Fancy indexing
- 인덱스 배열을 전달(index list로 indexing)
## 2-3. Boolean indexing
- index list에서 `True`인 index만 반환
- ***boolean index list와 Series 갯수 일치 필수***

# 3. Value
- series의 데이터 값만 가져옴
```python
series_name.values
```

