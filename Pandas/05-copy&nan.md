# INDEX
1. copy
2. 결측치
    1. 결측치 확인

---
# 1. copy
- DataFrame 복제(원본에 영향 X)
- 원본데이터에 바로 작업하기보다 복제본을 만들고 작업하면 정확도를 높일 수 있음 

# 2. 결측치
- 비어있는 데이터 (NaN, Null)
- 결측치 처리 순서
    - 결측 데이터 확인
    - 결측치가 아닌 데이터 확인
    - 결측 데이터 채우기
    - 결측 데이터 제거

## 2-1. 결측치 확인 
### 2-1-1. `.isnull()`, `.isna()`
- 결측치는 True, 아니면 False라고 채워진 DataFrame 반환(컬럼 선택 사용 가능)
```python
df['컬럼명'].isnull()
```
### 2-1-2. `.isnull().sum()` 
- 데이터프레임에서 컬럼별 결측치의 수 반환
```python
df.isnull().sum()
```
### 2-1-3. `.isnull().sum().sum()`
- 전체 결측 데이터 갯수 반환
```python
df.isnull().sum().sum()
```
### 2-1-4. 결측 데이터 필터링 
- `.loc` 이용해 조건 필터링 사용 가능
```python 
df.loc[df['컬럼명'].isnull()]
```
=> df[df['컬럼명'].isnull()]과 동일 


## 2-2. 결측치가 아닌 데이터 확인 
### 2-2-1. `.notna()`, `.notnull()`
- `.isnull()` , `.isna()` 반대
- bool type 으로 `True`, `False` 반환
- `.sum()` 이나 `.sum().sum()` 사용 가능

## 2-3. 결측 데이터 채우기
- `fillna()` 사용
- 결측치를 채운 후 변수에 꼭 할당하기
### 2-3-1. 카테고리형
- 범주 안에 있는 데이터로만 추가 가능
```python
df['컬럼명'].cat.add_categories('채울 값').fillna('채울 값')
```
### 2-3-2. 통계값으로 채우기
- 평균
```python
df['컬럼명'].fillna(df['컬럼명'].mean())
```

- 중앙값
```python
df['컬럼명'].fillna(df['컬럼명'].median())
```

- 최빈값
    - 최빈값을 출력하면 시리즈 형태로 출력되므로 [0]을 입력해 그 값만 사용할 것
```python
df['컬럼명'].fillna(df['컬럼명'].mode()[0])
```
## 2-4. 결측 데이터 제거
- `.dropna()` 사용
- ***how 옵션***
    - `.dropna(how='any')`: 결측치 1개라도 있을 시 제거
    - `.dropna(how='all')`: 모두 결측치일 때 제거
- ***axis 옵션***
    -  `.dropna(axis=0)`: (기본값) 행 삭제
    -  `.dropna(axis=1)`: 컬럼 삭제
- ***subset 옵션***
    -  `.dropna(subset=['컬럼명1', '컬럼명2'])`: 특정 컬럼에 결측치가 있으면 데이터 삭제(기본: 행)
- 중복값 제거:
    -  `.drop_duplicates(subset=['컬럼명'], keep='last')` : 컬럼 내에서 중복된 데이터 제거, 기본적으로 중복데이터 중 앞의 값을 살리지만 keep='last' 설정 시 뒤의 값을 살릴 수 있음 