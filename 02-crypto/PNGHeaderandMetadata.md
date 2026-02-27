
The PNG header and metadata were successfully restored using header carving, allowing the encrypted file to be recognized as a valid PNG. However, the image content remained visually
unreadable due to the encryption mode randomizing pixel data. This demonstrates that while file carving can restore file structure, 
strong encryption modes such as CBC and OFB effectively protect image contents.

How I did it:

I extracted the PNG header and metadata from the original tux-96.png file and overwrote the first 128 bytes of the encrypted image using dd with conv=notrunc.
After renaming the encrypted file with a .png extension, the file was recognized as a valid PNG, 
demonstrating that header carving can restore file structure even though the encrypted pixel data remained unreadable due to the encryption mode.

