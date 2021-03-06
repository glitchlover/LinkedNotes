---
ankified?: 'no'
lecture: null
subject: null
tag: null
date: Monday 21st, Dec 2020 (356th)
status:
  - ongoing
cards-deck: Theory of Computation::Pushdown Automata
---
<iframe src="https://www.youtube.com/embed/4ejIAmp_Atw" class="resize-vertical" style="height: 505px;"></iframe>

# Pushdown Automata
def:: A pushdown automaton is a way to implement a context-free grammar in a similar way we design DFA for a regular grammar. 
^1608565478911

A DFA can remember a finite amount of information, but a PDA can remember....:: an infinite amount of information.
^1608565479308
---
- What kind of stack PDA is?:: ε-NFA
^1608565479715

-  What kind of NFA PDA is?:: ε-NFA with a stack
^1608565480111


---

## Basic Components
A pushdown automata has three components #card 
![[Pasted image 20201221212617.png]]
- An input tape (which is like a input string)
- A finite control unit
- A stack with infinite size
^1608565480499

The stack head scans what?::the top symbol of the stack.
^1608565480902

## Formal Definition
A PDA can be formally described as a ___ tuple :: 7-tuple (Q, ∑, S, δ, q<sub>0</sub>, I, F) 
^1608565481279

The 7 tuple are #card 
- **Q** is the finite number of states
- **∑** is input alphabet
- **S** is stack symbols
- **δ** is the transition function: Q × (∑ ∪ {ε}) × S × Q × S\*
- **q<sub>0</sub>** is the initial state (q<sub>0</sub> ∈ Q)
- **I** is the initial stack top symbol (I ∈ S)
- **F** is a set of accepting states (F ∈ Q)
^1608565481655

## Transition Function
Transition function takes ... arguments :: 3
^1608565482135

The arguments of transition function are #card 
1. A state, in Q.
2. An input, which is either a symbol in Σ or ε.
3. A stack symbol in Γ.
^1608565482534
  
δ(q, a, Z) -> (p, α). Explain #card 
- p is a new state;
-  α is a string of stack symbols that replaces Z at the top of the stack
- ![[Pasted image 20201222140652.png]]
^1608635708172

### Example
The following diagram shows a transition in a PDA from a state q<sub>1</sub> to state q<sub>2</sub>, labeled as a,b → c. What are a,b and c are? #card 
![https://www.tutorialspoint.com/automata_theory/images/transition_in_a_pda.jpg](https://www.tutorialspoint.com/automata_theory/images/transition_in_a_pda.jpg)
This means at state *$q_1$*, if we encounter an input string **‘a’** and top symbol of the stack is **‘b’**, then we pop **‘b’**, push **‘c’** on top of the stack and move to state *$q_2$.*
^1608565482908
----

### Action of PDA
- In δ(q, a, Z) contains (p,α) and the stack 
	- if α = ε then stack is :: poped
^1608635708686
	- if α = Z then stack is :: unchanged
^1608635709161
	- if α = YZ then Stack is:: replaced and y and z is pushed 
^1608635709687

### Graphical Notation of pushdown automata #card
<iframe src="https://www.youtube.com/embed/eY7fwj5jvC4" class="resize-vertical" style="height: 505px;"></iframe>

![[Pasted image 20201222142740.png]]
```(A)===|a,b → c|===(B)```  What does a, b and c means? #card 
a = Input Symbol
b = top of the  stack
c = push character

