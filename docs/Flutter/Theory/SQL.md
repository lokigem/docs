---
title: "SQL"
date: 2022-10-06
template: main.html
---
## SQL이란?
Structured Query Language의 줄임말로 관계형 데이터베이스 관리 시스템(RDBMS)의 데이터를 관리 및 처리하기 위해 설계된 특수 목적의 프로그래밍 언어이며 질의(Query) 언어라고 불리기도 합니다.

### Normalization(정규화)
중복을 최소화하게 데이터를 구조화 하는 프로세스를 정규화(Normalization)이라고 한다.
## 문법
### Select : 데이터 선택하기 

```sql
SELECT {column} FROM {table}
```
> 출력

```console
 List[ {map}, {map} ... {map}] 
```
### Update : 데이터 업데이트하기
```sql
UPDATE {table} SET {column} WHERE {condition}
```
Where 조건에 일치하는 Colum이 Set에서 명시한 조건으로 변경된다.

![SQLupdate](/docs/assets/img/flutter/Theory/SQL/SQLupdate.jpeg)

### Delete : 데이터 삭제하기 
```sql
DELETE FROM {table} WHERE {condition}
```
Where 조건에 일치하는 Column이 전부 삭제된다.<br>
![SQLDelete](/docs/assets/img/flutter/Theory/SQL/SQLDelete.jpeg)
### Insert - 새로운 데이터 추가하기
```sql
INSERT INTO {table} {column1, column2 ...) VALUES {value1, value2 ...}
```
Column에해당하는 Value를 추가해준다.<br>
![SQLInsert](/docs/assets/img/flutter/Theory/SQL/SQLInsert.jpeg)

### Join - 여러 테이블 합치기 
#### Many to One Relationship
```sql
SELECT {column} FROM {table} INNER JOIN {other_table} ON {condition}
```
contion : table1.colum = table2.colum // 이 두개의 column이 동일하다는 의미이다.<br>
![SQLjoin](/docs/assets/img/flutter/Theory/SQL/SQLjoin.jpeg)<br>
![SQLjoinResult](/docs/assets/img/flutter/Theory/SQL/SQLjoinResult.jpeg)
#### Many to Many Relationship
![SQLjoinResultManyToMany](/docs/assets/img/flutter/Theory/SQL/SQLjoinResultManyToMany.jpeg)
#### Join의 종류
![SQLKindOfJoin](/docs/assets/img/flutter/Theory/SQL/SQLKindOfJoin.jpeg)<br>
