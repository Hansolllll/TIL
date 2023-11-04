INDEX
0. 데이터 분리
1. 스케일
    1. MinMaxScaler
    2. StandardScaler
    3. RobustScaler
2. 인코딩
    1. LabelEncoding
    2. One-HotEncoding
3. 데이터 합치기

---
# 0. 데이터 분리
- 전처리된 데이터 불러오기
- 데이터 타입 확인(수치형과 범주형 분리하기 위해)
- 수치형 컬럼과 범주형 컬럼 데이터 나누기(exclude -> 제외, include -> 포함)
```python
n_train = X_train.select_dtypes(exclude='object').copy()
n_test = X_test.select_dtypes(exclude='object').copy()

c_train = X_train.select_dtypes(include='object').copy()
c_test = X_test.select_dtypes(include='object').copy()
```

# 1. 스케일링
- 수치형 데이터 해당
- 트리기반의 모델에선 중요하지 않지만, 선형회귀나 로지스틱회귀 모델에선 중요함
- 스케일러 적용 전 작업할 컬럼명 지장해 놓기(cols)

## 1-1. MinMaxScaler
- 데이터를 0과 1 사이 값으로 변환
```python
from sklearn.preprocessing import MinMaxScaler
scaler = MinMaxScaler()
n_train[cols] = scaler.fit_transform(n_train[cols])
#=> 훈련데이터는 fit_transform
n_test[cols] = scaler.transform(n_test[cols])
#=> 시험데이터는 transform
```
## 1-2. StandardScaler
- Z-score 정규화, 평균 0 / 표준편차 1인 정규분포로 변경
- 이상치가 있을 때 영향을 받음
```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
n_train[cols] = scaler.fit_transform(n_train[cols])
n_test[cols] = scaler.transform(n_test[cols])
```
## 1-3. RobustScaler
- 중앙값과 사분위값 이용, 이상치 영향 최소화
```python
from sklearn.preprocessing import RobustScaler
scaler = RobustScaler()
n_train[cols] = scaler.fit_transform(n_train[cols])
n_test[cols] = scaler.transform(n_test[cols])
```

# 2. 인코딩
- 범주형 데이터 해당
- 스케일러 적용 전 작업할 컬럼명 지장해 놓기(cols)

## 2-1. 라벨(label) 인코딩
- 데이터에 이름표를 달아주듯 값을 부여해 연속적 수치 데이터로 변경
- 숫자값을 가중치로 잘못 인식해 값에 왜곡 생길 수 있음 
```python
from sklearn.preprocessing import LabelEncoder

for col in cols:
    le = LabelEncoder()
    c_train[col] = le.fit_transform(c_train[col])
    c_test[col] = le.transform(c_test[col])
```
## 2-2. 원핫(one-hot) 인코딩
- 변수들을 목록화하여 1 또는 0의 이진수를 부여
- pandas에 내장된 `get_dummies()` 메서드 사용 가능
```python
c_train = pd.get_dummies(c_train[cols])
c_test = pd.get_dummies(c_test[cols])
```

# 3. 데이터 합치기
- 분리해서 스케일링, 인코딩을 거친 데이터들을 다시 합침
- `axis=0`일때 행방향으로 결합되므로 `axis=1` 꼭 기입하기
```python
X_train = pd.concat([n_train, c_train], axis=1)
X_test = pd.concat([n_test, c_test], axis=1)
```
