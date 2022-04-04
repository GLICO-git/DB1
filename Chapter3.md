<!--
1. 이미지(가운데 정렬, 60%)
<p align = "center"><img src = "./img/Chapter3/" width = "60%"/></p>
<p align = "center">내용</p>

-->

# Chapter2 : 관계형 데이터 모델(2)
## Subtopics
 1. [Relational Algebra](#Relational-Algebra) 
	- [Select Operation](#Select-Operation)
		- [Select Operation Example](#Select-Operation-Example)
	- [Project Operation](#Project-Operation)
		- [Project Operation Example](#Project-Operation-Example)
	- [Union Operation](#Union-Operation)
		- [Union Operation Example](#Union-Operation-Example)
	- [Set Difference Operation](#Set-Difference-Operation-Example)
	- [Cartesian Product Operation](#Cartesian-Product-Operation)
		- [Cartesian Product Operation Example](#Cartesian-Product-Operation-Example)
	- [Rename Operation](#Rename-Operation)
	- [Relational Algebra Expressions](#Relational-Algebra-Expressions)
***

# Relational Algebra

>  Six basic operators

> - select : $\sigma$
> - project : $\Pi$
> - union : $\cup$
> - set difference : -
> - Cartesian product : x
> - rename : $\rho$
***
- 관계 대수는 관계에 대한 다수 개의 연산을 제공하며, 사용자는 이를 이용하여 <br>
DB로부터 구하고자 하는 정보를 DB System에 요청(또는 표현)할 수 있다
- 관계 대수는 6개의 기본적인 연산이 있다
	- 입력으로 하나 또는 두 개의 관계를 가지며
	- 결과물로 새로운 관계를 생성한다
- 이는 관계 대수 연산의 중요한 성질이며, 관계 대수 연산의 중첩을 허용하게 한다

- 상용 DB System은 관계 대수를 직접적으로 사용자에게 지원하지 않는다
<br>-> 그 대신 SQL 언어를 사용자에게 지원한다
***
# Select Operation
- 선택(select) 연산의 기호는 $\sigma$(sigma)이며, p는 선택 조건(selection predicate)을 의미한다<br>
- 선택 조건 p는 명제논리(propositional logic) 표현이며,
- 각각의 항(term)은 $\land$(and), $\lor$(or),$\lnot$(not)으로 연결이 가능하다

- 각 항은 `<attribute> op <attribute>` 또는 <br>
`<attribute> op <constant>`형태 이며, op는 6개의 비교 연산자 중 하나이다<br>
=, $\ne$, $\le$, <, $\ge$, >
***
- Example : $\sigma_{deptName = "CS"}(professor)$
- 이 선택 연산은, 교수 중에서 CS과에 속한 교수를 검색한다
***
 ## Select Operation Example
- Relation r

A|B|C|D
:---:|:---:|:---:|:---:
$\alpha$|$\alpha$|1|5
$\alpha$|$\alpha$|5|2
$\beta$|$\beta$|12|12
$\alpha$|$\beta$|23|10
***
- $\sigma_{A=B ^\land D > 4}(r)$
- 결과 : 

A|B|C|D
:---:|:---:|:---:|:---:
$\alpha$|$\alpha$|1|5
$\beta$|$\beta$|12|12
***
- 선택(select)연산은 입력 관계에서 주어진 조건을 만족하는 터플을 생성한다
- 상기 예제에서 조건은 `"A=B ^ D>4"`이며 조건을 만족하는 터플이 결과물로 나옴을 알 수 있다
- 선택 연산의 결과물은 새로운 관계이다
***
# Project Operation
***
- 투영(project)연산의 기호는 $\Pi$(pi)이며, 보고자 하는 속성을 아래 첨자(subscript)로 표시한다
- 중복 터플은 결과 관계에서 제거되어, 결과 관계는 항상 터플의 집합이다
- 선택 연산이 `터플 단위`로 원하는 결과를 구하는 것이라면,
- 투영 연산은 `속성 단위`로 원하는 결과를 구하는 것이다
***
- Example : $\Pi_{pID, name, salary}(professor)$
- 이 예제는 professor 관계에서 pID, name, salary 속성만을 구하는 연산이며,<br>
다른 속성은 결과 관계에서 제거된다
***
 ## Project Operation Example
- 투영(project)연산은 관계에서 임의의 속성을 선택하는 연산으로,<br>
상기 예제에서 관계 r에서 명시된 속성만을 보여주는 투영 연산이다
- 투영 후에 중복된 터플은 제거되어, 결과 관계에서는 동일한 터플이 두 번 이상 나타나지 않는다
# Union Operation
 ## Union Operation Example
# Set Difference Operation
# Cartesian Product Operation
 ## Cartesian Product Operation Example
# Rename Operation
# Relational Algebra Expressions
