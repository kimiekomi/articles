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

Alright, so with that explanatin, lets dive into the code and see how I handled some of the challenges with this particular cypher. 

<br>

### Step 1: Define the function and calculate offset values
<br>

```python

def vigenere_cypher(message, keyword, action):
    if debug: print(f"vigenere_cypher() with keyword -'{keyword}'")

    message = message.strip()
    keyword = keyword.lower()

    if debug: print(f"message - '{message}', keyword - '{keyword}', action - '{action}'")

    lower_letters = "abcdefghijklmnopqrstuvwxyz"
    upper_letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
    
```
<br>

The first section of the function looks practically identical to my Caesar cypher function. Once again, I defined the function and passed in an action to determine the encryption direction. The cypher was written to accept both upper and lower case letters; however, to simplify matters, I converted the keyword to all lower case. 

<br>

```python

keyword_index = 0

offsets = []
    
    for letter in keyword:
        if action == "encode":
            offsets.append(ord(letter) - ord("a"))
        
        else:
            offsets.append(-(ord(letter) - ord("a")))

```

<br>

Since spaces and special characters will not be assigned a keyword character, I had to create a variable to keep track of the keyword index. This keyword index variable will come into play later on in the message iteration; but for starters, it is set to 0. The next order of business was to calculate the offset values of each keyword character. These values will determine the position each letter in the message would shift by. I created a empty list to store all the values, and based on the action passed in, all the values would either be positive or negative integers. 

<br>

### Step 2: Iterate through the message and obtain new index
<br>

```python

    new_message = []

    for letter in message:

        if trace: print(f"iterating through '{letter}' in message")
        
        if not letter.isalpha():
        new_message.append(letter)
        continue

        if letter in lower_letters:
        old_index = ord(letter) - ord("a")

        else:
        old_index = ord(letter) - ord("A")

        if trace: print(f"old_index = '{old_index}', offsets[keyword_index] = '{offsets[keyword_index]}', new_message - '{new_message}'")

```

<br>

As I iterated through the message, I conducted a 2-part conditional check - first, I  determined whether the letter is a special character. If it is, I simply appended it to the empty list and continued to the next letter. If the letter is indeed in the alphabet, then I had a list of items to perform which included: 

- obtaining the correct letter index based on the letter casing
- calculating the new index and apply a modulus of the alphabet length 
- appending the replacement letter based on the new index previously calculated, once again, taking into consideration the letter casing

<br>

```python

        new_index = old_index + (offsets[keyword_index] % 26)

        if new_index > 25:
            new_index -= 26

        if new_index < 0:
            new_index += 26

        if trace: print(f"new_index - '{new_index}'")

        if letter.isupper():
            new_message.append(upper_letters[new_index])

        else:
            new_message.append(lower_letters[new_index])

```

<br>

### Step 3: Repeat the keyword
<br>

```python

        keyword_index += 1

        if keyword_index >= len(keyword):
            keyword_index = keyword_index % len(keyword)

```

<br>

The main challenge to this cypher was repeating and reassigning the keyword. I did not want to assign a keyword character to spaces and special characters. Therefore, I had to index the keyword from within the loop. Earlier, the keyword index was set to 0. If the letter in question is a space or special character, then the keyword index remains the same. In the words, the keyword characater in sequence would only be assigned if the letter is in the alphabet. Furthermore, to cycle the keyword assignment and avoid an IndexError, I applied a modulus, of the length of the keyword, to the keyword index. 

<br>
























