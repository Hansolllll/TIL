# INDEX
1. 컬럼
    1. 추가
    2. 삭제
    3. 연산
    4. 타입변환
2. 날짜 및 시간
    1. date_range
    2. date_type
3. 수치형 변환
4. 구간 분할
---
# 1. 컬럼 

## 1-1. 추가
- 새로운 컬럼에 임의의 값을 넣어 추가 가능
```python
df['컬럼명'] = 값
```

## 1-2. 삭제
- 행 삭제
    - `index`를 이용해 삭제
    - 범위를 이용해 삭제: range에 해당하는 범위 삭제 => ```df.drop(np.arrange())```
    - `fancy indexing` 이용해 삭제 => ```df.drop([, , , ])```
- 열 삭제
    - `axis=1` 기입해 삭제
    - `inplace=True` 옵션 사용해 변수에 지정하지 않고 바로 적용 가능
## 1-3. 연산
- 컬럼 사이의 연산 가능
- 문자열 이어붙일 수 있음
- 연산에 사용된 컬럼에 `NaN` 값이 있을 경우 `NaN` 출력
```
df[컬럼1] = df[컬럼2] + df[컬럼3]
```
## 1-4. 타입변환
- 수치형
```
df[컬럼명].astype(int 또는 float)
```
- 범주형
```
df[컬럼명].astype(str)
```
- 카테고리형
```
df[컬럼명].astype(category)
```
# 2. 날짜 및 시간
## 2-1. date_range
- 옵션
    - start: 시작 날짜
    - end: 끝 날짜
    - periods: 생성할 데이터 개수
    - freq: 주기
```python
dates = pd.date_range('20210101', periods=df.shape[0], freq='15H')
```

## 2-2. date_type
- pandas.Series.dt.year: 연도
- pandas.Series.dt.month: 월
- pandas.Series.dt.week: 주
- pandas.Series.dt.day: 일
- pandas.Series.dt.dayofweek: 요일
- pandas.Series.dt.weekday: 요일 (dayofweek과 동일)
- pandas.Series.dt.hour: 시
- pandas.Series.dt.minute: 분
- pandas.Series.dt.second: 초
- pandas.Series.dt.weekofyear: 연중 몇 째주
- pandas.Series.dt.dayofyear: 연중 몇 번째 날
- pandas.Series.dt.quarter: 분기

- `.dt` 접근자 사용하기 위해선 `datetime` 타입으로 변경 필요
```python
pd.to_datetime(df['컬럼명'])
```

# 3. 수치형 변환
- 수치형이 아닌 컬럼을 수치형으로 변환
```python
pd.to_numeric(df['컬럼명'])
```
- NaN 값이나 수치변환이 불가한 문자열 존재시 오류 발생
- `errors=` 옵션
    - `ignore`: 잘못된 문자열 무시
    - `raise`: 오류 발생
    - `coerce`: 잘못된 문자열 NaN 값으로 반환

# 4. 구간 분할
## 4-1. `pd.cut()`
- 연속된 수치를 구간으로 나눔
- 범위 또는 명목을 미리 지정한 후 코드에 할당
    - label 지정시 bin 개수보다 1개 적게 작성
- `right=False` 지정시 우측 범위 미포함
- 이상치 존재시 부적합
```python
bins = [0, 200, 400]
pd.cut(df['컬럼명'], bins, right=False)

labels = ['A', 'B', 'C']
pd.cut(df['컬럼명'], bins, labels=labels, right=False)
```
## 4-2. `pd.qcut()`
- 데이터의 분포가 서로 유사하도록 분할
```python
df2['컬럼명1'] = pd.qcut(df['컬럼명2'], q=분할할 구간 수)
```
- 분할 범위 직접 조정 가능하며 label 이용 가능
```python
qbins = [10, 20, 30, 40]
pd.qcut(df['컬럼명'], qbins)

qlabes = ['A', 'B', 'C']
pd.qcut(df['컬럼명'], qbins, labels=qlabel)
```