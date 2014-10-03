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
| Premisis |A<sub>1</sub>in AObject, A<sub>2</sub> in AObject | V in VObject |
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
>> S -> AaBb -> baBb -> baab
- bbaab<br> 
 S -> AaBb -> AbaBb -> bbaBb -> bbaab

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
- Yes the two grammars generate the same expression, letting the parse trees:<br>

######1
------------------------------------------- e operator operand  <br>
....................................................|.......... <br>
------------------------------ e operator operand ------ <br> 
....................................|.......... <br>
---------------- e operator operand ------ <br> 
...................|.................. <br>
--- e operator operand ------ <br> 

######(B)

'''Scala
2 << 3 - 1 = 
