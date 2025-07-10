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

<br/>
<br/>
<br/>

---

## DDL((Data Definition Language): 데이터 정의어
### 개념
- 테이블 같은 데이터 구조를 정의 하는 언어
- 특정 구조를 생성, 변경, 삭제, 이름을 바꾸는 명령어들로 궁성 되었있음

<br/>

### 명령어 종류
- CREATE : 테이블, USER 같은 객체를 생성하는 명령어
- ALTER : 테이블, USER(계정) 같은 객체를 변경하는 명령어
- DROP : 테이블, USER(계정) 같은 객체를 삭제하는 명령어
- TRUNCATE : 테이블 안에 있는 데이터를 영구 삭제하는 명령어
- RENAME : 테이블의 이름을 변경하는 명령어

<br/>
<br/>
<br/>

### CREATE
- 계정 생성
```sql
CREATE USER 계정(USER)이름 ;
```
- 테이블 생성
```
CREATE TABLE 테이블이름 ;
테이블 생성
```

- 테이블 복사
```sql
CREATE TABLE 테이블 명 
AS 해당 데이터의 내용이 들어있는 쿼리문 ;
```
  - 해당 쿼리문의 데이터만 복사가 된다
  - 제약 조건은 복사가 되지 않는다
<br/>
<br/>
<br/>

### ALTER
- 제약조건 추가
```sql
ALTER TABLE  테이블이름
ADD CONSTRAINT 제약조건이름 제약조건(해당컬럼) ;
```
- 제약조건 삭제
```sql
ALTER TABLE 테이블이름
DROP CONSTRAINT 제약조건이름 ;
```
- 제약조건 변경
```sql
TABLE 테이블명
MODIFY 컬럼 제약조건 ;
```
- 테이블의 컬럼 추가
```sql
ALTER TABLE 테이블명
ADD 추가할컬럼명 데이터타입 ;
```
- 테이블 컬럼 이름 변경
```sql
ALTER TABLE 테이블명
RENAME COLUMN 변경할컬럼
TO 변경할이름 ;
```
- 컬럼의 자료형 변경
```sql
ALTER TABLE 테이블
MODIFY 변경할컬럼 변경할자료형 ;
```
- 컬럼 삭제
```sql
ALTER TABLE 테이블
DROP COLUMN 삭제할컬럼 ;
```
<br/>
<br/>
<br/>

### DROP
- 테이블 삭제
```sql
DROP TABLE 테이블명 ;
```

<br/>
<br/>
<br/>

### TRUNCATE
- 데이터 삭제
```sql
TRUNCATE TABLE 테이블이름 ;
```
- TRUNCATE 와 DELETE
  - TRUNCATE : 데이터를 영구 삭제하는 명령어 > DDL이기 때문에 복구가 불가능하다
  - DELETE : 데이터를 삭제하는 명령어 > DML이기 때문에 복구가 가능하다(복구 명령어 ROLLBACK)

<br/>
<br/>
<br/>

### RENAME
- 테이블 이름 변경
```sql
RENAME 테이블
TO 변경할이름 ;
```
<br/>
<br/>
<br/>

---
## DML(Data Manipulation Language) : 데이터 조작어
### 개념
- 데이터베이스에 있는 데이터를 수정, 삭제, 추가 할때 사용하는 명령어

<br/>

### 명령어 종류
- SELECT : 데이터 조회
- INSERT : 데이터 삽입
- UPDATE : 데이터 수정
- DELETE : 데이터 삭제

<br/>
<br/>
<br/>


### SELECT
- 데이터 조회
```sql
SELECT 조회할컬럼
FROM 해당컬럼이있는테이블 ;
```
  - 컬럼자리에 *을 쓰면 모든 컬럼 조회

<br/>
<br/>
<br/>


### INSERT
- 데이터 추가
```sql
--방법1
INSERT INTO 테이블 (컬럼1, 컬럼2, 컬럼3)
VALUES (값1, 값2, 값3) ;

--방법2
INSERT INTO 테이블 VALUES (값1,값2,값3)
```
- 주의점
  - INSERT INTO에 입력한 컬럼 리스트와 VALUES에 입력한 실제 값은 1:1 매핑이 되어진다 그래서 순서와 자료형을 맞게 써줘야 한다
  - 컬럼 리스트를 생략 가능 단 VALUES에는 해당 테이블의 컬럼 리스트에 모든 순서와 자료형에 맞춰서 전부 써줘야 한다
  - 값이 문자형이면 ''필요 ex) '값1'

<br/>
<br/>
<br/>


### UPDATE
- 데이터 변경
```sql
UPDATE 테이블명
SET 변경할내용
WHERE 데이터를 변경할 대상행을 선별하기 위한 조건식 ;

```

<br/>
<br/>
<br/>

### DELETE
- 데이터 삭제
```sql
DELETE FROM 테이블이름
WHERE 삭제할 대상 행을 선별하기 위한 조건식 ;
```
  - ROLLBACK ; 으로 복구가능

<br/>
<br/>
<br/>

---
## DCL(Data Contril Language): 데이터 제어어
### 개념
- 데이터 베이스에 접근하거나 객체에 권한을 주는 드읭 역할을 하는 언어

<br/>

### 명령어 종류
- GRANT : 권한을 주는 명령어
- REVOKE : 권한을 회수하는 명령어
- ROLE : 권한을 묶어서 주는 명령어

<br/>
<br/>
<br/>

### GRANT
- 권한 부여
```sql
GRANT 시스템권한
TO 계정 ;
```
- 권한 회수
```sql
REVOKE 시스템 권한
FROM 계정 ;
```

<br/>

<br/>
<br/>

---
## TCL(Transaction Control Language) : 트랜잭션 제어어
### 개념
트랜잭션이란 데이터 베이스 상태를 변환 시키기 위해서 수행하는 최소 수행 단위 즉 업무를 처리하기 위한 최소 수행 단위

<br/>


### 특징
- 원자성(Atomicity) : All or Nothing 모두 실행되거나 전혀 실행 되지 않거나
- 일관성(Consistency) : 언제나 일관성 있는 상태를 유지 하는 것
- 고립성(Isolation) : 트랜잭션 실행 시 다른 트랜잭션의 영향을 받지 않는다.
-  지속성(Durability) : 성공적으로 수행된 트랜잭션은 영원히 반영이 되야 한다.

<br/>

### 명령어 종류
- COMMIT : 영구 저장하는 명령어
- ROLLBACK : 되돌리는 명령어
- SAVEPOINT : 중간 저장하는 명령어

