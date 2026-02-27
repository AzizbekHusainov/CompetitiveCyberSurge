# The Book - CyberSkyline gym challenge


## What operating system was this dump taken from?

`xz -d memdump.mem.xz`

`vol2 -f memdump.mem imageinfo`

##  What is the name of the computer?

`vol2 -f memdump.mem imageinfo`

##  What is the name of the user that was logged in?

`vol2 -f memdump.mem --profile=Win10x64 envars`

##  What is the full filepath and file of the file in interest?
` vol2 -f memdump.mem --profile=Win10x64 filescan | grep "liber8hacker" `
` vol2 -f memdump.mem --profile=Win10x64_10240_17770 filescan | grep "liber8hacker"| grep ".db" `

##  What is the real name of "cloud"?
` mkdir output `
` vol2 -f memdump.mem --profile=Win10x64 dumpfiles -Q 0x0000e0003f5a9d00 -D ./output/ `
` vol2 -f memdump.mem --profile=Win10x64_10240_17770 dumpfiles -Q 0x0000e0003f5a9d00 -D ./output/ -v `
` vol2 -f memdump.mem --profile=Win10x64_10240_17770 dumpfiles --regex="black_book.db" -D ./output/ `
` vol2 -f memdump.mem --profile=Win10x64_10240_17770 handles | grep "black_book.db"  `
` strings ./output/3768.dmp | grep -i "cloud" `
` strings ./output/3768.dmp | grep -i -A 5 "CREATE TABLE" `
` strings ./output/3768.dmp | grep -i -A 2 -B 2 "cloud" | grep -v "Microsoft\|UTC\|Windows\|PROVIDERDEFINITION" `
` strings ./output/3768.dmp | grep -B 2 -A 2 "first_name\|last_name" | grep -v "CREATE\|NOT NULL\|PRIMARY\|sqlb\|INSERT\|SELECT" `
` strings ./output/3768.dmp | grep -A 5 -B 5 "UPDATE.*book.*rowid.*2\|UPDATE.*book.*rowid.*6" `
` strings ./output/3768.dmp | grep -A 50 "^visage$" | grep -v "Microsoft\|UTC\|Windows\|PROVIDER\|CREATE\|SELECT\|INSERT\|UPDATE\|PRAGMA\|INDEX\|PRIMARY\|TABLE" | head -30 `

## What is the password of the currently logged in user?

`vol2 -f memdump.mem --profile=Win10x64_10240_17770 hashdump`

 Then used [crackstation](https://crackstation.net/) to crack the hash

# Notes
 
Had issues with volatility3. This challenge was completed by volatility2.
Had to restructure some commands, so most will likely look different to what was in the prompt.
Still has the core functionality though.
The real issue was the 'cloud' name. Disclaimer: AI was used to find the real name of cloud.


