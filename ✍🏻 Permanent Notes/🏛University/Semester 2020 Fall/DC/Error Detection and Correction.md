---
ankified?: 'no'
lecture: null
subject:
  - Computer Science
  - Digital Communication
links:
  - Linear Block Coding
tag: null
date: 'Thursday 17th, Dec 2020 (352nd)'
status:
  - ongoing
date updated: '2020-12-20T15:40:27+06:00'
cards-deck: "Digital Communication :: ⚠ Error Detection and Correction"
cards-deck: Digital Communication :: ⚠ Error Detection and Correction
^1608471049157
---
# Error Detection and Correction
- There are two types of error :: Single bit error and Burst Error 
^1608471049587
	- Single bit error #card 
		- if after transmission only one bit gets corrupted in one data unit then it  is called Single bit error.
^1608471049984


	- Burst error #card
		- if after transmission only multiple bits get corrupted in one data unit then it is called  Burst error.
^1608471050386

## Block Coding
- In block coding we divide our message :: into two blocks
^1608471050790

	- They are::Codewords and Datawords
^1608471051174
	
		- Codewords #card
			- We add r redundant bits to each block to make the length n = k+r. The resulting block is codewords 
^1608471051590

		- Datawords #card
			- We divide our massage into blocks, each of k bits called datawords.
^1608471051982

### Process of Error Detection and Block Coding 
here is how it is done #card 
![[Pasted image 20201220174923.png]]
^1608471052386

### Hamming Distance
Def::The Hamming distance between two codewords is simply the number of bit positions in which they differ.
^1608472612356

#### How to find the Humming distance
We can find humming distance using the gate . . . ::XOR
^1608472612925

##### Example
What is the humming distance d(000, 011)? #card 
- 2
- ![[Pasted image 20201220204016.png]]
^1608475246624

#### Minimum Humming Distance
if we want to find n errors then minimum humming distance is :: $d_min = n+1$
^1608472613443

#### How the codewords are generated?
- **Using parity code** ::codewords are generated such a way that every time parity checker checks the datawords gets true
^1608475246999

###  Parity 
A simple parity check code can detect which kind of error?::odd number

#### Parity Checker
What is parity check? #card 
-  Circuit that gives output ‘1’ if there is some error found and gives output ‘0’ if no error is found in the message including the parity bit.
^1608475247381


##### Even Parity Checker
def::In a circuit if even number 1 is found on input then that is called Even parity checker and its true 
^1608475247759

In even parity checker if the error bit (E) *is equal to ‘1’, then we have an error.* If error bit E=0 then indicates there is no error. What does this means? #card
>Error Bit (E) =1, error occurs
>Error Bit (E) =0, no error
^1608475248139

##### Odd Parity Checker
def::In a circuit if odd number 1 is found on input then that is called Odd parity checker and its true 
^1608475248539

In odd parity checker if an *error bit (E) is equal to ‘1’, then it indicates there is no error.* If an error bit E=0 then indicates there is an error. What does this means? #card 
>Error Bit (E) =1, no error
>Error Bit (E) =0, error occurs       
^1608475248937

#### Encoder and decoder for simple parity check code
here is how it is done #card
![[Pasted image 20201221102235.png]]


### Linear Block Coding
def::A linear block code is a code in which exclusive or (addition modulo-2) of two valid codewords creates another valid codewords 

