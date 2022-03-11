# Hangman in Python  
<br>             

<div align="center">
<img style="float: block; margin: 0" width="400" height="300" src="images/hangman.png"> 
</div>

<br>             

This article will explain my Python version of the classic word guessing game - Hangman. This single-player game consists of a hidden computer-generated word in which the player must reveal through guessing the letters of the word. The computer will display the length of the hidden word and the player will guess the letters individually. If the player guesses a letter that is not in the hidden word, the computer will start to draw elements of a man. In this particular version, a complete illustion of a man consists of six body parts (one head, one body, two arms and two legs). Each body part represents an incorrectly guessed letter, as no body parts are drawn for correctly guessed letters. The player loses the game if the word has *not* been guessed once all six body parts are displayed and the man is considered "hanged" (hence the name, Hangman). The

So without further ado, let's dive into the code!

<br>

### Random Word
<br>

The game starts off with a hidden word. Since this is a computer game for a solo player, this word will be randomly selected by a computer, from a word bank.  