INDEX

1. 문제정의, 라이브러리/데이터 불러오기
2. 탐색적 데이터 분석 (EDA)
3. 데이터 전처리 및 피처엔지니어링 
4. 검증 데이터 분리
5. 모델 선택/훈련/평가/최적화
6. 예측
7. csv 생성 및 제출

---

# 1. 문제정의, 라이브러리/데이터 불러오기
- 보험료 예측
- 평가: rmse(시험에서 rmse를 지원하지 않음. mse구해서 루트 씌울것)
- csv: id와 예측값
```python
import pandas as pd
train = pd.read_csv('train.csv')
test = pd.read_csv('test.csv')
```
# 2. 탐색적 데이터 분석 (EDA)
- train과 test 데이터의 크기, 샘플, 결측치 확인
- train과 test의 샘플 확인하면서 타겟 컬럼 확인하기(test엔 없고 train엔 있음)

# 3. 데이터 전처리 및 피처엔지니어링
- train과 test에 결측치가 없으므로 object형에 대한 인코딩 진행
```python
# object 컬럼 선택
cols = ['sex', 'smoker', 'region' ]
cols = train.select_dtypes(include='O').columns #=> dtypes로 선택하면 데이터 프레임형태가 반환되므로 .columns 붙일 것

# 원핫 인코딩
train = pd.get_dummies(train, columns=cols)
test = pd.get_dummies(test, columns=cols)
```

# 4. 검증 데이터 분리
```python
from sklearn.model_selection import train_test_split

#=> train_test_split(데이터1, 데이터2, 검증데이터 사이즈, random_state)
X_tr, X_val, y_tr, y_val = train_test_split(train.drop('charges', axis=1), train['charges'], test_size=0.15, random_state=2022)

X_tr.shape, X_val.shape, y_tr.shape, y_val.shape
```

# 5. 모델 선택/훈련/평가/최적화
- rmse 함수 정의
```python
from sklearn.metrics import mean_squared_error
import numpy as np

# mse를 구한뒤 루트 씌워서 rmse 구하는 함수 만들기
def rmse(y_test, pred):
    return np.sqrt(mean_squared_error(y_test, pred))
```

- 여러 모델로 실행해보고 오류값이 적은 모델 찾기
```python
# LinearRegression
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_tr, y_tr)
pred = model.predict(X_val)
rmse(y_val, pred) #=> 학습한 결과인 pred를 y_val에 적용

# RandomForestRegressor
from sklearn.ensemble import RandomForestRegressor
model = RandomForestRegressor()
model.fit(X_tr, y_tr)
pred = model.predict(X_val)
rmse(y_val, pred)

# xgboost Regressor
#=> xgboost의 경우 상황에 따라 경고가 발생할 수도 있음(파라미터에 대한 공부 필요)
from xgboost import XGBRegressor
model = XGBRegressor(objective='reg:squarederror') 

model = RandomForestRegressor()
model.fit(X_tr, y_tr)
pred = model.predict(X_val)
rmse(y_val, pred)
```

- 더 정확한 값을 찾기 위해 scaler 적용(구해놓은 베이스라인 값 주석으로 저장해놓기)
    - StandardScaler
    - MinMaxScaler

# 6. 예측

```python
pred = model.predict(test)
```

# 7. csv 생성 및 제출
- 문제에서 요구한 `id`와 예측값 이용한 데이터프레임 생성
```python
sumbit = (
    {
        'id': test['id'],
        'charges': pred
    }
)

submit.to_csv('0000.csv', index=False) #=> index=False로 필요없는 인덱스 포함되지 않게 만들기
```
