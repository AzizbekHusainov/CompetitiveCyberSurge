# Number Bases
An encrypted string starting with **0x** is in hexadecimal.
1. 0x73636f7270696f6e -> "scorpion"

If an encrypted string has letters in both cases, it is likely in base64.

2. c2NyaWJibGU= -> "scribble"

If an encrypted string is made of 1s and 0s, it is in binary.

3. 01110011 01100101 01100011 01110101 01110010 01100101 01101100 01111001 -> "securely"
4. 01100010 01000111 00111001 01110011 01100010 01000111 01101100 01110111 01100010 00110011 01000001 00111101 -> bG9sbGlwb3A= -> "lollipop"

# Shift (ROT13/Cesarian Cipher)
The _Cesarian Cipher_ is a basic encryption cipher that shifts the alphabet 13 letters.
|          | | | | | | | | | | | | | | | | | | | | | | | | | | |
|----------|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
|**input** |A|B|C|D|E|F|G|H|I|J|K|L|M|N|O|P|Q|R|S|T|U|V|W|X|Y|Z|
|**output**|N|O|P|Q|R|S|T|U|V|W|X|Y|Z|A|B|C|D|E|F|G|H|I|J|K|L|M|
1. iveghny ynxr -> "virtual lake"

# @bash (Atbash)
The _Atbash Cipher_, when applied to the Latin alphabet, simply reverses the alphabet.
|          | | | | | | | | | | | | | | | | | | | | | | | | | | |
|----------|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
|**input** |A|B|C|D|E|F|G|H|I|J|K|L|M|N|O|P|Q|R|S|T|U|V|W|X|Y|Z|
|**output**|Z|Y|X|W|V|U|T|S|R|Q|O|P|M|N|L|K|J|I|H|G|F|E|D|C|B|A|
1. hzuvob lyerlfh xzev -> "safely obvious cave"

# Beep (Morse)
_Morse Code_ is a method of reducing English letters to simple combinations of two lengths of pulse, sorted by frequency.

|          | | | | | | | | | | | | | | | | | | | | | | | | | | |
|----------|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|-|
|**input** |A|B|C|D|E|F|G|H|I|J|K|L|M|N|O|P|Q|R|S|T|U|V|W|X|Y|Z|
|**output**| .- |-...|-.-.| -..|  . |..-.| --.|....| .. |.---| -.-|.-..| -- | -.| ---|.--.|--.-| -.-| ...|  - | ..-|...-| .--|-..-|-.--|--..|
1. - .... . / ... . -.-. .-. . - / --- ..-. / --. . - - .. -. --. / .- .... . .- -.. / .. ... / --. . - - .. -. --. / ... - .- .-. - . -.. / ... -.- -.-- / -.. -.- ...- -... / ----. ---.. .---- -.... -> THESECRETOFGETTINGAHEADISGETTINGSTARTEDSKYDKVB9816 -> **SKY-DKVB-9816**
  
# Fencing (Rail-Fence)
# French (Vignere)
# Strings
# RSA
