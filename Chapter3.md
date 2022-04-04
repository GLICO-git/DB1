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
- Relation r

A|B|C|D
:---:|:---:|:---:|:---:
$\alpha$|$\alpha$|1|5
$\alpha$|$\alpha$|5|2
$\beta$|$\beta$|12|12
$\alpha$|$\beta$|23|10
***
- $\Pi_{A, C}(r)$

A|C
:---:|:---:|:---:|:---:
$\alpha$|1
$\alpha$|5
$\beta$|12
$\alpha$|23
***
- $\Pi_{A, B}(r)$

A|B
:---:|:---:|:---:|:---:
$\alpha$|$\alpha$
$\beta$|$\beta$
$\alpha$|$\beta$
***

- 투영(project)연산은 관계에서 임의의 속성을 선택하는 연산으로,<br>
상기 예제에서 관계 r에서 명시된 속성만을 보여주는 투영 연산이다
- 투영 후에 중복된 터플은 제거되어, 결과 관계에서는 동일한 터플이 두 번 이상 나타나지 않는다
***
# Union Operation
- 관계 대수의 합집합 정의는 일반적인 합집합 정의와 동일하며, 터플을 집합 원소로 취급한다
- 관계 대수 집합 연산이 유효하려면, 터플의 속성 개수가 동일하여야 하고, 대응되는 속성의 <br>
도메인이 상호 호환적이어야 한다
***
- Example :<br>
$\Pi_{cID}(\sigma_{semester="Fall" \bigwedge year=2014}(teaches))$ $\cup$
<br>$\Pi_{cID}(\sigma_{semester="Spring" \bigwedge year=2015}(teaches))$
***
- 위 예제는 2014년 가을과 2015년 봄에 개설된 모든 과목의 과목번호(cID)를 검색한다
- course 관계에는 과목 개설 시기에 대한 정보가 없으므로 teaches 관계를 이용하였다
***
 ## Union Operation Example
- Relation r

A | B
:---: | :---:
$\alpha$|1
$\alpha$|5
$\alpha$|23
***
- Relation s

A | B
:---: | :---:
$\alpha$|1
$\beta$|12
***
- r $\cup$ s

A | B
:---: | :---:
$\alpha$|1
$\alpha$|5
$\alpha$|23
$\beta$|12
***
# Set Difference Operation
- 차집합(set difference)은 `commutative`하지 않으므로 "r-s"과 "s-r"연산 결과는 다르다
***
- Example : <br>
$\Pi_{cID}(\sigma_{semester="Fall" \bigwedge year=2014}(teaches))$ ---
<br>$\Pi_{cID}(\sigma_{semester="Spring" \bigwedge year=2015}(teaches))$
***
- 위 예제는 2014년 가을 학기에 개설되었으나 2015년 봄 학기에는<br>
개설되지 않은 과목 번호를 검색하는 질의이다
***
# Cartesian Product Operation
- 카티시안곱(Cartesian Product)은 입력 관계의 각 터플을 취하여 이를 연결(concatenation)하여<br>
결과 관계를 만든다
- 두 개의 입력 테이블에 동일 속성이 존재하면, 재명명(rename)연산을 이용하여 동일한 속성 이름이<br>
없도록 해야 한다
- 이는 입력 테이블에 동일 속성 이름이 존재하면 자연 조인(natural join)연산이 되기 때문이다
- Cartesian Product operation

||R|S|R x S
:---:|:---:|:---:|:---:
Arity|m|n|m+n
# of tuples| x|y|x*y

- Arity : 속성의 개수
***
 ## Cartesian Product Operation Example
- Relation r

A | B
:---: | :---:
$\alpha$|1
$\alpha$|5
$\alpha$|23
***
- Relation s

A | B
:---: | :---:
$\alpha$|1
$\beta$|12
***
- r x s

A|B|C|D
:---:|:---:|:---:|:---:
$\alpha$|1|$\alpha$|1
$\alpha$|1|$\beta$|12
$\alpha$|5|$\alpha$|1
$\alpha$|5|$\beta$|12
$\alpha$|23|$\alpha$|1
$\alpha$|23|$\beta$|12
***
- 카티시안곱의 결과물은 입력 관계에 속하는 터플의 모든 가능한 조합을 결과 관계로 산출한다
***

# Rename Operation
- 재명명 연산은 단순히 테이블 이름이나 속성 이름을 변경하는 연산이다
- 수학 기호는 $\rho$(rho)이다
***
- Example :
$\rho_{x(A_1, A_2,...,A_n)}(E)$
- 입력 관계가 `E`이면, 이를 아래첨자에 표시된 바와 같이 재명명하여 겨로가 관계를 도출한다
- 아래 첨자에서 X는 관계명, $A_1,...,A_n$는 속성명을 나타낸다
***
# Relational Algebra Expressions
- 앞선 관계 대수 6개는 기본적인 관계대수 연산이다
- 기본 관계 대수 연산을 이용하여 관계 대수식이 생성된다
- 관계 대수식의 결과는 관계이므로 관계 대수식의 합성이 가능하다
- 입력 관계 대신에 유효한 관계 대수식을 사용될 수 있으며, 이를 이용하여
<br>복잡한 질의문 작성이 가능하다
***
