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
- abcd, the parse tree is<br> 
->S<- <br> 
>>> a >>> S >>> c >>> B<br> 
... ... b ... ... ... d

- bbaab
... S -> AaBb -> AbaBb -> bbaBb -> bbaab

## Question 2

We consider the body of the function g to be well typed and we give the following demonstration using the format required by the second part of the question:

*Line 2 =>* (a,b): **Tuple** (**Int**,**Int**)  because
- 1: **Int**
- (x,3) : **Tuple** (**Int**,**Int**)  because
- x: **Int**
- 3 : **Int**

*Line 3 =>* (b,1) : **Tuple** (**Tuple** (**Int**,**Int**), **Int**) because
- b : **Tuple** (**Int**,**Int**)  because
- x : **Int**
- 3 : **Int**
- 1 : **Int**

*Line 3 =>* (b, a+2) : **Tuple** (**Tuple** (**Int**,**Int**), **Int**) because
- b : **Tuple** (**Int**,**Int**) because
- x : **Int**
- 3 : **Int**
- a + 2 : **Int** because
- a : **Int**
- 2 : **Int**

## Question 3
For this part of the Lab we were asked to implement some basic operations: Absolute Value and XOR.

######(A): Absolute Value
To implement _**def** abs_ we simply forced the returned value to be positive.

######(B): XOR
We created two cases using the ***match*** function. Since XOR accepts ***boolean*** and returns ***boolean***, we coded our algorithm with respect to the
following logic:

|     A      |     B     |     Result     |
|:------------: | :---------------: | :-----: |
| T | T | F |
| F | F | F |
| T | F  | T |
| F | T  | T |

## Question 4

The main idea of this section was to become familiar with recursive calls in *SCALA*. 

######(A): _**def** repeat(s :**String**, n :**Int**)_
This function was easily implemented considering two cases:
1. if *n = 0* (we do not repeat the string) 
2. if *n != 0* we recursively call the function ***repeat()*** *n-1* times

######(B): Newton's Method
We used Newton's Method to implement the *square root*. We wrote several functions:
1. _**def** sqrtStep(c: **Double**, xn: **Double**): **Double**_

This function was implemented using the basic algorithm through which we derive the approximation, given a base case ***xn***.
2. _**def** sqrtN(c: **Double**, x0: **Double**, n: **Int**): **Double**_

This was the function in charge of the level of approximation of the square root. We required a positive ***n*** (level of approximation) and then we defined the base case (***n=0***). In order to reach the final approximation we needed to recursively call ***sqrtN()***.
3. _**def** sqrtErr(c: **Double**, x0: **Double**, n: **Int**): **Double**_

This was the function that defined the maximum error allowed when calculating the square root of a number. We required a positive ***epsilon*** (maximum error allowed) and then we defined two cases that follows from the following question: is the error less then epsilon? 
- yes, return the approximated result
- no, recursively call ***sqrtErr()***

## Question 5

This section was based on the implementation of the data structure ***tree***. In order to realize a good data structure we had to wrote multiple functions.
######(A) _**def** repOk(t: **SearchTree**): **Boolean**_

We checked if the ***tree*** was valid, meaning we made sure to return ***true*** if the left child and the right child of each node were respectively less and bigger then their root value. Moreover, we considered the special case of an empty ***tree*** to be ***true***.
######(B) _**def** insert(t: **SearchTree**, n: **Int**): **SearchTree**_

In order to insert the value ***n*** in ***t*** we traversed the ***tree*** (recursive calls of ***insert()***) to see where the value could fit. If we found the right place to insert it we placed it with respect to the idea expressed in part **(a)**.
######(C) _**def** deleteMin(t: **SearchTree**): (**SearchTree**, **Int**)_

From the idea expressed in part **(a)** we deleted the root value if no left child was present, otherwise we recursively called ***deleteMin()*** with the left subtree as the argument of the function. Finally, we returned the new ***Node*** and the value deleted.
######(D) _**def** delete(t: **SearchTree**, n: **Int**): **SearchTree**_

We implemented ***delete()*** considering the different positions of  ***n*** in the ***tree***. Does ***n*** have any children?:
- only left child
- only right child
- both children
- none

if the value was not found in the current ***Node*** we recursively called ***delete()*** with the new ***SearchTree*** argument (depending on the cases).

## Question 6

The propose of this section was implementing a basic language interpreter performing basic operation with unary and binary operators. We were able to implement the function _**def** eval(e: **Expr**): **Double**_ using ***match()*** and the *case object*.

For  *case class* **Binary**:
- ***Plus***
- ***Minus***
- ***Times***
- ***Div***

For *case class* **Unary**: 
- ***Neg***

