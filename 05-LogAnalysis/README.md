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
2. Command: `cat squid_access.log | awk 'print $2' | sort -n` then grab the first number for the fastest time. Answer: `5`
3. Same command as problem 2 but grab the last number Answer: `41762`
4. Command: `cat squid_access.log | awk '{print$3}' | sort | uniq | wc -l` Answer: `4`
5. Command: `cat squid_access.log | grep GET | wc -l` Answer: `35`
6. Run same command as question 5 but grep for POST. Answer: `78` 
7. Run command `cat squid_access.log | grep 192.168.0.224` Answer: `Symantecliveupdate`
8. Run same command as question 7. Answer: `http://liveupdate.symantecliveupdate.com/streaming/norton$202009$20streaming$20virus$20definitions_1.0_symalllanguages_livetri.zip`
