# Vigenere Cypher in Python 
<br>             

<div align="center">
<img style="float: block; margin: 0" width="400" height="300" src="vigenere-image.jpeg"> 
</div>

<br>

This article will explain how I solved the Vigenere cypher - a more advanced and evolved encryption method to the Caesar cypher. Essentially, the Vigenere technique operates by using a combination of Caesar cyphers with a keyword. However, instead of uniformly shifting each letter in a message by the same offset value, each letter is shifted based on a different character in a keyword. This keyword is repeated throughout the encryption process, until the end of the message is reached. Once each letter in the message is assigned a new character, that letter is shifted by the index of the keyword character. 

<br>

For example, let's use the message, "attack at dawn!", with the keyword, "sun". The first letter of the message would be assigned the first character of the keyword. The second letter, assigned to the second character of the keyword; the third, assigned to the third character, and so on, excluding any spaces and special characters, such as punctuations. 

<br>

        - message: attack at dawn!
        - keyword: sunsun su nsun
        - decoded: sngswx sn qsqa!

<br>

The index of "s" is 18, so the "a" would be shifted down the alphabet by 18 positions, and become "s". The index of "u" is 20, so "t" would be shifted by 20 position, and become "n". The index of "n" is 13, so the second "t" now becomes "g". Similar to the Caesar technique, when the end of the alphabet is reached, the position of the letters cycles around to the front of the alphabet and the pattern repeats itself for the length of the message.















