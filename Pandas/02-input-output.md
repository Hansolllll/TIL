# INDEX
1. CSV
    1. 불러오기
    2. 저장하기

---
# 1. CSV(Comma Seperated Values)
- 열 사이를 쉼표(,)로 구분
- 대부분의 데이터 파일은 csv 형태
- TSV(Tab Seperated Values): tab으로 열 구분

## 1-1. 불러오기
- 기본형
```python
변수명 = pd.read_csv('파일명.csv')
```

- 끊어서 불러오기
    - 데이터의 크기가 매우 큰 경우 사용
    - chunksize를 지정하고 그 크기만큼 끊어서 불러옴
```python
변수명 = pd.read_csv('파일명.csv', chunksize = 사이즈지정)
```

## 1-2. 저장
```python
변수명 = pd.to_csv('파일명.csv', index=False)
```
- `index = False`를 안넣으면 인덱스를 또 다른 인덱스로 저장함