# 1장
## Subtopics
 1. Databases
 1. Data Abstraction and Data Model
 1. Database Systems

***
# Databases
- DB 는 데이터의 collection임
- DBMS(Database Management System)은 DB를 다루기 위한 시스템 집합
- DBS (Database System)
<br>
-> 이 세가지 용어는 혼합하여 자주 사용함
***

# DBMS의 장점
- 데이터 추상화
- 데이터 접근이 쉽다
    - DB언어 지원
    - UI 지원
- 데이터의 일치, 불일치를 컨트롤할 수 있다
- Integrity constraint(IC) 데이터의 조건 유지
- Atomicity of Updates (원자성 : All or Nothing을 잘 지킴)
- 다수의 사용자가 동시에 접근하는 것(Concurrent access)을 잘 처리할 수 있다
- 데이터 보호(Data security)
- 데이터 백업 및 복원
***

# File Systems
- 파일 시스템은 보통 운영체제의 한 부분이고, 이론적으로 사용자는 파일 시스템을 이용하여 자신의 파일을 관리 할 수 있다.
<br>
-> 즉, Data의 크기가 적거나 다수가 사용하지 않는다면 File System만으로도 처리 가능하다<br>
'All functionalities of DBMSs are then on users responsibility'
***

# Instances and Schemas
- 스키마(Schema) : 데이터베이스의 논리적, 물리적인 구조체
    - the variable `type`
- 인스턴스(Instance) : 스키마에 대한 데이터베이스의 실제 내용
    - the `value` of variable
***
# CS에서의 추상화
- Computer Science에서의 추상화는
구체적인 인스턴스들에서 중요한 아이디어들만 뽑아내는 과정을 뜻 함
***
# 데이터 추상화의 레벨(Level)
- 물리적(Physical) 레벨 : 어떻게 물리적으로 저장되어있는지 설명하는 것
- 논리적(Logical) 레벨 : 저장되어 있는 데이터들과 그 관계성을 설명하는 것
- 뷰(View) 레벨 : 특정 사용자에게 관심있는 부분만 설명하는 것<br>

![three level abstraction](/img/Three_Level_Abstraction.jpeg)
- physical level 밑에 Data가 있다고 보면 됨
***
# Data Independence
- Physical data independence
    - 논리적 스키마의 변화 없이 물리적 스키마만 수정하는 것
- Logical data independence
    - 뷰 스키마의 변화 없이 논리적 스키마만 수정하는 것
***
# Data Model
- 실제 데이터는 굉장히 흩어져있고 복잡함
- 데이터 모델은 specification describing임
    - 관계형 모델
    - 객체지향형 모델
    - 객체관계형 모델
    - XML 등등...
***
# 관계형 모델
![relationModel](/img/Relation_exam.jpeg)
- 가장 일반적인 모델
***
# 객체관계형 모델
- 객체 지향 패러다임을 지원함
- 기존의 관계형 모델을 호환함
***
# XML
- Extensible Markup Language의 약자
# Database Design
- 데이터베이스 스키마는 성능에 가장 큰 영향을 미침
## DB Design Approaches
- Entity Realtionship Model
- Normalization Theory
<br>

-> 이번 학기 말에 자세히 설명
***
# Database Languages
- DBMS는 다양한 DB언어를 지원함
- QUEL, SQL, relational algebra 등
- SQL은 가장 인기있는 DB언어임
# SQL examples
- Find the name of the professor with ID 22222
``` sql
Select name
form professor
where pID = '22222';
```
- find the course titles that the professor with ID 22222 teaches
```sql
Select title
from teaches, course
where teaches.cID=course.cID and pID='22222';
```
***
# DBMS
- DBMS는 매우 크고 복잡한 s/w임
- 2가지 구성요소로 구분 할 수 있다
    - Query Processor
    - Storage Manager

![simplified DB System](/img/simple_db_sys.jpeg)

***
# Data dictionary
- 메타데이터(data about data)를 저장하는 딕셔너리
    - Database schema
    - Integrity constraints
    - Authorization
    - Statistical data
***
# Transaction Management
- Transaction은 데이터베이스 어플리케이션에서 단일 논리적 기능을 수행하는 DB 수행자(operation)의 절차
- 2가지 구성요소로 구분 됨
    - Concurrency control manager
    - Recovery manager