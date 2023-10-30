# INDEX
1. 통계
    1. .describe()  
    2. .count()
    3. .min() & .max()
    4. .mean()
    5. .median()
    6. .sum()
    7. .cumsum() & .cumprod()
    8. .var()
    9. .std()
    10. .agg()
    11. .quantile()
    12. .unique() & .nunique()
    13. .mode()
    14. .corr()

---
# 1. 통계
- 데이터분석에서의 요소
- 아래 함수 사용 형식
```python
df['컬럼명'].함수()
```
## 1-1. .describe()
- 전반적인 주요 통계 확인
- ***수치형컬럼***에 대한 통계표
- include='O' 또는 include='object'로 문자열 컬럼 정보도 확인 가능

## 1-2. .count()
- 결측치가 빠진 데이터의 갯수

## 1-3. .min() & .max()
- 데이터프레임 또는 데이터프레임의 특정 칼럼에서의 최솟값 또는 최댓값

## 1-4. .mean()
- 데이터의 평균
- 조건별 평균
 ```python
df.loc[조건, '컬럼명'].mean()
```
- skipna=True 옵션
    - NaN값을 제외하고 평균 계산
    - skipna=False로 입력시 NaN값이 있는 컬럼은 NaN값 출력됨

## 1-5. .median()
- 데이터 오름차순 정렬시 중앙에 위치한 값
- 데이터 수가 짝수개일 경우 가운데 2개의 중앙 데이터 평균값 출력
## 1-6. .sum()
- 데이터의 합계
- pandas 최신버전에서는 numeric_only=True라는 옵션 넣어줘야함(원래는 문자가 포함되어있어도 자동 계산됐지만 최신버전부터는 에러 발생)
## 1-7. .cumsum() & .cumprod()
- .cumsum(): 누적합
- .cumprod(): 누적곱

## 1-8. .var()
- 편차 제곱의 평균

## 1-9. .std()
- 분산의 제곱근

## 1-10. .agg()
- 단일 또는 복수개의 컬럼에 복수개의 함수 적용 가능
```python
df[['컬럼1', '컬럼2']].agg(['min', 'max', 'count', 'mean'])
```
## 1-11. .quantile()
- 분위(분할지점) 반환
- 0.1은 하위 10%, 0.9는 상위 10%
```python
df['컬럼1'].quantile(0.1)
(= df['컬럼1'].quantile(.1))
```
## 1-12. .unique() & .nunique()
- 컬럼의 고유값(unique)과 고유값의 개수(nunique)를 구할때 사용

## 1-13. .mode()
- 가장 많은 데이터
## 1-14. .corr()
- 컬럼별 상관관계
- -1(반비례) ~ 1(정비례) 사이의 값
- 괄호안 numeric_only=True 넣어주기