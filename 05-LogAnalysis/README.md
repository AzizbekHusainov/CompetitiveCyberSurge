### VSFTPD
1. Utilize cat to look at the file and pipe into grep to search through the log file for that specific user. Ex: `cat file.log | grep user | head` Answer: `10.0.0.123`
2. You can grep mkdir. Ex: `cat file.log | grep mkdir | head` Answer: `/home/ftpuser/TreeSizeFree`
3. Grep mkdir again but pipe to tail. Ex: `cat file.log | grep mkdir | tail` Answer: `/home/ftpuser/110D300S`
4. Analyze the log file and utilize grep, awk, sort, and uniq accordingly to parse. Command: `cat vsftpd.log | grep ftpuser | grep 'OK UPLOAD' | awk -F ',' '{print $2 }' | awk -F "." '{print $2}' | sort | uniq -c | sort` Answer: `JPG`
5. Same approach as problem 4. Command: `cat vsftpd.log | awk '{print $8}' | sort | uniq` Answer: `Jimmy`
6. Command: cat vsftpd.log | grep jimmy | grep LOGIN | awk '{print $12}' Answer: 10.0.0.214
7. 
