---
cards-deck: Theory of computation::Turing Computation
^1608214104275
ankified?: no

lecture:
subject: [Computer Science, Theory of computation]
tag:
date:  Thursday 17th, Dec 2020 (352nd)
status: [ongoing]
---
- Undecidable Problems
- Basic Concept
- First Computer
- Can Machine Think?
	- Turing Test
	- Artificial Intelligent
- Turing Test
- Turing Machine Characteristics
- How it works
	- steps of input tape (3)
	- The Input String
- Picture of a Turing Machine
- Def of Turing Machine
	- 7 tuples
		- M= (Q,⨊ ,Γ , δ,  $q_0$ , B, F)
		- Transition Function
			- two argument
			- 3 output
		-  Example

# Turing Machine
## Why Turing Machine 
the following problem is called the decision making problem
Turing asked a question
![[Pasted image 20201217184001.png]]

## Defining Turing Machine

The Turing machine — was this: #card
-	![[Pasted image 20201217184508.png]]
	- (1) A tape of infinite length
	- (2) Finitely many squares of the tape have a single symbol from a finite language.
	- (3) Someone (or something) that can read the squares and write in them.
	- (4) At any time, the machine is in one of a finite number of internal states.
	- (5) The machine has instructions that determine what it does given its internal state and the symbol it encounters on the tape
^1608214071677


		- The instruction of the Turing machine can #card 
			-   change its internal state;
			-   change the symbol on the square; 
			-   move forward;  
			-   move backward;  
			-   halt (i.e. stop).
^1608214072323

### The Tape Head #card 
The turing machine had a tape head. With that the machine can read and write on the head
![[Pasted image 20201217185558.png]]
^1608214072711

The head follow this 3 steps at each time . . . #card
- 1. Reads a symbol
- 2. Writes a symbol
- 3. Moves Left or Right
^1608214073101

## Turing-Machine Formalism
How many tuples does Turing Machine is defined #card
- A TM is described by 07 tuples:
	- M= (Q,⨊ ,Γ , δ,  $q_0$ , B, F), the symbols are ..  #card
		- Q is a *finite set of states*
		- T is the *tape alphabet* (symbols which can be written on Tape)
		- B is *blank symbol* (every cell is filled with B except input alphabet initially)
		- ∑ is the *input alphabet* (symbols which are part of input alphabet)
		- δ is a *transition function* which maps Q × T → Q × T × {L,R}. Depending on its present state and present tape alphabet (pointed by head pointer), it will move to new state, change the tape symbol (may or may not) and move head pointer to either left or right.
		- q0 is the *initial state*
		- F is the set of *final states*. If any state of F is reached, input string is accepted
^1608214073509

### Transition function
- Takes two arguments #card 
	- 1. A state, in Q.
	-  2. A tape symbol in Γ .
^1608214073881

here is  how δ looks like #card
```(q0, a) → (q1, A, R)```
That means in q0 state, if we read symbol 'a' then it will go to state q1, replaced a by X and move ahead right(R stands for right).
^1608214074248

