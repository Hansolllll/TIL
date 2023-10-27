# INDEX
1. 함수
    1. .head() 및 .tail()   
    2. .info()
    3. .describe()
    4. .value_counts()
2. 속성
    1. ndim
    2. shape
    3. index
    4. columns
    5. values
    6. T
3. 타입변환
4. 정렬
    1. sort_index
    2. sort_values
5. loc & iloc
    1. loc
    2. iloc

---

- 타이타닉 데이터 불러오기
```python
df = sns.load_dataset("titanic")
```
# 1. 함수
- 데이터를 조회하는 데 필요한 함수들
## 1-1. `.head()` 및 `.tail()`
- `.head()` 
    - *앞*에서부터 조회하고 싶은 데이터의 수 입력(default 값은 5)
- `.tail()`
    - *뒤*에서부터 조회하고 싶은 데이터의 수 입력(default 값은 5)
## 1-2. `.info()`
- 컬럼별 데이터의 갯수 및 타입 확인 가능
- 타입종류 : `int32`, `int64`, `float64`, `object`, `category`, `bool`
## 1-3. `.describe()`
- 컬럼에 대한 요약 통계 제공
![describe()](./../assets/describe().jpeg)
- 수치형 컬럼이 기본이지만 include='object' 이용해 문자열 컬럼도 사용가능
```python
df.describe(include='object')

df.describe(include='O')
```
## 1-4. `.value_counts()`
- `column별 값의 분포` 확인
```python
df['컬럼명'].value_counts()
```

# 2. 속성(function) 
- 데이터를 조회하는데 필요한 속성 값
- 함수형으로 사용하지 않으므로 뒤에 괄호 없음

## 2-1. `.ndim` 
- `차원` 출력 
- DataFrame의 차원은 2, Series의 차원은 1

## 2-2. `.shape`
- 데이터의 `크기` 출력
- (행, 열)의 형태로 출력

## 2-3. `.index`
- 인덱스 확인 가능
- 기본 설정은 RangeIndex(start= , stop= , step= )

## 2-4. `.columns`
- 컬럼명 출력

## 2-5. `.values`
- 모든 값을 출력하면 *numpy array* 형식으로 출력

## 2-6. `.T`
- 전치(Transpose)
- index축과 column축 교환

# 3. 타입변환(astype)
- 종류
    - `int64`
    - `int32`
    - `objec`
    - `float64`
    - `category`
    - `bool`
- 사용
```python
df['컬럼명'].astype('바꿀타입')
```

# 4. 정렬(sort)
## 4-1. `sort_index`
- index 정렬
    - index를 기준으로 정렬
    - 기본 오름차순, 내림차순시 `ascending=False` 입력
```python
df.sort_index(ascending=False)
```

## 4-2. `sort_values`
- 값에 대한 정렬
- by 뒤에 기준 컬럼 설정(생략 가능) 
- 기준 컬럼 2개 이상 지정 시 []로 묶기
- 컬럼별 오름차순/내림차순 지정 가능
```python
df.sort_values(by=['컬럼명1', '컬럼명2'], ascending=[True, False])
```

# 5. `loc` & `iloc`

## 5-1. `loc`
- indexing
    - 인덱스 명 사용
    - [행, 열]
- slicing    
    - 범위 지정시 *시작(포함):끝(포함)*
    - 다수개의 컬럼 지정시 []로 묶기
```python
df.loc[행1:행5, ['컬럼1', '컬럼2']]
```
- filtering
    - df[condition]과 df.loc[condition]의 두 가지 방법
    - 조건과 칼럼 동시 조회시 df.loc[condition]이 편리
    - 다중 조건시 &(and)나 |(or) 사용
```python
condition = df['컬럼명'] == '값'
df[condition]
df.loc[condition, '컬럼명']
```

## 5-2. `iloc`
- indexing
    - 인덱스 번호 사용
    - [행, 열]
- slicing    
    - 범위 지정시 *시작(포함):끝(미포함)*
    - 다수개의 컬럼 지정시 []로 묶기
```python
df.loc[행1:행5, ['컬럼1', '컬럼2']]
```


