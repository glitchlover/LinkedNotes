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
cards-deck: "Data Communication :: ⚠ Error Detection and Correction"
---
# Error Detection and Correction
- There are two types of error :: Single bit error and Burst Error 
	- Single bit error #card 
		- if after transmission only one bit gets corrupted in one data unit then it  is called Single bit error.


	- Burst error #card
		- if after transmission only multiple bits get corrupted in one data unit then it is called  Burst error.

## Block Coding
- In block coding we divide our message :: into two blocks

	- They are::Codewords and Datawords
	
		- Codewords #card
			- We add r redundant bits to each block to make the length n = k+r. The resulting block is codewords 

		- Datawords #card
			- We divide our massage into blocks, each of k bits called datawords.

### Process of Error Detection and Block Coding 
here is how it is done #card 
![[Pasted image 20201220174923.png]]

### Hamming Distance
       
-   How to detect two error?
-   How to generate codewords
    -   Parity
        -   Parity code 
        -   Not good
-   How to correct the massage
-   What happened to odd and even errors
-   Two Dimension parity checker
