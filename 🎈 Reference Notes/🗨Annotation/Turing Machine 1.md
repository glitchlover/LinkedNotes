----

----
page: 2
type: text-highlight
created: 2020-12-17T11:46:37.811Z
color: #9900EF

Devices of Increasing Computational Power

----
page: 2
type: text-highlight
created: 2020-12-17T11:47:06.914Z
color: yellow

Finite Automata
----
page: 2
type: text-highlight
created: 2020-12-17T11:47:09.930Z
color: yellow

Pushdown Automata

----
page: 2
type: text-highlight
created: 2020-12-17T11:47:14.474Z
color: yellow
both have limitations for even simple tasks, too restrictive as general purpose computers

----
page: 2
type: text-highlight
created: 2020-12-17T11:47:19.059Z
color: yellow
Enter the Turing Machine

----
page: 2
type: text-highlight
created: 2020-12-17T11:47:25.252Z
color: yellow
– More powerful than either of the above 
– Essentially a finite automaton but with unlimited memory 
– Although theoretical, can do everything a general purpose computer of today can do

----
page: 2
type: text-highlight
created: 2020-12-17T11:47:34.844Z
color: yellow

If a TM can’t solve it, neither can a compute

----
page: 4
type: text-highlight
created: 2020-12-17T11:47:43.578Z
color: #9900EF
The Turing Machine

----
page: 4
type: text-highlight
created: 2020-12-17T11:49:26.156Z
color: yellow
==the Turing machine —  was this:==

----
page: 4
type: text-highlight
created: 2020-12-17T11:49:29.157Z
color: yellow
==(1) A tape of infinite length==

----
page: 4
type: text-highlight
created: 2020-12-17T11:49:39.656Z
color: yellow
==(2) Finitely many squares of the tape have a single symbol from a finite language.
==

----
page: 4
type: text-highlight
created: 2020-12-17T11:49:45.790Z
color: yellow
==(3) Someone (or something) that can read the squares and write in them.==

----
page: 4
type: text-highlight
created: 2020-12-17T11:49:56.071Z
color: yellow
==(4) At any time, the machine is in one of a finite number of internal states.==

----
page: 4
type: text-highlight
created: 2020-12-17T11:50:09.856Z
color: yellow
==(5) The machine has instructions that determine what it does given its internal state and the symbol it encounters on the tape==

----
page: 4
type: text-highlight
created: 2020-12-17T11:50:18.074Z
color: yellow
==It can 
 change its internal state;
 change the symbol on the square; 
 move forward; 
 move backward; 
 halt (i.e. stop).==

----
page: 6
type: text-highlight
created: 2020-12-17T11:51:20.425Z
color: #9900EF
Can Machines Think?
----
page: 6
type: text-highlight
created: 2020-12-17T11:51:28.456Z
color: yellow
In “Computing machinery and intelligence,” written in 1950, Turing asks whether machines can think
----
page: 6
type: text-highlight
created: 2020-12-17T11:51:38.783Z
color: yellow
That question is: Can machines pass the “imitation game” (now called the Turing test)?
----
page: 7
type: text-highlight
created: 2020-12-17T11:51:48.324Z
color: #9900EF
The Turing Test
----
page: 7
type: text-highlight
created: 2020-12-17T11:52:41.172Z
color: yellow
If you can’t distinguish between a human being  and a computer from your interactions, then the computer is intelligent.
----
page: 9
type: text-highlight
created: 2020-12-17T11:52:54.099Z
color: #9900EF
A Turing Machine
----
type: area-highlight
created: 2020-12-17T11:53:00.565Z
color: 
image: ![](https://storage.googleapis.com/polar-32b0f.appspot.com/image/129NVrivfshKKYPrnbuGuJp74LENBkkDY3N1SYy8.png
)

----
page: 11
type: text-highlight
created: 2020-12-17T11:53:32.103Z
color: yellow
==The head at each time step:==

----
page: 11
type: text-highlight
created: 2020-12-17T11:53:34.710Z
color: yellow
==1. Reads a symbol==

----
page: 11
type: text-highlight
created: 2020-12-17T11:53:37.283Z
color: yellow
==2. Writes a symbol==

----
page: 11
type: text-highlight
created: 2020-12-17T11:53:39.955Z
color: yellow
==3. Moves Left or Right==

----
page: 19
type: text-highlight
created: 2020-12-17T11:54:12.688Z
color: #9900EF
==Turing-Machine Formalism==
----
page: 19
type: text-highlight
created: 2020-12-17T11:54:18.084Z
color: yellow
==A TM is described by 07 tuples:==
----
page: 19
type: text-highlight
created: 2020-12-17T11:54:22.432Z
color: yellow
M = (Q, , , , ΣΓδ q 0 , B, F)
----
page: 19
type: text-highlight
created: 2020-12-17T11:54:27.980Z
color: yellow
==1. A finite set of states==
----
page: 19
type: text-highlight
created: 2020-12-17T11:54:31.196Z
color: yellow
==2. An input alphabet==
----
page: 19
type: text-highlight
created: 2020-12-17T11:54:34.084Z
color: yellow
==3. A tape alphabet==
----
page: 19
type: text-highlight
created: 2020-12-17T11:54:39.820Z
color: yellow
==4. A transition function==
----
page: 19
type: text-highlight
created: 2020-12-17T11:54:43.165Z
color: yellow
==5. A start state==
----
page: 19
type: text-highlight
created: 2020-12-17T11:54:46.108Z
color: yellow
==6. A blank symbol==
----
page: 19
type: text-highlight
created: 2020-12-17T11:54:48.869Z
color: yellow
==7. A set of final states==
----
page: 20
type: text-highlight
created: 2020-12-17T11:54:55.850Z
color: #9900EF
Conventions
----
page: 20
type: text-highlight
created: 2020-12-17T11:54:59.355Z
color: yellow
a, b, ... are input symbols.
----
page: 20
type: text-highlight
created: 2020-12-17T11:55:02.549Z
color: yellow
.. , X, Y, Z are tape symbols.
----
page: 20
type: text-highlight
created: 2020-12-17T11:55:07.505Z
color: yellow
... , w, x, y, z are strings of input symbols
----
page: 20
type: text-highlight
created: 2020-12-17T11:55:11.237Z
color: yellow
 ,  ,... are strings of tape symbols.
----
page: 21
type: text-highlight
created: 2020-12-17T11:55:20.645Z
color: #9900EF
The Transition Function
----
page: 21
type: text-highlight
created: 2020-12-17T11:55:35.885Z
color: yellow
==Takes two arguments: 1. A state, in Q. 2. A tape symbol in Γ .==
----
page: 21
type: text-highlight
created: 2020-12-17T11:56:03.167Z
color: yellow
==δ (q, Z) is either undefined or a triple of the form (p, Y, D).==
----
page: 22
type: text-highlight
created: 2020-12-17T11:56:22.517Z
color: #9900EF
Actions of the PDA
----
page: 22
type: text-highlight
created: 2020-12-17T11:56:47.429Z
color: yellow
If δ (q, Z) = (p, Y, D) then, in state q, scanning Z under its tape head, the TM: 1. Changes the state to p . 2. Replaces Z by Y on the tape . 3. Moves the head one square in direction D.  D = L: move left ; D = R; move right .
