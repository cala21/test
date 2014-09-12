test
====
# Lab 1
# Group's partners: Ca
In this Lab we are implementing some functions and an easy script to become familiar with the functional language SCALA

##Question 1
(a) 

Given the code we identify pi in line 4 to be bound at line 3 (val pi = 3.14159). This happens to be because we are considering the value pi previously defined in the same scope (line 2 to 5).

Given the code we identify pi in line 7 to be bound at line 1 (val pi = 3.14). This happens to be because we are considering the value pi outside the function circumference. It follows that its declaration is bound to line 1.

(b)

Given the code we identify x in line 3 to be bound at line 2 (f(x: Int)). This happens to be because x at line 3 is allocated in the scope of the function f.

Given the code we identify x in line 6 to be bound at line 2 (f(x: Int)) as well. This happens to be because x at line 6 is allocated in the scope of the function f. 

Given the code we identify x in line 10 to be bound at line 2 (f(x: Int)) as well. This happens to be because x at line 10 is in the scope of the function f and it is outside the scope that goes from line 7 to line 10.

Given the code we identify x in line 13t o be bound at line 1 (val x=3). This happens to be because x at line 13 (for both x and f(x)) is allocated outside the function f. 

##Question 2

We consider the body of the function g to be well typed and we give the following demonstration using the format required by the second part of the question:

(a,b): Tuple (Int, Int) because
## 1: Int
## (x,3) : Tuple (Int, Int) because
#####x: Int
#####3 : Int
(b,1) : Tuple (Tuple (Int,Int), Int) because
## b : Tuple (Int,Int)) because
#### x : Int
#### 3 : Int
## 1 : Int
(b, a+2) : Tuple (Tuple (Int,Int), Int) because
## b : Tuple (Int,Int)) because
#### x : Int
#### 3 : Int
## a + 2 : Int because
####a : Int
####2 : Int