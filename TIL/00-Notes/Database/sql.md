## SQL
### 특징

  - SQL 문장 끝에는 반드시 ; (세미클론)을 작성해줘야 한다.

<br/>

  - 띄어쓰기나 줄바꿈 또한 명령어 수행에 영향을 주지 않는다

<br/>

  - SQL 문자에는 대소문자 구분하지 않는다



    - 데이터베이스에 저장되는 테이블와 컬럼의 정보는 전부 대문자로 저장된다


    - SQL 문장도 대문자로 작성하는게 일반적이다

<br/>
<br/>
<br/>

---
## SELECT문
```sql
SELECT [ALL/ DISTINCT] 컬럼명 [AS 별칭] FROM 테이블명 ;
```
- [] 있는 것들은 생략 가능
- ALL 
  - 기본값 
  - 입력 안할시 ALL로 작동 
- DISTINCT 
  - 중복을 제거하는 키워드
- SELECT 컬럼
  - 조회하고자 하는 "컬럼의 정보"
- SELECT *
  - 모든 컬럼 조회
- FROM 테이블
  - 데이터를 가져올 "테이블의 정보"
- SELECT 컬럼명 AS 별칭
  - 컬럼에 별칭을 적용 하여 출력
  - 별칭에 특수문자를 적용시키고 싶으면 별칭에 ""(쌍따움표)를 감싸줘야 함

<br/>
<br/>
<br/>


### 정석 SQL 문장
``` sql
SELECT EMPLOYEE_ID  
     , FIRST_NAME  
     , EMAIL  
     , PHONE_NUMBER  
     , SALARY
  FROM EMPLOYEES ;  
```


<br/>

<br/>

<br/>

---

## order by 절
### 개념
- 특정 컬럼을 기준으로 정렬화
- SQL문에서 가장 마지막에 작성되고 가장 마지막에 실행된다
- 별도로 정렬 방식을 지정하지 않으면 기본값은 ASC이다

<br/>
<br/>
<br/>

### 사용법
```sql
SELECT "컬럼의 정보"  
FROM " 테이블의 정보"  
ORDER BY  "정렬화할 컬럼" [ASC/DESC] ;
```
<br/>

- ASC(Ascending) : 오름차순 정렬 (기본값)
- DESC(Descending) : 내림차순 정렬

<br/>
<br/>
<br/>

## WHERE절
### 개념
- 조건절

<br/>

### 사용법
```sql
SELECT "컬럼의 정보"  
FROM   "테이블의 정보"  
WHERE  원하는 행(데이터)을 선별하기 위한 "조건 식" ; 
```
<br/>
<br/>
<br/>

### 비교연산자
- `=`: 같다
- `>` : 보다 크다(초과)
- `>=` : 크거나 같다(이상)
- `<` : 보다 작다(미만)
- `<=` : 작거나 같다(이하)

<br/>
<br/>
<br/>

### 부정 비교 연산자

- = : 같다
- !=, <>, ^= : 같지 않다
- NOT A = B : 같지 않다

<br/>
<br/>
<br/>

### 논리 연산자
- AND : 조건 모두 만족해야만 TRUE값을 반환해주는 논리 연산자
- OR : 하나의 조건이라도 만족하면 TRUE 값을 반환해주는 논리 연산자

<br/>
<br/>
<br/>

### SQL 연산자
|연산자|연사자의미|
|-----|----------|
|IS NULL|NULL 값인 경우를 의미한다|
|IN(LIST)|리스트에 있는 값 중에서 어느 하나라도 일치한다|
|BETWEEN A AND B|a 와 b의 값 사이의 값을 갖는다(a이상 b이하)|
|LIKE "비교문자열"|비교문자열과 형태가 일치한다(% _ 사용)|

<br/>
<br/>
<br/>

### IS NULL 연산자
- 데이터 값이 NULL인 값을 조회하여 가져온다
```sql
WHERE 컬럼명 IS NULL
```
  - 해당 컬럼의 데이터 값이 NULL 인 값 조회
```sql
WHERE 컬럼명 IS NOT NULL
```
  - 해당 컬럼의 데이터에서 NULL이 아닌 값을 조회


<br/>
<br/>
<br/>

### IN 연산자
- 특정컬럼에 포함된 데이터를 여러 개 조회할 때 활용한다
```sql
WHERE 컬럼명 IN (데이터1, 데이터2, ... 데이터N)
```  
  - 컬럼명에서 데이터1,데이터2,데이터N이 있는 값을 조회한다
 ```sql
 WHERE 컬럼명 NOT IN (데이터1, 데이터2, .. 데이터N)
 ```
  - 컬럼명에서 데이터1,데이터2,데이터N이 없는 값을 조회한다


<br/>
<br/>
<br/>

### BETWEEN 연산자
- 일정 범위 내의 데이터를 조회하는 연산자
- A 이상 B 이하 의 범위 의 값을 가져온다
  ```sql
  WHERE 컬럼명 BETWEEN A AND B
  ```

  <br/>
  <br/>
  <br/>

### LIKE 연산자
- 일부 문자열이 포함된 데이터를 조회할 때 사용
- 와일드카드를 이용해 매칭 연산을 진행한다

<br/>

#### 와일드카드 종류
- % : 길이와 상관 없이 모든 문자 데이터를 의미하는 특수문자
- _ : 어떤 값이든 상관 없이 한 개의 문자 데이터를 의미하는 특수 문자

<br/>

#### %
- 길이와 상관 없이 모든 문자 데이터를 의미하는 특수문자

<br/>

```sql
WHERE 컬럼명 LIKE 'S%'
```
S로 시작하느 모든 데이터 검색
```sql
WHERE 컬럼명 LIKE '%S'
```
S로 끝나는 모든 데이터 검색
```sql
WHERE 컬럼명 LIKE '%S%'
```
S가 포함된 모든 데이터 검색

<br/>

#### _
- 어떤 값이든 상관 없이 한 개의 문자 데이터를 의미하는 특수 문자

<br/>

```sql
WHERE 컬럼명 LIKE 'S__'
```
S로 시작하고 총 3글자인 모든 데이터 검색
```sql
WHERE 컬럼명 LIKE `___S'
```
S로 끝나고 총 4글자인 모든 데이터 검색

<br/>
<br/>
<br/>

### 연산자의 우선 순위
|연산자 우선순위|설명|
|---------|--------|
|1|괄호()|
|2|비교 연산자, SQL 연산자|
|3|NOT 연산자|
|4|AND|
|5|OR|

<br/>
<br/>
<br/>

## SQL 문장의 종류

### DDL(Data Definition Language)
- 데이터 정의어
- 테이블 같은 데이터 구조를 정의하는 언어
- 특정 구조를 생성, 변경, 삭제, 이름을 바꾸는 명령어들이 있음
- CREATE, ALTER, DROP, TRUNCATE, RENAME

<br/>

### DML(Data Manipulation Language)
- 데이터 조작어
- DB에 저장된 자료들을 입력, 수정, 삭제, 조회하는 언어
- SELECT, INSERT, UPDATE, DELETE

<br/>

### DCL(Data Control Language)
- 데이터 제어어
- DB관리자가 데이터 보안, 무결성 유지, 병행 제어, 회복을 위해 사용하는 언어
- GRANT, REVOKE, ROLE, COMMIT, ROLLBACK, SAVEPOINT
  - COMMIT, ROLLBACK, SAVEPOINT는 TCL로 구분하기도 함

<br/>

### TCL(Transaction Control Language)
- 트랜젝션 제어어
- 트랜잭션을 제어하는 언어
- COMMIT, ROLLBACK, SAVEPOINT