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
The _rail-fence_ cipher is about moving diagonally on rails. The provided key is how many rails there are.
1. (key = 3) Cair eruSA-0org sgaeudrpesr K-II98.ue cn seYQ3 -> Courage is grace under pressure **SKY-AIQI-9380**.
   ```
   C   a   i   r       e   r   u   S   A   -   0 
    o r g   s g a e u d r p e s r   K - I I 9 8 .
     u   e       c   n       s   e   Y   Q   3
   ```
2. (key = 5) F daS-eefn  n KZ3eheadty.YI8lta oiwy-Q0. r aI2 -> Feel the fear and do it anyway. **SKY-IQIZ-3802**.
   ```
   F               d       a       S       -     
    e     e f     n         n       K     Z 3    
     e   h   e   a   d   t   y   .   Y   I   8   
      l t     a       o i     w y     - Q     0 .
               r               a       I       2
   ```
# French (Vignere)
The _vignere_ cipher uses a key to encode text. Think of it as coordinates. Use the row for the *n*th letter of the key, and in that row find the encoded letter. The associative column is the decoded letter.

![vignere decode table](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/347ba7c1-3eb6-476c-94b4-3658d861eebb/image/w=1920,quality=90,fit=scale-down)

1. Y ln xkv lubj swlzqvkht, A vmzb pjk bbua we ddgs ILQ-GQYU-8026 (key = QIZKWCGQBS) -> i do not fear computers, i fear the lack of them **sky-qizk-8026**.
# Strings
To do this one, use the linux command `strings` to get the image as text. To find the key, pipe the `strings` output into a `grep` for `SKY `
1. ![leaves with a hidden key](https://cyberskyline.com/artifact/69838443ad476b082c7a0449/69690a38f845cf0a7e6d8b81/65b01563ad4ea5fef1fce4ac/65b01566ad4ea5fef1fce5c7/65b01566ad4ea5fef1fce5c9/download?t=1)

   **SKY-TVJI-2063**
# RSA
RSA encryption requires some math. One of the values of the public key, _n_, is the product of two prime numbers, _p_ and _q_. We need a third value, _d_, which can be found by

$`d=\frac{1\mod(p-1)(q-1)}{e}`$

After we get that, for each value in the encoded text _c_ at position _x_, use

$`m_{x}=c_{x}^{d}\mod(n)`$

1. _p_ = 13 (smaller prime)
2. _q_ = 83 (larger prime)
3. **SKY-KRYG-5530**
