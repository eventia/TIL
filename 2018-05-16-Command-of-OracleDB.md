jsp/spring 학습시 필요한 oracle db (sqlplus) 의 기본명령어들
=========================================

설치 후 첫실행
--------------

### 관리자계정접속
<pre>
> sqlplus system/oracle
</pre>

### 사용자계정생성
<pre>
SQL> create user scott identified by "tiger";
</pre>
"tiger" 란 비밀번호를 가진 scott 란 ID 를  만든다.

### 인증
<pre>
SQL> grant connect, resource to scott;
</pre>

### 종료
<pre>
SQL> exit
</pre>

### 사용자계정접속
<pre>
> sqlplus scott/tiger
</pre>

### 테이블생성
<pre>
SQL> create table TABLENAME (COL1NAME TYPE1(size), COL2NAME TYPE2(size));
SQL> create table member (id varchar2(20) primary key, pw varchar2(20), name varchar2(20), phone VARCHAR2(20));
SQL> create table mtmember (id varchar2(20) primary key, pw varchar2(20), name varchar2(20));
</pre>

### 테이블검색
<pre>
SQL> select * from tab;
</pre>

### 테이블구조확인
<pre>
SQL>DESC mtmember;
</pre>


### 테이블변경 - 칼럼추가
<pre>
SQL>ALTER TABLE mtmember ADD(phone VARCHAR2(20));
SQL>ALTER TABLE mtmember ADD(memo VARCHAR2(20), memo2 VARCHAR2(20));
</pre>

### 테이블변경 - 칼럼삭제
<pre>
SQL>ALTER TABLE mtmember DROP(memo2);
</pre>

### 테이블삭제
<pre>
SQL>DROP TABLE mtmember;
</pre>

### 레코드추가
<pre>
SQL>INSERT INTO member (id, name, phone, pw)  VALUES ('abc', '김가나', '555-5555', '112' );
SQL>INSERT INTO member (id, name, phone, pw)  VALUES ('aaa', '김안나', '555-5556', '101' );
SQL>INSERT INTO member (id, name, phone, pw)  VALUES ('ba1', '기러기', '555-5557', '201' );
SQL>INSERT INTO member (id, name, phone, pw)  VALUES ('ba2', '갈매기', '555-5558', '202' );
SQL>INSERT INTO member (id, name, phone, pw)  VALUES ('ab1', '최가나', '555-5560', '112' );
SQL>INSERT INTO member (id, name, phone, pw)  VALUES ('aa2', '최안나', '555-5561', '101' );
SQL>INSERT INTO member (id, name, phone, pw)  VALUES ('ba3', '최러기', '555-5562', '201' );
SQL>INSERT INTO member (id, name, phone, pw)  VALUES ('ba4', '최매기', '555-5563', '202' );
</pre>

### 커밋
<pre>
SQL>commit;
</pre>

### 레코드수정
<pre>
SQL>UPDATE member SET name = '한가나' WHERE id = 'abc';
</pre>

### 레코드확인
<pre>
SQL>SELECT * FROM member;
SQL>SELECT id, name FROM member;
SQL>SELECT id FROM member WHERE name='한가나';
</pre>

### 레코드삭제
<pre>
SQL>DELETE FROM member WHERE name = '최러기';
</pre>

### 커밋(여기까지 저장)
<pre>
SQL>commit;
</pre>

<hr/>

## A.계정 관련
### 현재 계정 확인
<pre>
SQL> SHOW USER;
</pre>

#### 모든 계정 확인
<pre>
SQL>SELECT * FROM all_users;
</pre>

### 다른 계정으로
<pre>
SQL>conn scott1/tiger;
SQL>conn scott/tiger;
SQL>conn testuser/testuser@coreDB;
</pre>

#### 비밀번호변경
<pre>
SQL>connect system/oracle;
SQL>ALTER USER scott1 IDENTIFIED BY "tiger1";
SQL>connect scott1/tiger1;
SQL>connect scott/tiger;
</pre>

#### 계정삭제
<pre>
SQL>connect system/oracle;
SQL>DROP USER scott1;
SQL>DROP USER scott1 CASCADE;
SQL>connect scott/tiger;
</pre>




## B.권한 관련
### 사용자계정에 접속 권한 주기
<pre>
SQL>connect system/oracle;
SQL>GRANT CONNECT, RESOURCE TO scott;
</pre>

### 사용자계정에 접속 권한 취소
<pre>
SQL>connect system/oracle;
SQL>REVOKE CONNECT, RESOURCE FROM scott;
</pre>




## C. 테이블 관련
### 모든 테이블 보기
<pre>
SQL>SELECT * FROM TAB;
</pre>

### 테이블 구조보기
<pre>
SQL>DESC member;
</pre>

### 테이블생성
<pre>

SQL> create table TABLENAME (COL1NAME TYPE1(size), COL2NAME TYPE2(size));
SQL> create table member (id varchar2(20) primary key, pw varchar2(20), name varchar2(20), phone VARCHAR2(20));
SQL> create table mtmember (
        id varchar2(20) primary key, 
        pw varchar2(20), 
        name varchar2(20),
        birthday date,
        studentnum number);
        
</pre>


### 테이블변경 - 칼럼추가
<pre>
SQL>ALTER TABLE mtmember ADD(phone VARCHAR2(20));
SQL>ALTER TABLE mtmember ADD(memo VARCHAR2(20), memo2 VARCHAR2(20));
</pre>

### 테이블변경 - 칼럼삭제
<pre>
SQL>ALTER TABLE mtmember DROP(memo2);
</pre>

### 테이블삭제
<pre>
SQL>DROP TABLE mtmember;
</pre>





## D. 입출력
### 레코드추가
<pre>
SQL>INSERT INTO member (id, name, phone, pw)  VALUES ('abc', '김가나', '555-5555', '112' );
</pre>

### 커밋
<pre>
SQL>commit;
</pre>

### 레코드수정
<pre>
SQL>UPDATE member SET name = '한가나' WHERE id = 'abc';
</pre>

### 레코드확인
<pre>
SQL>SELECT * FROM member;
SQL>SELECT id, name FROM member;
SQL>SELECT id FROM member WHERE name='한가나';
</pre>

### 레코드삭제
<pre>
SQL>DELETE FROM member WHERE name = '최러기';
</pre>


## E. 기타
### DB명 확인
<pre>
SQL>SELECT NAME, DB_UNIQUE_NAME FROM v$database;
</pre>

### SID 확인
<pre>
SQL>SELECT INSTANCE FROM v$thread;
</pre>

