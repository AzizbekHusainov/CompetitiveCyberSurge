# Decrypt
We're using Wireshark for this one, so install it. Load the challenge's snapshot (the `.pcapng`) into the software and the `.log` into "Edit > Preferences > Protocols > TLS > (Pre)-Master-Secret Log filename"

After that, right click the sixth packet and select "Follow > TLS Stream"
1. **What Cipher Suite was chosen by the Secure Socket Server?**
   Expand the list in the bottom-left window titled "Transport Layer Security". The Cipher Suite is located in TLS 1.2 Record Layer: Handshake Protocol: Server Hello > Handshake Protocol > Cipher Suite

   Answer: `0xc02F`

2. **What is the domain covered by the SSL key?**
   Instead of expanding the "Server Hello" TLS Record Layer, expand the "Certificates" layer and navigate to The "Certificate" sublist. You'll need to comb through the HEX editor to find the domain.

   Answer: `tomsvacations.com`

3. **What is the flag transferred over HTTPS?**
   Right click on the 6th packet and select "Follow... > TLS Stream". It should be the last line.

   Answer: `SKY-LADN-1435`
