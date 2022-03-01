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

### Step 1: Define function with parameters
<br>

```

def caesar_cypher(message, offset, action):
    if debug: print(f"caesar_cypher() with offset - {offset}")

    message = message.strip()

    if debug: print(f"message = '{message}'")

    if action == "decode":
        offset = -(offset)

```
<br>

Right from the start I decided to handle cypher directions by passing in a separate parameter - action. Upon calling the function, if action was set to "encode", then the cypher would move in the positive direction. If action was set to "decode", then the cypher would work backwards, respectively, by setting the offset value to a negative integer.   

<br>

### Step 2: Iterate through each letters
<br>

```

new_message = []

    for letter in message:

        if trace: print(f"iterating through '{letter}' in message")

        if not letter.isalpha():
            new_message.append(letter)

        else:
            if letter in lower_letters:
                old_index = ord(letter) - ord("a")

            else:
                old_index = ord(letter) - ord("A")

            if trace: print(f"old_index = {old_index}")

```
<br>

Next, I created an empty list (because lists are easier to manipulate than strings) to store the new letter replacements. Now the questions to answer is, whether or not the letter in the message is in the alphabet. If it is a special character, say a punctuation, then I will not manipulate it and simply add it, as is, to the empty list. If it is indeed in the alphabet, then I need to know whether or not the letter in question is capitalized. I elected to use Python's built-in ord() function instead of the index() function,  
