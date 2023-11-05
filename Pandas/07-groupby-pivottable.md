# INDEX
1. apply
    1. function
    2. lambda
2. groupby
    1. 2개 이상의 컬럼으로 그룹
    2. 특정 컬럼에 대한 결과 도출
        - 1개의 특정컬럼
        - 다수개의 특정컬럼
    3. 인덱스 초기화
    4. 다중 통계함수 적용
3. pivot_table
    1. 1개 그룹에 대한 단일 컬럼 결과
    2. 다중 그룹에 대한 단일 컬럼 결과
    3. 다중 통계함수 적용
---
# 1. `apply()`
- 데이터 전처리시 활용
- 복잡한 로직을 컬럼이나 데이터프레임에 적용시 사용

## 1-1. function
- 정의한 함수를 컬럼이나 데이터프레임에 적용 가능
```python
def function(x):
    pass

df['컬럼명'].apply(function)
```
## 1-2. lambda
- 함수를 사용하지 않아도 되는 간단한 로직은 `lambda` 사용 가능
```python
df['컬럼명'].apply(lambda x: pass)
```
# 2. `groupby()`
- 그룹핑시 활용
- 일반적으로 ***통계함수***와 함께 적용
```python
# 기준 삼을 컬럼과 확인할 통계함수 입력
df.groupby('컬럼').mean
```
## 2-1. 2개 이상의 컬럼으로 그룹
- 컬럼을 리스트로 묶기
```python
df.groupby(['컬럼1', '컬럼2']).mean
```
## 2-2. 특정 컬럼에 대한 결과 도출
### 2-2-1. 한 개의 특정 컬럼
- ***특정컬럼에 대한*** 기준컬럼의 결과 확인 가능
```python
# 컬럼3에 대한 컬럼1과 컬럼2의 평균값 확인 
df.groupby(['컬럼1', '컬럼2'])['컬럼3'].mean()

# 데이터프레임으로도 출력 가능(아래 2개 동일)
pd.DataFrame(df.groupby(['컬럼1', '컬럼2'])['컬럼3'].mean())
df.groupby(['컬럼1', '컬럼2'])[['컬럼3']].mean()
```
### 2-2-2. 다수개의 특정 컬럼
- 특정 컬럼을 리스트 형태로 묶어주기
```python
df.groupby(['컬럼1', '컬럼2'])[['컬럼3', '컬럼4']].mean()
```
## 2-3. 인덱스 초기화
- 데이터프레임의 앞에 새로운 인덱스 부여
```python
df.groupby(['컬럼1', '컬럼2'])[['컬럼3']].mean().reset_index()
```
## 2-4. 다중 통계함수 적용
- 여러 통계값 확인시 `.agg()`사용
```python
# 컬럼3 & 4에 대한 컬럼1 & 2의 mean과 sum 확인(데이터프레임)
df.groupby(['컬럼1', '컬럼2'])[['컬럼3', '컬럼4']].agg(['mean', 'sum'])
```

# 3. pivot_table
- `groupby()`와 유사
- `index`, `columns`, `values` 지정

## 3-1. 1개 그룹에 대한 단일 컬럼 결과
- index에 그룹 표기
```python
df.pivot_table(index='컬럼1', values='컬럼2')
```
- columns에 그룹 표기
```python
df.pivot_table(columns='컬럼1', values='컬럼2')
```
- 컬럼을 `index`와 `column` 중 어디에 배치하느냐에 따라 형태가 달라짐

## 3-2. 다중 그룹에 대한 단일 컬럼 결과
- `index`나 `columns`에 리스트 형태로 다수개의 컬럼을 대입
```python
# 컬럼1과 컬럼3의 조합에서 컬럼2에 대한 데이터
df.pivot_table(index=['컬럼1', '컬럼3'], values='컬럼2')
```
## 3-3. 다중 통계함수 적용
- 다중 통계함수 적용시 `aggfunc` 사용
```python
df.pivot_table(index='컬럼1', columns='컬럼3', values='컬럼2', aggfunc=['sum', 'mean'])
```