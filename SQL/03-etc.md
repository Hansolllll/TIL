INDEX
1. SELECT/ALIAS
    1. SELECT 
    2. ALIAS
2. WHERE
    1. LIMIN
    2. IN
    3. LIKE
    4. BETWEEN
3. ORDER BY
4. AGGREGATION FUNCTION
    1. COUNT
    2. SUM
    3. AVG
    4. MIN/MAX
5. GROUP BY
6. HAVING
---
# 1. SELECT/ALIAS
## 1-1 `select` 
- 데이터베이스 내의 데이터 선택시 사용
- `select` 뒤에 오는 컬럼 선택 
- `*`를 이용해서 전체 선택 가능
- `distinct`로 중복 값 제거 가능
- 사용 예시
```sql
-- 전체 선택 
select * from 테이블명;

-- 컬럼의 값만 선택
select 컬럼명 from 테이블명;

-- 중복된 값을 제거한 결과 
select distinct 컬럼명 from 테이블명;

-- 중복이 제거된 값의 개수 
select count(distinct 컬럼명) from 테이블명; 
```

## 1-2. `alias`
- 별칭
- 테이블이나 컬럼의 이름에 별칭 지정 가능
- `as`를 사용하며 영어와 달리 한글은 `''` 내에 기입
- `as` 생략가능 
- 사용 예시
```sql
select 컬럼명  as 별칭 from 테이블명;
```

# 2. WHERE
- 조건절 
- 여러개의 조건절 사용 가능 (and와 or로 연결)
    - and : 모두 true인 것만 반환
    - or : 하나라도 true인 것을 반환
- `limit`, `in`,`like`,`between`과 함께 사용 가능
- 사용 예시 
```sql
-- 기본
select 컬럼명 from 테이블명 where 조건;

-- 다중 조건
select 컬럼명 from 테이블명 where 조건1 and 조건2;
select 컬럼명 from 테이블명 where 조건1 or 조건2;
```

## 2-1 `limit`
- 반한하는 데이터의 수 제한
- 많은 데이터의 일부 조회시 유용
- ***limit 건수제한***: 표시한 건수만큼만 반환
- ***limit offset, 건수제한***: offset만큼 건너뛰고 표시한 건수만큼만 반환
- 사용 예시
```sql
select * from 테이블명 limit 건수;
select * from 테이블명 where 조건 limit 건수;
```

## 2-2 `in`
- or 연산과 같은 의미
- `in` 뒤에 나열된 항목중 하나라도 true면 선택
- 사용 예시
```sql
-- 컬럼의 값이 1이거나, 2거나, 3인 데이터 선택
select * from 테이블명 where 컬럼 in (값1, 값2, 값3)

select * from 테이블명 where 컬럼 = 값1 or 컬럼= 값2 or 컬럼 = 값3;
```

## 2-3 `like`
- 특정 문자열 검색시 사용 
- `_`와 `%` 가 있음 
     - `_` : 기호 하나당 문자 한개 의미
     - `%` : 문자 길이 가변
- `_`와 `%`를 문자로 검색하고 싶을 뗀 `escape` 사용
    - 아무 특수문자를 `_`나 `%` 앞에 붙이고 문장끝에 *escape '특수문자'* 입력
- 사용 예시
```sql
-- 값으로 시작하거나 끝나는 데이터 선택(글자수 제한 없음)
select * from 테이블명 where 컬럼 like '%값'
select * from 테이블명 where 컬럼 like '값%' 

-- 값으로 시작하거나 끝나는 데이터 선택(글자수 제한 있음)
select * from 테이블명 where 컬럼 like '_값'
select * from 테이블명 where 컬럼 like '값_'

-- %나 _를 문자로 검색시 
-- escape 사용
select 컬럼명 from 테이블명 where 컬럼 '%#_%' escape '#';
``` 

## 2-4 `between`
- 범위 내의 값을 가진 데이터 조회시 사용
- 작은 수를 앞에 입력
- `between` 앞 뒤에 적힌 값도 포함(이상, 이하 개념)

# 3. `ORDER BY`
- 뒤에 입력되는 컬럼을 기준으로 테이블의 데이터를 정렬
- 정렬 기준이 되는 컬럼을 `select`절에 명시하지 않아도 됨
- 다중 컬럼 선택 가능(,로 연결, 앞 컬럼이 우선순위)
- 실행 순서중 가장 마지막 
    - select, from, where, group by, having, select, order by
- `asc`, `desc`
    - `asc`: 오름차순, 기본값, 생략가능
    - `desc`: 내림차순
- 사용 에시
```sql
select 컬럼1, 컬럼2 from 테이블명 order by 컬럼3;

-- 다중 컬럼을 기준으로 선택 
select * from 테이블명 order by 컬럼1 asc, 컬럼2 desc;
```

# 4. `AGGREGATION FUNCTION`(집계함수)
- 여러 행에 대한 데이터를 받아 하나의 값으로 반환
- where 조건절에 쓰일 수 있음 
- `count`, `sum`, `avg`, `min`, `max`가 있으며 `group by`와 잘 쓰임

## 4-1. `count`
- 데이터의 건수 반환
- `count(*)`와 `count(1)`은 같은 의미
- `count(컬럼)`은 데이터 중 null 값 제외 

## 4-2. `sum`
- 데이터의 합계 반환
- null 값 제외하고 계산

## 4-3. `avg`
- 데이터의 평균 반환
- null 값 제외하고 계산

## 4-4. `min`, `max`
- 데이터의 최솟값, 최댓값 반환
- null 값 제외

```sql
-- 전체데이터, 컬럼1, 컬럼2의 건수 
select count(*), count(컬럼1), count(컬럼2) from 테이블명;

-- 컬럼의 합계, 평균, 최솟값, 최댓값 
select sum(컬럼명), avg(컬럼명), min(컬럼명), max(컬럼명) from 테이블명;
```

# 5. `GROUP BY`
- 뒤에오는 컬럼을 기준으로 묶기
- `group by` 기준 컬럼 외엔 `select`절에 올 수 없음
- 보통 `group by`로 묶은 컬럼을 앞에 두고, 뒤에 확인할 집계함수를 입력 
- 다중 컬럼 사용 가능(앞의 컬럼이 우선순위)
- 사용 예시
```sql
select 컬럼1, 컬럼2, count(*) from 테이블명 group by 컬럼1, 컬럼2;

select 컬럼1, 컬럼2, avg(컬럼4) from 테이블명 where 조건 group by 컬럼1, 컬럼2;
```

# 6. `HAVING`
- `group by`와 `order by` 사이에 입력
- `group by`에 대한 집계를 조건으로 넣고 싶으면 `having`, 일반 조건은 `where`에 입력(결과는 나오지만 실행 순서를 고려해 효율적인 작업 가능)
- 사용 예시
```sql
select 컬럼1, count(*) from 테이블명 where 조건 group by 컬럼1 having (count(*)에 대한 조건) order by count(*); 
```