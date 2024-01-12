INDEX
1. JOIN
    1. INNER JOIN
    2. OUTER JOIN 
2. CASE WHEN
3. SUBQUERY
    1. SCALAR SUBQUERY
    2. INLINE VIEW
    3. NESTED SUBQUERY
4. UNION & UNION ALL
    1. UNION 
    2. UNION ALL 
5. ROLLUP
6. WINDOW FUNCTION
---

# 1. `JOIN`
- 두 개의 테이블을 하나로 묶음 
- `INNER JOIN`, `OUTER JOIN`, `CROSS JOIN`, `SELF JOIN`이 있음 
- 두 테이블에 같은 컬럼이 있으면 어떤 테이블의 컬럼인지 `.`앞에 적어줘야함
- `alias` 지정시 on절에서 사용해야함  
![sql join](./../assets/sqljoin.jpeg)

## 1-1 `INNER JOIN`
- 교집합에 해당(두 테이블에서 공통된 데이터만 반환)
- `inner join`이 아닌 `join`으로 입력해도 정상 작동 
- join 조건관 filtering 조건을 and로 연결해 where절에 명시 가능 
- 사용 예시 
```sql
-- 표준방식 
select 별칭1.컬럼명1, 별칭1.컬럼명2 from 테이블1 별칭1 inner join 테이블명2 별칭2 on 별칭1.컬럼명1 = 별칭2.컬럼명2;

-- 실무방식
select 별칭1.컬럼명1 from 테이블1 별칭1, 테이블2 별칭2 where 별칭1.컬럼명1 = 별칭2.컬럼명1;

-- join 조건과 filtering 조건 함께 사용 
select 별칭1.컬럼명 from 테이블1 별칭1, 테이블2 별칭2 where 별칭1.컬럼명1 = 별칭2.컬럼명1 and 조건 
```

## 1-2 `OUTER JOIN`
- 데이터가 있는 테이블을 기준으로 데이터가 없는 테이블에서 매치되는 데이터를 가져오는 방법
- 기준에 따라 `left outer join`과 `right outer join`으로 나뉨
- 사용 예시 
```sql
-- left outer join
select * from 테이블1 별칭1 left outer join 테이블2 별칭2 on 별칭1.컬럼명1 = 별칭2.컬럼명2;

-- left outer join + where 이용해 inner join 결과 도출 
select * from 테이블1 별칭1 right outer join 테이블2 별칭2 on 별칭1.컬럼명1 = 별칭2.컬럼명1 where 별칭2.컬럼명1 is not null;

-- right outer join
select * from 테이블1 별칭1 right outer join 테이블2 별칭2 on 별칭1.컬럼명1 = 별칭2.컬럼명1;
```

# 2. `CASE WHEN`
- select절에 사용되며 `if then else`와 유사
- 단순케이스 문법식과 검색케이스 문법식이 있음 
    - 단순케이스 문법식 : equal 조건식만 가능 
    - 검색케이스 문법식 : 범위조건 가능 
- 마지막 else 생략시 그 외의 값들은 null로 반환 
- 사용 예시 
```sql 
-- 단순케이스 문법식 
select 컬럼1, case 컬럼2 when 값1 then 값2 when 값3 then 값4 else 값5 end as 별칭 from 테이블명;

-- 검색케이스 문법식 
-- 범위 조건 적용 가능(다중범위도 가능: 앞에 있는 범위가 우선순위 가짐) 
select 컬럼1, case when 컬럼2 = 값1 then 값2 when 컬럼2 = 값2 then 값3 else 값4 end as 별칭 from 테이블1;
```
