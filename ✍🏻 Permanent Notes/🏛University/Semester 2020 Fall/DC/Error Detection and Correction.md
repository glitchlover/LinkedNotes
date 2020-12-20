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
Def:: Humming distance is the difference between two words in the number of different corresponding bits

-   How to detect two error?
-   How to generate codewords
    -   Parity
        -   Parity code 
        -   Not good
-   How to correct the massage
-   What happened to odd and even errors
-   Two Dimension parity checker
