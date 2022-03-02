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

The first section of the function looks practically identical to my Caesar cypher function. Once again, I defined the function and passed in an action to determine the encryption direction. The cypher was written to accept both upper and lower case letters; however, to simplify matters, I converted the keyword to all lower case. Now, this is where the intricacy of the code begins. 

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

Since spaces and special characters will not be assigned a keyword character, I had to create a variable to keep track of the keyword index. This keyword index variable will come into play later on in the message iteration; but for starters, it is set to 0. The next order of business was to calculate the offset values of each keyword character. I created a empty list to store all the values, and based on the action, all the values would either be positive if the action was set to "encode", or negative values if the action was set to "decode". 

<br>

### Step 2: Iterate through each letter in the messagee
<br>

```python

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











