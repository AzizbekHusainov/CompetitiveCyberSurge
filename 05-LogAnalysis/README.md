### VSFTPD
1. Utilize cat to look at the file and pipe into grep to search through the log file for that specific user. Ex: `cat file.log | grep user | head` Answer: `10.0.0.123`
2. You can grep mkdir. Ex: `cat file.log | grep mkdir | head` Answer: `/home/ftpuser/TreeSizeFree`
3. Grep mkdir again but pipe to tail. Ex: `cat file.log | grep mkdir | tail` Answer: `/home/ftpuser/110D300S`
4. Analyze the log file and utilize grep, awk, sort, and uniq accordingly to parse. Command: `cat vsftpd.log | grep ftpuser | grep 'OK UPLOAD' | awk -F ',' '{print $2 }' | awk -F "." '{print $2}' | sort | uniq -c | sort` Answer: `JPG`
5. Same approach as problem 4. Command: `cat vsftpd.log | awk '{print $8}' | sort | uniq` Answer: `Jimmy`
6. Command: `cat vsftpd.log | grep jimmy | grep LOGIN | awk '{print $12}'` Answer: `10.0.0.214`
7. This problem requires you to use `awk '{s+=$1} END {print s}'` which basically creates a variable and adds the value in the first field. Command: `cat vsftpd.log | grep jimmy | grep 'OK UPLOAD' | awk -F ',' '{print  $3 }'` | awk '{s+=$1} END {print s}' Answer: `105750628 bytes`
8. Command `cat vsftpd.log | grep ftpuser | grep 'OK UPLOAD' | awk -F ',' '{print  $3 }' | awk '{s+=$1} END {print s}'` Answer: `13980839165 bytes`
9. Command: cat vsftpd.log | grep ftpuser | grep 'OK DOWNLOAD' | awk -F ',' '{print  $3 }' | awk '{s+=$1} END {print s}' Answer: `6008032 bytes`
10. Command: `cat vsftpd.log | grep 'OK LOGIN' | awk -F '"' '{print $2 }' | sort | uniq` Answer: `10.3.0.6`

### History

We will be using sqlite3 for data query provided in Cyber Skyline terminal. To use command line tool use the command `sqlite3 browser.sqlite`. Command `.tables` shows all available tables and you can use sql queries accordingly. It is stated that moz_places is a location where urls are often stored. Use command `PRAGMA table_info(moz_places);` to look at columns and table structure.

1. Since we found urls in moz_places use command `select url from moz_places;` Answer: `bitcoin`
2. Command: `select * from moz_places where title like '%$%';` Answer: `239.5`
3. Command: `select url from moz_places;` Answer: `coinbase`
4. Command: `select * from moz_places where title like '%gmail%';` Answer: `b1gbird@gmail.com`
5. Command: `select url from moz_places;` Scroll and look for blockchain.info/search/. Answer: `5274cfba585a4b5681527a37f95c76340428916bb7480cef6c545f0a28dcd2d7`
6. Look through urls from moz_places using command `select url from moz_places;` Then scroll until you see `https://blockchain.info/tx/5274cfba585a4b5681527a37f95c76340428916bb7480cef6c545f0a28dcd2d7?show_adv=true`. This url was obtained by smart trial and error. After clicking on the link and scrolling down you will find the answer of `0.22616302 BTC`
7. Use the same url from question 6 and locate the answer of `18z6bTFjxkXCmhfp8YBetR2wgmoVjXGJZz`

### Squid

1. Command: `head squid_access.log` grab the first field containing a decimal number and run `date -d @thatnumber` this will give you the saved time. Answer: `2010`
2. Command: `cat squid_access.log | awk '{print $2}' | sort -n` then grab the first number for the fastest time. Answer: `5`
3. Same command as problem 2 but grab the last number Answer: `41762`
4. Command: `cat squid_access.log | awk '{print$3}' | sort | uniq | wc -l` Answer: `4`
5. Command: `cat squid_access.log | grep GET | wc -l` Answer: `35`
6. Run same command as question 5 but grep for POST. Answer: `78` 
7. Run command `cat squid_access.log | grep 192.168.0.224` Answer: `Symantecliveupdate`
8. Run same command as question 7. Answer: `http://liveupdate.symantecliveupdate.com/streaming/norton$202009$20streaming$20virus$20definitions_1.0_symalllanguages_livetri.zip`

### SSH

1.	Utilize cat to look at the ssh.log, which shows the whole file, and a pipe to send an output to another command, and use head, which shows the first 10 lines. Ex: cat ssh.log | head. Answer: My raptor
2.	Identifying the IP addresses that had failed login attempts and extracting the attacking IP address. Example: grep "Failed password" ssh.log | awk '{print $11}' | awk '!seen[$0]++' | head -1. Answer:169.139.243.218
3.	Identifying the IP addresses that had failed login attempts and extracting the attacking IP address for the second attempt. Example: grep "Failed password" ssh.log | awk '{print $11}' | awk '!seen[$0]++' | sed -n '2p'. Answer: 56.13.188.38
4. Identifying the IP addresses that had failed login attempts and extracted the attacking IP address for the Third attempt. Example: grep "Failed password" ssh.log | awk '{print $11}' | awk '!seen[$0]++' | sed -n '3p' .Answer:30.167.206.91
5.	 Extracted usernames from the login attempts using the logs. Example: grep "Failed password" "auth_(2).log" | head. Answer: Harvey

### Login

1.	Get the line count of the log. Example: cat login.log | wc -l. Answer:6063
2. Extract the third field (with the usernames) of the log, sort the usernames, get the unique usernames, and then get a line count of the number of unique usernames. Example: cat login.log | cut -f 3 | sort | uniq | wc -l. Answer:1879
3. Extract the same third field (with the usernames) of the log, sort the usernames, get the unique usernames, and then get a line count of the number of unique usernames. Example: cat login.log | cut -f 3 | sort | uniq | wc -l.Answer: nonstory
4. Extract the same third field (with the usernames) of the log, sort the usernames, get the unique usernames, and then get a line count of the number of unique usernames. Example: cat login.log | cut -f 3 | sort | uniq | wc -l. Answer:
5. Extract the first field (with the date+time) of the log, extract just the date, sort the dates, get a frequency count of each unique date, and then sort the unique dates by frequency. Example: cat login.log | cut -f 1 | cut -d " " -f 1 | sort | uniq -c | sort -n. Answer:2011-03-23
6. Extract the second field (with the Ip address) and third field (with the username) of the log, sort the Ip/username pairs, get the unique Ip/username pairs, then extract just the usernames from each pair, sort the usernames, get a frequency count of how many unique pairs each username has, and then sort by frequency. Example: cat login.log | cut -f 2,3 | sort | uniq | cut -f 2 | sort | uniq -c | sort -n.Answer:nongae80

### NGINX

1. Extract the first field (with the IP addresses), sort the IP addresses, get the unique IP addresses, and then get a line count. Example: cat access.log | cut -d " " -f 1 | sort | uniq | wc -l. Answer:47
2. Extract the third field (with the IP addresses), sort the IP addresses, get the unique values with a count of the occurrences of each IP address, and then sort in descending numeric order. Example: cat access.log | cut -d '"' -f 3 | cut -d ' ' -f 2 | sort | uniq -c | sort -rn. Answer:19
3. Extract the third field (with the IP addresses), sort the IP addresses, get the unique values with a count of the occurrences of each IP address, and then sort in descending numeric order Example: cat access.log | cut -d '"' -f 3 | cut -d ' ' -f 2 | sort | uniq -c | sort -rn. Answer: 38
4. Search the log for any lines that contain “bell.” Example: cat access.log | grep "bell"
 Answer:186.64.69.141
5. Search the log for any lines that contain “Googlebot”. Example: cat access.log | grep "Googlebot" Answer: 2.1
6. Search the log for any lines that contain () { :; }; . Example: cat access.log | grep '() { :; };’.  Answer:61.160.212.172
7 Search the log for all lines that contain “Firefox” and the following characters, which make up the version number, sort those values, and then get a unique count. Example: cat access.log | egrep -o "Firefox/.*" | sort | uniq -c. Answer: 3.6.28
8. Extract the 6th field (with the HTTP method), sort, get the unique values with a count of the occurrences of each value, and then sort in descending numeric order. Example: cat access.log | awk -F " " '{print $6}' | sort | uniq -c | sort -rn. Answer: GET
9. Extract the 6th field (with the HTTP method), sort, get the unique values with a count of the occurrences of each value, and then sort in descending numeric order. Example: cat access.log | awk -F " " '{print $6}' | sort | uniq -c | sort -rn. Answer: CONNECT
10. Search the log for all lines that contain that sequence of characters and then get a line count. Example: cat access.log | grep '\\x04\\x01\\x00P\\xC6\\xCE\\x0Eu0\\x00' | wc -l. Answer: 6

### Payments

1. Used Kali to count the number of lines that start with PPAPIService: Request: using grep. Example grep -c "^PPAPIService: Request:" payments.log. Answer:192
2. Used Google Sheets, sorted the request by the order total column to find the largest purchase, then got the transaction ID from the corresponding response. Example: Made in the spreadsheet. Answer: 3a4da8c8-6934-4655-9ec5-335ab4540a2b
3. Used Google Sheets and got a count of the unique values for the state of the ship-to address. Example: on the spreadsheet. Answer: MT

