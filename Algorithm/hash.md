# 개념
- dictionary 처럼 `key:검색어`와 `value:검색결과`를 갖는 하나의 ***자료구조***
- `string` 기반으로 정보 기록 및 관리 시 사용
- `hash`/`hash function`/`hashing`/`hash table`의 개념으로 나뉨
- `hash function`: `key`를 고정된 길이의 `hash`로 변환
- `hashing`: 해시 함수에서 `key`값을 `hash`로 변환하는 과정
- `hash table`: 연관 배열구조를 이용하여 데이터를 `key`와 `value`로 저장하는 자료구조 => ???hash와 hash table 개념차이???

# 장점
- `List` 자료형의 경우 `index`는 숫자만 가능하지만 `hash`는 모든 자료형을 `index`로 사용할 수 있음
- `hash`사용시 `List`에 비해 많은 데이터에서 원하는 데이터를 찾기 쉬움 => 연산이 빠름
- 중복 제거 가능

# 단점
- 공간복잡도가 커짐
- 충돌 발생 우려 있음 => 충돌: 해싱한 값이 중복인 경우
- 순서가 있는 배열과 어울리지 않음

# 사용방법 
```python
# 해시맵에 키-밸류 데이터 넣을 때
HashMap.put('key', 'value')

# 키에 해당하는 값을 불러올 때(키에 해당하는 밸류 없을시 에러)
HashMap.get('key') 

# 해당 값이 없을 때 false 값 반환
HashMap.getOrDefaule('key', false)
```