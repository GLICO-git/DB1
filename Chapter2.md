<!--
1. 이미지(가운데 정렬, 60%)
<p align = "center"><img src = "./img/Chapter/" width = "60%"/></p>
<p align = "center">내용</p>

-->

# Chapter2 관계형 데이터 모델(1)
## Subtopics
 1. [Relational Data Model](#Relational-Data-Model)
	- [Relation Example](#Relation-Example)
	- [Equivalent Terms](#Equivalent-Terms)
	- [Attributes](#Attributes)
	- [All attributes are atomic in relational model](#All-attributes-are-atomic-in-relational-model)
	- [Relation Schema and Instance](#Relation-Schema-and-Instance)
	- [Relational Databases](#Relational-Databases)
	- [Sample University Database](#Sample-University-Database)
	- [Order is immaterial](#Order-is-immaterial)
	- [Keys](#Keys)
	- [Key Example](#Key-Example)
	- [Referential Integrity Constraint](#Referential-Integrity-Constraint)
	- [Why Referential Integrity Constraint?](#Why-Referential-Integrity-Constraint)
 1. [Sample University Database](#Sample-University-Database)
	- [Running Example(University)](#Running-Example(University))
	- [Schema Diagram](#Schema-Diagram)
		- ["department" Relation](#"department"-Relation)
		- ["course" Relation](#"course"-Relation)
		- ["professor" Relation](#"professor"-Relation)
		- ["teaches" Relation](#"teaches"-Relation)
		- ["student" Relation](#"student"-Relation)
		- ["takes" Relation](#"takes"-Relation)
		- ["room" Relation](#"room"-Relation)

***
# Relational Data Model
- 관계형 데이터 모델은 1970년 수학자 `E.F Codd`에 의해 제안되었다
- 수학적 이론 중에서 집합이론, 일차 수학논리를 사용하며, 그 내용은 아주 간단하다
- 관계형 데이터 모델은 데이터베이스를 `관계(Relation)`와 `무결성 제약사항(Constraints)`의 집합으로 표현한다
***
## Relation Example

sID|name|gender|deptName|year|GPA|totalCredit
:---:|:---:|:---:|:---:|:---:|:---:|:---:
152|Eric Lee|M|CS|freshman|3.54|15
201|Sam Kim|M|EE|senior|3.89|103
301|John Park|M|Media|sophomore|4.13|38
157|Alma Lee|F|CS|freshman|2.57|18
154|Joan Lee|F|CS|sophmore|1.80|58

- 위 표는  `student`관계의 예제이다 관계형 데이터 모델에서 의미하는 관계는 우리가 흔히 보는 테이블 형식이다
- `student`관계는 7개의 속성(attribute)과 5개의 터플(tuple)을 가지고 있다<br>
각 속성은 속성헤드(attribute head)를 가지고 있으며, 상기 관계에서는 `sID`, `name`, `gender`,<br>
`deptName`, `year`, `GPA`, `totalCredit`이다
***
## Equivalent Terms
Relational data model | Network data model<br>Hierarchical data model
:---:|:---:
relation|table
tuple|record, row
attribute|column

- 관계형 모델에서의 `relation`, `tuple`, `attribute`는 기존 데이터 모델에서의 <br>
`table`, `record`, `column`과 동일한 용어로 볼 수 있다
***
## Attributes
- 각 속성은 속성 값으로 허용할 수 있는 값의 집합을 가지고 있으며, 이를 `도메인(Domain)`이라고 한다.
- 속성 도메인에 속하는 값은 `원자(atomic)`값을 가져야 한다.
- 각 도메인은 값이 없는 것을 의미하는 `널(null)`값을 `디폴트(default)`로 가진다
***
## All attributes are atomic in relational model
- 관계형 모델에서 **모든 속성 값은 원자 값**이어야 하는데, 원자 값은 더 이상 분해할 수 없는 값이란 뜻이다
- 일반적으로, `정수`, `실수`, `문자`, `문자열`, `시간`, `날짜` 등을 원자 값으로 생각한다
***
## Relation Schema and Instance
- 간단하게 보면, 관계 스키마는 관계 이름과 속성명 나열을 의미한다
- 관계 스키마가 정의되면 관계 스키마에 적합한 값의 조합을 가질 수 있으며, 이를 관계 인스턴스라고 한다
- 앞선 student는 관계 인스턴스의 예제라고 볼 수 있다
- 관계 인스턴스는 각 속성 도메인의 값의 모든 조합에서 일부분을 가진다
- 즉, 관계 인스턴스는 도메인의 카티시안곱(Cartesian Product)의 부분 집합으로 볼 수 있다
- 수학에서 이러한 부분집합을 관계(Relation)라고 명명하며, 이러한 이유로 관계형 데이터 모델이라고 명명되고 있다.

***
- Let A1, A2, ..., An be attributes
- R = (A1, A2, ..., An) is a relation schema
- with a relation schema, we can have individual values
for the schema, which we call a relation instance
- Given sets D1, D2, ..., Dn(domains), a relation instance is a subset of
D1 x D2 x ... Dn
- A relation instance is a set of n-tuples(a1, a2, ..., an)
	where each
	$ai \in Di$
***
## Relational Databases
- 관계형 데이터베이스 시스템에서 데이터베이스는 관계와 제약 조건으로 구성된다고 정의한다
`Relational DB` = `a set of relations` + `a set of integrity constraints`
- 여기서 무결성 제약(integrity constraint)은 다양한 형태가 존재하며,<br>`키 제약`(주 키는 중복된 값을 가지지 못하는 제약),<br>
`엔티티 제약`(주 키는 널 값을 가지지 못하는 제약),<br>`참조 무결성 제약` 등이 있다.
***
## Sample University Database
<p align = "center"><img src = "./img/Chapter2/univDB.jpg" width = "60%"/></p>
<p align = "center">대학 데이터베이스 예제</p>

- 위 그림은 관계형 데이터베이스의 예제를 보인다
- 그림 중에 속성 밑줄은 `주 키(Primary key)` 속성을 표시하며, `course` 관계의 주 키는 `cID`속성이다
- `teaches` 관계의 주 키는 4개 속성의 연결(concatenation) (pID, cID, semester, year)이며, <br>
속성 하나 하나는 주 키가 아니다.
- 그림에서 화살표시는 `참조 무결성 제약`을 표시한다.
<br>-> `teaches`관계의 `cID`속성은 `course`관계의 주 키 속성인 `cID` 속성을 참조하는 `외래 키(foreign key)`이다
***
## Order is immaterial
- 관계형 데이터베이스에서 관계 간에는 순서가 없다
- 관계 내에서의 터플(tuple)도 순서가 없다
- 이는 관계형 데이터 모델의 중요한 특징이며, 편리함을 제공한다
***
## Keys
- 키는 속성의 집합으로 구성이 된다
- `Super key(슈퍼 키)`는 관계에서 터플을 유일하게 식별할 수 있는 속성의 집합이다
- `Candidate key(후보 키)`는 `Super key`의 유일성을 유지하면서 가장 적은(minimal) 수의 속성으로 구성된 키이다<br>
만약 관계에 하나 이상의 후보 키가 존재하면, 데이터 베이스 설계자가 그 중의 하나를 `Primary key(주 키)`로 지정한다
***
## Key Example
```
Mystudent(student-id, name, national-id, address, phone)

Superkey
	- (student-id), (student-id, name), (student-id, name, address),
	- (national-id), (national-id, name), (national-id, address, phone)
	- (student-id, national-id), (student-id, national-id, name) so as on

Candidate
	- (student-id)
	- (national-id)

Primarykey
	- One of (student-id) or (national-id)
```
***
- MyStudent 관계가 있으며, 그 중 `student-id`와 `national-id`속성은 유일 식별자이다
- `student-id`는 학번을 의미하며 학생들에게 **유일한** 번호가 지정되며,
- `national-id`는 주민등록번호를 의미하며 이 역시 **유일한** 번호가 지정된다
- 슈퍼 키는 그 수가 매우 많으며 그 중 일부분이 나열되어 있다
- 슈퍼 키 (`student-id`, `name`)은  `student-id`만으로도 각 학생을 유일하게 식별 가능하므로
<br> 굳이 (`student-id`, `name`)와 같이 두 개 속성을 가질 필요가 없지만, 슈퍼 키 이다
- 슈퍼 키에서 키 속성을 유지하면서 가장 적은 수의 속성을 가지는 키를 후보 키 라고 한다
- `student-id`은 가장 적은 수의 속성을 가지는 후보 키가 되는 것이다 
- 같은 방식으로 `national-id`도 후보 키가 된다
***
## Referential Integrity Constraint
- `참조 무결성 제약(Referential Integrity Constraint)`는 관계형 데이터 모델에만 존재하는 제약이다
- 간단하게 말하면, `참조 무결성 제약`은 특정 속성에 나타나는 모든 값은 반드시 다른 속성에도 나타나야 한다는 것이다
## Why Referential Integrity Constraint?
<p align = "center"><img src = "./img/Chapter2/constraint.jpg" width = "60%"/></p>
<p align = "center">참조 무결성 예제</p>

- 위 그림과 같이 두 테이블이 있으며, `student`테이블에서 `Lee`학생의 `major`속성 값은 2이며,<br>
이는 `department`테이블을 보면 `electrical engineering`을 전공하고 있음을 알 수 있다
- **그러나 `Sohn` 학생은 `major`속성값 4에 대응이 되는 학과가 없어 문제가 있다**
- `Park`학생은 `major`값이 없는 `null`인데, 아직 학과가 결정되지 않았거나 또는 데이터가<br>
존재하지 않거나 등으로 해석할 수 있어, 문제가 되지 않는다
***
- 즉, `major`속성 값은 아무런 제약 없이 임의의 값을 가질 수 없고, <br>
`department`의 `dID` 속성 값 중 에서 나와야 의미가 있다
- 이 경우, `major`속성을 `department(dID)`를 참조하는 외래 키라고 하며,
- `student`테이블을 참조하는 테이블, `department`테이블을 참조 받는 테이블이라고 한다
***
- **참조 받는 속성은 반드시 그 테이블의 주 키이어야 하며**
- 본 예제에서도 `dID`가 `department`테이블의 주 키임을 알 수 있다
- 또한 `<3, media>` 터플을 참조하는 터플이 `student`테이블에 없으며,<br>
이는 참조 무결성 제약과 관련 없이 허용되는 현상이다
***
# Sample University Database

## Running-Example(University))
## Schema-Diagram)
### "department"-Relation)
### "course"-Relation)
### "professor"-Relation)
### "teaches"-Relation)
### "student"-Relation)
### "takes"-Relation)
### "room"-Relation)
***
