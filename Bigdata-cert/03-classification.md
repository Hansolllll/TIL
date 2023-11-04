INDEX
0. 데이터 전처리 및 분리
1. 분류 모델 선택
2. 검증용 데이터 분리
    1. 의사결정나무
    2. 랜덤포레스트
    3. XGBoost
3. 평가
---
# 0. 데이터 전처리 및 분리
- 데이터 불러오기
- 데이터 크기 확인
- 타겟 컬럼 및 수 확인
    - `y_train.head()` 작성시 출력되는 컬럼
    - `y_train['타겟컬럼'].value_counts()`
- 데이터 타입 확인 후 수치형 데이터 `cols`에 묶기
- `cols` 결측값 확인 후 간단한 결측치 처리
    - ex) `0` 채우기
- y_train에서 조건에 맞는 데이터들을 정수형으로 변경
```python
y = (y_train['income'] == '>50K').astype(int)
```
# 1. 머신러닝 모델
- 모델 선택(의사결정나무, 랜덤포레스트, XGBoost)
```python
# 랜덤포레스트 분류 모델 import
from sklearn.ensemble import RandomForestClassifier
# rf 변수에 지정
rf = RandomForestClassifier()
# train데이터로 훈련 
rf.fit(X_train[cols], y)
# test데이터로 예측
pred = rf.predict(X_test[cols])
```
- 예측 후 csv파일 생성
    - index=False 지정 안하면 인덱스가 추가되므로 꼭 제거하기
```python
submit = pd.DataFrame(
        {
            'id': X_test['id'],
            'income':pred
        }
    )
# 수험번호.csv로 저장
submit.to_csv('0000.csv', index=False)
```
# 2. 검증용 데이터 분리
- 수험생이 평가를 해볼 수 없으므로 훈련용 데이터에서 검증용을 분리해 직접 검증
- roc_auc_score가 가장 높은 모델 선택해 예측한 후 csv파일 생성
```python
# 훈련용데이터와 검증용데이터를 분리할 수 있는 라이브러리
from sklearn.model_selection import train_test_split 

# 데이터 분리 전 범주형 -> 수치형으로 변환
y = (y_train['income'] == '>50K').astype(int)

# test_size는 검증용데이터의 크기, random_state는 동일하게 분리하기 위해 지정(아무 숫자나 가능)
X_tr, X_val, y_tr, y_val = train_test_split(X_train, y, test_size=0.1, random_state=0) 
```
## 2-1. 랜덤포레스트
```python
from sklearn.ensemble import RandomForestClassifier
# 정확성 검증 위해 roc_auc_score import
from sklearn.metrics import roc_auc_score
rf = RandomForestClassifier()
# X_tr과 y_tr로 훈련
rf.fit(X_tr[cols], y_tr)
# X_val 넣어서 검증
pred = rf.predict_proba(X_val[cols])
# 정확도 확인
roc_auc_score(y_val,pred[:, 1])
```
## 2-2. 의사결정나무
```python
from sklearn.tree import DecisionTreeClassifier
dt = DecisionTreeClassifier()
dt.fit(X_tr[cols], y_tr)
pred = dt.predict_proba(X_val[cols])
# 정확도 확인
roc_auc_score(y_val,pred[:, 1])
```
## 2-3. XGBoost 
```python
from xgboost import XGBClassifier
xgb = XGBClassifier()
xgb.fit(X_tr[cols], y_tr)
pred = xgb.predict_proba(X_val[cols])
# 정확도 확인
roc_auc_score(y_val,pred[:, 1])
```

# 3. 평가
- 아래 코드로 평가가 이루어짐(수험자가 확인해볼 순 없음)
```python
from sklearn.metrics import roc_auc_score
y_test = pd.read_csv("y_test.csv")
ans = (y_test['income'] != '<=50K').astype(int)
roc_auc_score(ans, pred[:,1])
```