---
ankified?: 'no'
lecture: null
subject: null
tag: null
date: 2020-12-22
status:
  - ongoing
cards-deck: Theory of Computation::CNF
---
# CNF
 ## Convert CFG to CNF
 There is three steps to convert
 
 the steps are #card
 - Eliminate useless symbols
 - Eliminate ε-production
 - Eliminate unit production
#### First step:: Find nullable variables
<<<<<<< HEAD
^1608635693407

**Basis**:: if A ->ε is a production of G, then A is nullable
^1608635693869

**Induction**:: if there is a production b -> $C_1 C_2$...$C_k$ such that C is a variable and each C is nullable then B is nullable

#### Procedure to Remove Null Production
here is the steps #card 
- to remove A -> ε, look for the production right side contain A
- Replace each occurrences of "A" in each of these production with ε 
- Add the resultant production to the Grammar
^1608698128736

##### Example
Here is the Cfg `S -> AB; A -> aAA/ε & B -> bBB/ε` Now remove null production ... #card
Nullale Variables are {A, B, S}
Because start state also a Nullable symbol so ε belongs to given CFG
We will proceed with the method:
```c		
		S -> AB/A/B/ε
		A -> aAA/aA/a
		B -> bAA/bA/b
```

### Eliminating Unit Production

#### Find the Unit Production

**Basis**::(A, A) is a unit pair of any variabel A, if A->A by 0 steps

Induction:: Let's (A, B) be a unit pair and let B -> C is a production, where A, B, and C are variables, then we can conclude that (A, C) is also a unit pair


# Lecture Video:
<iframe src="https://drive.google.com/file/d/1KYIwuHmL9NdWDaqsBkGPLKeTOYadmNae/preview" width="640" height="480"></iframe>
=======

Basis:: if A ->ε is a production of G, then A is nullable

Induction:: if there is a production b -> $C_1 C_2$...$C_k$ such that C is a variable and each C is nullable then B is nullable

#### Procedure to remove Null Production
