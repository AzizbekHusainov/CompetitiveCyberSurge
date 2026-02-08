# Encoding/Decoding Notes
## Number Bases Gym
Rapid Tables (Hex to String | Hex to ASCII Converter) is a quicker method for decoding into ASCII than by hand. Simply input the form of the code you are going to decode to the format you wish to see. Then paste the code or file where directed and clarify which character encoding option you want, then convert. Base64 Decode and Encode - Online is quite similar in the way it’s straightforward.

**Questions:**

Q1: 0x73636f7270696f6e
This text is encoded in hexadecimal. This text can be converted to ASCII by hand or by using an online tool such as RapidTables or CyberChef.
💡
Note: The 0x is used to indicate that the value is hexadecimal and should not be converted.

*A: scorpion*

**Q2: c2NyaWJibGU=**
This text is encoded in base64. You can identify this by analyzing the range of characters used in the message and recognizing that it falls within the range for base64 (A-Z, a-z, 0-9, +, /, and =). This text can be converted to ASCII by hand or by using an online tool such as Base64Decode or CyberChef.


*A: scribble*
- To decode base64 → in terminal simply decode by using command:
  - echo c2NyaWJibGU= | base64 -d
  - Scribble is the output.

**Q3: 01110011 01100101 01100011 01110101 01110010 01100101 01101100 01111001**
This text is encoded in binary. You can identify this by analyzing the range of characters used in the message and recognizing that it falls within the range for binary (0 and 1). This text can be converted to ASCII by hand or by using an online tool such as Binary Hex Converter or CyberChef.

*A: securely* 
- In kali, command to get securely decoded:
  - echo "01110011 01100101 01100011 01110101 01110010 01100101 01101100 01111001" | \
  - while read -r b; do printf "\\$(printf '%03o' $((2#$b)))"; done

**Q4: 01100010 01000111 00111001 01110011 01100010 01000111 01101100 01110111 01100010 00110011 01000001 00111101**
This text is doubly encoded - first with base64 and then with binary. To revere the process, the message has to be converted from binary to ASCII, then base64 to ASCII. You can use the Binary Hex Converter followed by Base64Decode. It’s possible to combine these two steps using CyberChef.
*A: From binary to ASCII, it is bG9sbGlwb3A=.*
*From base64 to ASCII, bG9sbGlwb3A= is lollipop.*


### Strings Gym 
*A: FLAG = SKY-TVJI-2063*
Using the strings command, I was able to extract the hidden flag (SKY-TVJI-2063) from steg1.jpg and verify it by viewing the image in hexadecimal using xxd (the same method used in Vim with :%!xxd) and searching the hex dump for the ASCII string.
- Commands:
  - strings steg1.jpg | grep SKY
  - xxd steg1.jpg | grep 534b59


#### Encoding and Decoding side challenge on linux only system:
Goal of this challenge was to recognize that even though we can delete data on storage device, it can still exist until overwritten. Deleting a file removes its filesystem reference, but the underlying data may remain on disk until overwritten, which allows forensic tools like strings to recover readable data from raw devices.
- Main commands used (no one on team had linux system and USB passthrough was unavailable in VM so I “created” a USB):
  - sudo mkfs.ext4 /dev/loop0
  - sudo mount /dev/loop0 /mnt/fakeusb
  - echo "LINDSEY_USB_TEST" | sudo tee /mnt/fakeusb/secret.txt
  - sudo rm /mnt/fakeusb/secret.txt
  - sudo umount /mnt/fakeusb
  - sudo strings /dev/loop0 | grep LINDSEY_USB_TEST


**AI Assistance Disclosure:**
Portions of the workflow explanations and Linux command usage were clarified with the help of ChatGPT (OpenAI) as a learning aid. All commands were executed and verified independently by the student.
