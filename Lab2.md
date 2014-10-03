Lab 2
====

### Group:
- Camilla Lambrocco
- Bruno Guovela

In this Lab we are implementing an interpreter and a javascript to become familiar programming languages.

## Question 1 

######(A)
We consider V ::= a|b our domain. When tranformed it in judgment form it becames:



| **axiom1** |  **axiom2**|    
|:-------: | :------: |
|  |  |
|a in VObject | b in VObject |


We then convert A ::= A&A|V. When tranformed it in judgment form it becames:

|      | **Rule1** |  **Rule2**|    
| :--: |:-------: | :------: |
| Premise |A<sub>1</sub>in AObject, A<sub>2</sub> in AObject | V in VObject |
|Conclusion |A<sub>1</sub> & A<sub>2</sub> in AObject | V in AObject |

######(B)

######(C)
S ::= A|B|C<br> 
A ::= aA|a<br> 
B ::= bB|ε<br> 
C ::= cC|c

From the this grammar we can see that the syntax allows either only _**a**_ or only _**b**_ or only _**c**_. The difference between the repetition of the _**a**_ (or _**c**_) and the repetition of _**b**_ is in the number of repetition of the same character. Indeed, letting _*N*_ be the number of repetitions, if we repeat _**A**_ (or _**C**_) and _**B**_ _*N*_ times then we would have one more character when repeating _**a**_ (or _**c**_) then when repeating _**b**_. This is due to the ε in the definition of _**B**_.

######(D)
S ::= AaBb <br> 
A ::= Ab|b <br> 
B ::= aB|a

The possible outputs of this grammar are:
- baab, the derivation is<br> 
 _**S -> AaBb -> baBb -> baab**_
- bbaab<br> 
 _**S -> AaBb -> AbaBb -> bbaBb -> bbaab**_

######(E)
S ::= aScB|A|b<br> 
A ::= cA|c<br> 
B ::= d|A

The possible outputs of this grammar are:
- ***abcd***, the parse tree is<br> 
--------------- S --------------- <br>
------ a --- S --- c --- B ------ <br> 
..................|................|.......... <br>
------------ b --------- d ------

- ***accc***, the parse tree is<br> 
--------------- S --------------- <br>
------ a --- S --- c --- B ------ <br> 
..................|................|.......... <br>
------------ A --------- A ------ <br>
..................|................|.......... <br>
------------ c --------- c ------ 

## Question 2

######(A)
1. e ::= operand | e operator operand <br>

2. e ::= operand esuffix<br>
esuffix ::= operator operand esuffix | ε

- The two grammars allow us to create the sequence "operand operator operand" thanks to the "premise" (_**e operator operand**_ for the first one and _**operand esuffix**_ for the second syntax) that call recursively the "conclusion" (_**e**_ for the first syntax, _**esuffix**_ fo the second one).

- Letting the parse trees:<br>

######1
------------------------------------------------ e operator operand  <br>
.....................................................................| <br>
--------------------------------- e operator operand ------ <br> 
................................................| <br>
------------------ e operator operand ------ <br> 
...........................| <br>
--- e operator operand ------ <br> 
......|
operand

This produce the output:<br>
_**operand operator operand operator operand operator operand operator operand**_


######2
operand esuffix<br>
...................| <br>
--------- operator operand esuffix <br> 
...............................................| <br>
---------------------------- operator operand esuffix <br> 
..........................................................................| <br>
----------------------------------------------- operator operand esuffix<br> 
....................................................................................................|<br>
----------------------------------------------------------------------- ε <br> 

This produce the output:<br>
_**operand operator operand operator operand operator operand**_ <br>
We notice that the two grammars generate the same pattern, however for the same number of recursions the second grammar produces one _**operator operand**_ less.

######(B)
We test the higer priority of "-" with the following command code:<br>

_**scala> 1 - 3 << 1 <br>
res5: Int = -4**_ <br>

_**scala> 1-3 <br>
res8: Int = -2 <br>
scala> -2 << 1 <br>
res9: Int = -4**_  <br>

In this case we see that "-" has higher precedence then "<<". If we introduce parentheses to give priority to "<<" then we have:<br>

_**scala> 1- (3 << 1) <br>
res11: Int = -5**_  <br>

_**scala> 3 << 1 <br>
res12: Int = 6 <br>
scala> 1-6 <br>
res13: Int = -5**_ <br>

We now notice that the parentheses are forcing the higer priority to "<<" letting to a different output with resect to the case in which we didn't introduce them.<br>
For safety we check that this is not just the case of left associativity:<br>

_**scala> 1 << 4-3  <br>
res19: Int = 2**_ <br>

_**scala> 4-3 <br>
res20: Int = 1 <br>
scala> 1 << 1 <br>
res21: Int = 2**_ <br>

Whereas when introducing parentheses we have:<br>

_**scala> (1 << 4) - 3<br>
res23: Int = 13**_ <br>

_**scala> (1 << 4) <br>
res24: Int = 16 <br>
scala> 16 -3 <br>
res25: Int = 13**_ <br>

We notice that the parentheses force the priority once again to "<<" letting to a different output with respect to the case where we didn't use them. This tested the precedence of the operators proving that "-" has higher priority then "<<".

######(C)
We create a grammar that satisfies unambiguously the requirements to write a float that can be rised to an exponent.

_**< Float >**_ ::= < Integer > . < Decimal > <br>
_**< Integer >**_ ::= < Value > | < NegVal > <br>
_**< Positive >**_ ::= 0 < Positive > | < Value > | ε <br>
_**< Value >**_ ::= 1 < Positive > | 2 < Positive > | ....... | 9 < Positive > <br>
_**< NegVal >**_ ::= - < Value > <br>
_**< Zero >**_ ::= 0 < Zero > | 0 <br>
_**< DecimalWithExp >**_ ::= < Positive > < Value > E < Integer > <br>
_**< Decimal >**_ ::= < Zero > | < DecimalWithExp >


