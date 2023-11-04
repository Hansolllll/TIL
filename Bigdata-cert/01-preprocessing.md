INDEX
1. 결측치 처리
    1. 범주형 변수 결측치 처리
    2. 수치형 변수 결측치 처리
2. 이상치 처리
    1. 

---
# 0. 데이터 불러오기

```python
import pandas as pd
X_train = pd.read_csv("X_train.csv")
y_train = pd.read_csv("y_train.csv")
X_test = pd.read_csv("X_test.csv")
```
- 데이터 샘플 확인
- 결측치 컬럼 확인(훈련데이터 사용): ```X-train.isnull().sum```
- 데이터 타입 확인(훈련데이터 사용): ```X_train.info() ```
- 결측치가 많은 컬럼의 고유값 개수 확인: ```X_train['컬럼명'].value_counts() ```

# 1. 결측치 처리
## 1-1. 범주형 변수 결측치 처리
- 삭제
    - `.dropna(axis=0 또는 1)`: 0일 땐 행을, 1일 땐 컬럼을 삭제
    - `.dropna(subset=['컬럼명'])`: 컬럼에 결측치 있을 때 행 삭제
- 최빈값 이용
    - `.fillna(X_train['컬럼명'].mode()[0])`: 컬럼의 최빈값 이용해 결측치 채움(mode는 시리즈 형태로 출력되므로 [0]붙여서 사용하기)
- 없는 값 이용
    - 최빈값을 사용하는게 최선이 아닐 때 새로운 값으로 결측치 채우기
    - `.fillna('값')`
## 1-2. 수치형 변수 결측치 처리
- 평균값: ```.fillna(X_train['컬럼명'].mean())```
- 중앙값: ```.fillna(X_train['컬럼명'].median())```
- 최댓값, 최솟값: 
```.fillna(X_train['컬럼명'].max())```
```.fillna(X_train['컬럼명'].min())```

# 2. 이상치 처리
- 이상한 값 삭제
    - 음수값이나, 과도하게 큰 값은 조건식으로 걸러낼 수 있음
    - ```X_train = X_train[X_train['age']>0]```

