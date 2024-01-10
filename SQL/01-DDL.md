INDEX
0. DDL
1. CREATE
2. ALTER
3. DROP_TRUNCATE

---
# 0. DDL(Data Definition Language)
- 데이터 정의어
- 데이터 구조와 관련되며 `CREATE`, `ALTER`, `DROP`, `TRUNCATE`가 있음
- 구조 변경후 자동으로 저장하는 `auto commit` 가능 

# 1. CREATE
- 데이터베이스에 ***테이블 생성***
- 테이블 생성시, 테이블명, 컬럼명, 데이터타입, 사이즈, not null 등을 정의
    - 테이블명
        - 테이블명은 숫자로 시작할 수 없음
        - 테이블명엔 `_`, `$` 외의 특수문자 사용 불가

    - 데이터타입
        - `CHAR` : 고정된 길이의 문자열 데이터
        - `VARCHAR` : 가변 길이의 문자열 데이터
        - `INT` : 수치형 데이터
        - `DATE` : 날짜 데이터

    - 사이즈 
        - `CHAR` : 고정된 크기 
        - `VARCHAR` : 입력가능한 최대 크기

    - not null 
        - null 허용이 default
        - 데이터 타입 뒤에 `not null` 붙여서 지정 

- 작성 예시        
```sql
-- 테이블 생성
create table 테이블명(
    컬럼1 varchar(16) not null,
    컬럼2 varchar(50),
    컬럼3 date,
    컬럼4 int not null);

-- 데이터 넣기(컬럼과 넣을 데이터 순서가 일치하는 적합한 데이터여야함)
insert into 테이블 values(값1, 값2, 값3, 값4);

-- 여러개의 데이터 한번에 넣기 
insert into 테이블 values
(값1, 값2, 값3, 값4),
(값5, 값6, 값7, 값8);

-- 선택한 컬럼에만 값 넣기(not null 컬럼 주의) 
insert into 테이블명 (컬럼명1, 컬럼명2) values (값1, 값2);

-- 테이블 전체 조회
select * from 테이블명;
```

# 2. ALTER
- 테이블의 구조 변경
- 가능한 작업
    - `CHANGE` : 컬럼명 변경 
    - `MODIFY` : 데이터 타입 및 사이즈 변경
    - `ADD` : 컬럼 추가
    - `DROP` : 컬럼 삭제
    - `RENAME` : 테이블명 변경
- 작성 예시
```sql
-- 컬럼 추가 
alter table 테이블명 add column 컬럼명 데이터타입 및 크기;

-- 컬럼 속성 바꾸기 
alter table 테이블명 modify column 컬럼명 바꿀데이터타입 및 크기;

-- 컬럼명 변경
alter table 테이블명 chage column 기존컬럼명 바꿀컬럼명 데이터타입 및 크기;

-- 컬럼 삭제
alter table 테이블명 drop column 컬럼명;

-- 테이블명 변경
alter table 기존테이블명 rename 바꿀테이블명;
```
# 3. DROP_TRUNCATE
- 테이블 삭제
- `DROP` 
    - 테이블과 데이터 모두 삭제
    - `rollback` 불가
- `TRUNCATE`
    - 테이블은 남고, 데이터만 삭제
    - 행선택 불가능
    - `rollback` 불가
    - 남김없이 지우기때문에 속도 빠름(대용량 데이터 적합)
- 사용 예시
```sql
-- 테이블 내부 데이터 삭제(truncate)
truncate table 테이블명;

-- 테이블 삭제(drop)
drop table 테이블명;
```