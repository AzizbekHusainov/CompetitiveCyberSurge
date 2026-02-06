# CyberChef & quipqiup

## CyberChef
[CyberChef](https://gchq.github.io/CyberChef/) is a browser-based software that allows for the encryption/decryption of data, allowing for a sequential "recipe" of methods. It is *extremely* thorough, and features methods beyond simple text ciphers. The text ciphers or hash bruteforcing "ingredients" (this software enjoys using cooking terms) are likely going to be the most used options for completing gyms, where passwords or somesuch are encrypted, even if it's just one step on the staircase to the endpoint. There may be some strategic approach to encrypting our own passwords for things, if those are necessary. One notable ingredient is the "magic" operation, which essentially bruteforces various decryption methods. However, I'm concerned that it might take issue with multi-step encoding.

### Usage
As complex and thorough as the program is, operation is simple.

1. Write some text or insert a file into the panel labelled **Input**.
2.  Navigate the list for the desired method.
3. Drag the method into the **Recipe** panel.
    
    3a. "Ingredients" are applied sequentially, top-to-bottom. If you're doing something with a lot of steps, you're able to set breakpoints by selecting the pause button on the ingredient.
4. If the **Auto-Bake** option is not activated, press the big green **Bake** button.

### Local Install?
CyberChef does have a downloadable standalone version. There are some calls outlined on the download panel that connect to external services like Wikimedia or an HTTP server, so if you choose to run it there may be some network configuration necessary.

## quipqiup
[quipqiup](https://quipqiup.com/) is a much simpler tool designed for solely text ciphers. Paste or enter your text into the textbox labelled **Puzzle** and the information that you know in the **Clues** textbox, formatted like `[e]=[d]`, where `e` is an encrypted character or string and `[d]` is the decrypted character or string.
