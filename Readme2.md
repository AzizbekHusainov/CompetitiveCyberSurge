1. Extract the first field (with the IP addresses), sort the IP addresses, get the unique IP addresses, and then get a line count Ex: cat access.log | cut -d " " -f 1 | sort | uniq | wc -l. Answer:47

2. Extract the third field (with the IP addresses), sort the IP addresses, get the unique values with a count of the occurrences of each IP address, and then sort in descending numeric order. Example: cat access.log | cut -d '"' -f 3 | cut -d ' ' -f 2 | sort | uniq -c | sort -rn. Answer:19

3. Extract the third field (with the IP addresses), sort the IP addresses, get the unique values with a count of the occurrences of each IP address, and then sort in descending numeric order Example: cat access.log | cut -d '"' -f 3 | cut -d ' ' -f 2 | sort | uniq -c | sort -rn. Answer: 38

4. Search the log for any lines that contain “bell” Example: cat access.log | grep "bell"
 Answer:186.64.69.141

5. Search the log for any lines that contain “Googlebot”. Example:cat access.log | grep "Googlebot" Answer: 2.1
6. Search the log for any lines that contain () { :; }; . Example: cat access.log | grep '() { :; };’.  Answer:61.160.212.172

7 Search the log for all lines that contain “Firefox” and the following characters which make up the version number, sort those values, and then get a unique count. Example: cat access.log | egrep -o "Firefox/.*" | sort | uniq -c. Answer: 3.6.28

8. Extract the 6th field (with the HTTP method), sort, get the unique values with a count of the occurrences of each value, and then sort in descending numeric order. Example: cat access.log | awk -F " " '{print $6}' | sort | uniq -c | sort -rn. Answer: GET

9. Extract the 6th field (with the HTTP method), sort, get the unique values with a count of the occurrences of each value, and then sort in descending numeric order. Example: cat access.log | awk -F " " '{print $6}' | sort | uniq -c | sort -rn. Answer: CONNECT

10. Search the log for all lines that contain that sequence of characters and then get a line count. Example: cat access.log | grep '\\x04\\x01\\x00P\\xC6\\xCE\\x0Eu0\\x00' | wc -l. Answer: 6 


