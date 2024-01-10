INDEX
0. DML
1. INSERT
2. UPDATE
3. DELETE
---
# 0. DML(Date Manipulation Language)
- 데이터 조작어 
- 데이터베이스를 실질적으로 처리하는데 사용
- `INSERT`, `UPDATE`, `DELETE` 가 있으며 셋 다 `rollback` 가능
    - `rollback` : 데이터를 가장 마지막에 `commit`한 지점으로 되돌림 
- 명령어 작성 후 maual로 `commit` 해야 저장됨(python에서 변수 할당하듯이)

# 1. INSERT

- 테이블에 값 넣기(지정된 데이터타입 및 크기에 적합해야함)
- 전체 컬럼 또는 선택한 컬럼에만 값을 넣을 수 있음
- 사용 예시
```sql
-- 모든 컬럼에 값 넣는 경우
insert into 테이블명 values (값1, 값2, 값3, 값4);

-- 선택한 컬럼에 값 넣는 경우(not null 설정한 컬럼에 값 꼭 넣기)
-- 데이터 컬럼에 변동이 잦은 실무에서는 이 방법을 더 많이 씀
insert into 테이블명 (컬럼1, 컬럼2) values (값1, 값2);
```

# 2. UPDATE
- 테이블의 데이터를 수정
- `set`과 함께 사용
- 조건절 사용 필수(조건절이 없으면 모든 데이터가 수정됨)
- 사용 예시
```sql
update 테이블명 set 컬럼명 = 값 where 조건;  
```

# 3. DELETE
- 테이블의 데이터를 삭제(테이블은 남기고 데이터만 삭제)
- 조건절 사용 필수(조건절 없으면 모든 데이터 삭제됨)
- 행단위로 데이터를 지움(컬럼 선택 불가)
- 사용 예시
```sql
delete from 테이블명 where 조건;

-- 행 중에서 특정 컬럼만 비우고 싶다면 
-- delete가 아닌 update 사용
update 테이블명 set 컬럼명 = null where 조건
```
