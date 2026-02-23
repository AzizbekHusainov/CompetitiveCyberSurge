
(Used Kali for all the exercises)
SSH 

1.	Utilize cat to look at the ssh.log, which shows the whole file, and a pipe to send an output to another command, and use head, which shows the first 10 lines. Ex: cat ssh.log | head. Answer: My raptor

2.	Identifying the IP addresses that had failed login attempts and extracting the attacking IP address. Example: grep "Failed password" ssh.log | awk '{print $11}' | awk '!seen[$0]++' | head -1. Answer:169.139.243.218

3.	Identifying the IP addresses that had failed login attempts and extracting the attacking IP address for the second attempt. Example: grep "Failed password" ssh.log | awk '{print $11}' | awk '!seen[$0]++' | sed -n '2p'. Answer: 56.13.188.38


   4. Identifying the IP addresses that had failed login attempts and extracted the attacking IP address for the Third attempt. Example: grep "Failed password" ssh.log | awk '{print $11}' | awk '!seen[$0]++' | sed -n '3p' .Answer:30.167.206.91

5.	 Extracted usernames from the login attempts using the logs. Example: grep "Failed password" "auth_(2).log" | head. Answer: Harvey

Login:

1.	Get the line count of the log. Example: cat login.log | wc -l. Answer:6063
2. Extract the third field (with the usernames) of the log, sort the usernames, get the unique usernames, and then get a line count of the number of unique usernames. Example: cat login.log | cut -f 3 | sort | uniq | wc -l. Answer:1879

3. Extract the same third field (with the usernames) of the log, sort the usernames, get the unique usernames, and then get a line count of the number of unique usernames. Example: cat login.log | cut -f 3 | sort | uniq | wc -l.Answer: nonstory
4. Extract the same third field (with the usernames) of the log, sort the usernames, get the unique usernames, and then get a line count of the number of unique usernames. Example: cat login.log | cut -f 3 | sort | uniq | wc -l. Answer:
5. Extract the first field (with the date+time) of the log, extract just the date, sort the dates, get a frequency count of each unique date, and then sort the unique dates by frequency. Example: cat login.log | cut -f 1 | cut -d " " -f 1 | sort | uniq -c | sort -n. Answer:2011-03-23

6. Extract the second field (with the Ip address) and third field (with the username) of the log, sort the Ip/username pairs, get the unique Ip/username pairs, then extract just the usernames from each pair, sort the usernames, get a frequency count of how many unique pairs each username has, and then sort by frequency. Example: cat login.log | cut -f 2,3 | sort | uniq | cut -f 2 | sort | uniq -c | sort -n.Answer:nongae80



   

Nginx:
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

    Payments 

1. Used Kali to count the number of lines that start with PPAPIService: Request: using grep. Example grep -c "^PPAPIService: Request:" payments.log. Answer:192
   
2. Used Google Sheets, sorted the request by the order total column to find the largest purchase, then got the transaction ID from the corresponding response. Example: Made in the spreadsheet. Answer: 3a4da8c8-6934-4655-9ec5-335ab4540a2b
   
3. Used Google Sheets and got a count of the unique values for the state of the ship-to address. Example: on the spreadsheet. Answer: MT





