# Hangman in Python  
<br>             

<div align="center">
<img style="float: block; margin: 0" width="400" height="300" src="images/hangman.png"> 
</div>

<br>             

This article will explain my Python version of the classic word guessing game - Hangman. This single-player game consists of a hidden computer-generated word in which the player must reveal through guessing the letters of the word. The computer will display the length of the hidden word and the player will guess the letters individually. If the player guesses a letter that is not in the hidden word, the computer will start to draw elements of a man. In this particular version, a complete illustion of a man consists of six body parts (1 head, 1 body, 2 arms and 2 legs). Each body part represents an incorrectly guessed letter, as no body parts are drawn for correctly guessed letters. The player loses the game if the word has *not* been guessed once all 6 body parts are displayed and the man is considered "hanged" (hence the name, Hangman).

<br>

The main aspect of the code simply compares the user input with the letters in the hidden word. However, the code was divided into various components of the game which included:

- generating a random word for player to guess
- printing the status of the word (i.e. which letters have been guessed)
- displaying the hanged man depiction
- prompting the user for letter guesses
- and comparing the guessed letter with the letters in the word
  
Each component resides in it's separate function, with a main funtion that incorporates all aspects of the game. I will describe the specifics of each component below. So without further ado, let's dive into the code!

<br>

### Generate Random Word
<br>

```python

def random_word(list):

    if debug: print(f"initialized random_word()")

    hidden_word = random.choice(list)

    if "-" in hidden_word:
        hidden_word = random.choice(list)

    if debug: print(f"hidden_word - {hidden_word}")

    return hidden_word


def word_status(word):
    word_state = ""

    for character in word:
       word_state += "_" 

    return word_state

```
<br>

My first task was to create a list of words, which I stored in a separate file (for potential reuse with a different application or game at a later time). I then used Python's built-in ```random.choice()``` method, to arbitraly select a word for the game. At the initialization of the game, each letter of the hidden word will be displayed as blank lines, since none of the letters have been guessed yet. As the game proceeds, the letter will only be revealed when it is correctly guessed. 

<br>

### Prompt for User Input
<br>

```python

def prompt_user():

    while True: 
        guess_letter = input("Guess a letter: ")

        if not guess_letter.isalpha():
            print(">>> Enter a valid letter")
            continue

        if len(guess_letter) > 1:
            print(">>> Enter only one letter")
            continue

        break

    if debug: print(f"guess_ letter - {guess_letter}")

    return guess_letter

```
<br>

This game is played from the command line, where users will enter their letter guesses. Exception handling is achieved at this stage, as the game does not accept integers or special character inputs. Additionally, players are only allowed to enter one letter at a time. Each of the above scenarios will result in a prompt for the user to submit a valid letter-entry. 

<br>

### Compare Letters 
<br>

```python

def letter_compare(secret_word, correct_letters):

    if debug: print (f"letter_compare (secret_word={secret_word}, {correct_letters})")

    new_state = ""

    for letter in secret_word:

        if letter in correct_letters:
            new_state += letter.lower ()
        else:
            new_state += "_"

    if debug: print(f"new_state - {new_state}")

    return new_state

```
<br>

After obtaining a user input, I compared the guessed letter with each character in the hidden word. If the hidden word contains the guessed letter, then the previously blanked line(s) will be replaced with the letter. This function ultimately returns the new status of the hidden word, with only the correctly guessed letters revealed. Furthermore, letter guesses are tracked after each turn, by including them in either the "correct guesses" or "incorrect guesses" string to prevent users from repeatedly entering the same letter. If the player enters a previously guessed letter, the player will be prompted to submit a different entry. 

<br>

### Depict Hangman Status 
<br>

```python

def attempt_status(attempts_remaining):
    ...

    if attempts_remaining == 2:
        return """Attempts remaining: X X\n
            x-------x
            |       |
            |       0
            |      /|\\
            |
            |
            """
    ...

    else:
        return """Attempts remaining: None\n
            x-------x
            |       |
            |       0
            |      /|\\
            |      / \\
            |

            GAME OVER
                """

```
<br>

I created a variable to track the number of attempts remaining in the game. After each round, if the player correctly guesses a letter, the attempt status will remain unchanged. However, if a letter was incorrectly guessed, then the player will lose an attempt. Additionally, an illustration of the game or hanged man status will be displayed after each attempt. This is done through a simple if/else statement that assigns each attempt status to a specific drawing. The game is over when either occurs: 1) all the letters in the hidden word have been guessed or 2) the player has exhausted all 6 attempts, at which point the entire hidden word will be revealed. 

<br>

So there you have it, folks - a simple command line interface (CLI) Hangman game written in Python! In my next article, I will review my Wordle code, which is based off the Hangman game, but has a couple varying elements. The entirety of my Hangman code is available on [GitHub](https://github.com/kimiekomi/hangman). Thanks for reading and as always, Happy Coding!

<br>