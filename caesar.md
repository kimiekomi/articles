# Caesar Cypher in Python 
<br>             

<div align="center">
<img style="float: block; margin: 0" width="350" height="400" src="caesar-image.png"> 
</div>

<br>

This article will explain how I solved one of the earliest, simplest, and most famous cyphers in history - the Caesar cypher. A Caesar cypher is an encryption technique that takes a message and substitutes each letter of the message with a different letter, a set number of positions down the alphabet. For example, with a shift or offset of 3, "A" is replaced with "D", "B" becomes "E", "C" becomes "F", and so on. When the end of the alphabet is reached, the position of the letters cycles around to the front of the alphabet. In other words, with an offset of 3, "X" then becomes "A", "Y" becomes "B", "Z" becomes "C", and such. 

<br>

A bulk of the code is simply iterating through each letter and replacing it with the corresponding letter-shift. However, some of the challenges involved:   
- accepting capitalized letters
- wrapping back to the front of the alphabet once the end is reached
- and cyphering in either directions
  
I will share how I handled each challenge below. So without furuther ado, let's dive into the code!

<br>

### Step 1: 