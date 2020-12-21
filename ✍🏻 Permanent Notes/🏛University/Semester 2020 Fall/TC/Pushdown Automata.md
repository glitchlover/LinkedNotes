---
ankified?: 'no'
lecture: null
subject: null
tag: null
date: Monday 21st, Dec 2020 (356th)
status:
  - ongoing
cards-deck: default
---
<iframe src="https://www.youtube.com/embed/4ejIAmp_Atw" class="resize-vertical" style="height: 505px;"></iframe>

# Pushdown Automata
def:: A pushdown automaton is a way to implement a context-free grammar in a similar way we design DFA for a regular grammar. 

A DFA can remember a finite amount of information, but a PDA can remember....:: an infinite amount of information.

---
- What kind of stack PDA is?:: ε-NFA

-  What kind of NFA PDA is?:: ε-NFA with a stack


---

## Basic Components
A pushdown automata has three components #card 
![[Pasted image 20201221212617.png]]
- An input tape
- A finite control unit
- A stack with infinite size

The stack head scans what?::the top symbol of the stack.

## Formal Definition
A PDA can be formally described as a ___ tuple :: 7-tuple (Q, ∑, S, δ, q<sub>0</sub>, I, F) 

The 7 tuple are #card 
- **Q** is the finite number of states
- **∑** is input alphabet
- **S** is stack symbols
- **δ** is the transition function: Q × (∑ ∪ {ε}) × S × Q × S\*
- **q<sub>0</sub>** is the initial state (q<sub>0</sub> ∈ Q)
- **I** is the initial stack top symbol (I ∈ S)
- **F** is a set of accepting states (F ∈ Q)

## Transition Function
Transition function takes ... arguments :: 3

The argument


The following diagram shows a transition in a PDA from a state q<sub>1</sub> to state q<sub>2</sub>, labeled as a,b → c. What are a,b and c are? #card 
![Transition in a PDA](/automata_theory/images/transition_in_a_pda.jpg)
This means at state **q<sub>1</sub>**, if we encounter an input string **‘a’** and top symbol of the stack is **‘b’**, then we pop **‘b’**, push **‘c’** on top of the stack and move to state **q<sub>2</sub>**.

