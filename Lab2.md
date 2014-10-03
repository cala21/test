Lab 2
====

### Group:
- Camilla Lambrocco
- Bruno Guovela

In this Lab we are implementing an interpreter and a javascript to become familiar programming languages.

## Question 1 

######(A)
We consider V ::= a|b our domain. When tranformed in judgment form it becames:

\(\pi\)

|          |          |    
|:-------: | :------: |
| a | b |


######(B)
Given the code we identify ***x*** in line 3 to be bound at line 2 (_**f**(x: Int)_). This happens to be because ***x*** at line 3 is allocated in the scope of the function f.

Given the code we identify ***x*** in line 6 to be bound at line 2 (_**f**(x: Int)_). This happens to be because ***x*** at line 6 is allocated in the scope of the function ***f()***. 

Given the code we identify ***x*** in line 10 to be bound at line 2 (_**f**(x: Int)_) as well. This happens to be because ***x*** at line 10 is in the scope of the function f and it is outside the scope that goes from line 7 to line 10.

Given the code we identify ***x*** in line 13t o be bound at line 1 (_**val** x=3_). This happens to be because ***x*** at line 13 (for both ***x*** and ***f(x)***) is allocated outside the function ***f()***. 

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

