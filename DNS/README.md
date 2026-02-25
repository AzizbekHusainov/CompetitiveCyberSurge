# What is DNS

## Domain Name System

- Hiearchal Naming system that translates a domain name into an IP address and vice verse
- Instead of enetering an entire IP address to find a webpage, you type in the domain instead, something like, 'Jey.com'

## Structure

- Browser --> Local Cache --> DNS Server --> Remote DNS Servers --> Browser 

- Root DNS servers : Direct DNS queries
- TLD(Top Level Domain) : manages domain extensions like '.com' '.net' '.gov'
- Authoritative DNS Servers : Stores DNS Rceords and their dedicated IP Address

## Types of Domains

- Generic Domains - '.com' '.edu' '.net', all of the major and easily accessible domains -
- Country Code Domains - domains that represent specific countries '.us' '.In' '.JP'
- Inverse Domains - Domains used to map IP addresses domain names

Reverse DNS - DNS maps IP to the domain name

Domain Name Server - Actively stores DNS records and answers lookup queries in the larger Domain Name System archicture Domain name servers returned to as Name servers or DNSs

##  DNS Lookup / DNS Resolution

 - process of translating a human-readable domain name into it's corresponding IP address
 
 - DNS Resolver:  DNS client, initiates Lookup process
 - Recursive query: Roslver queries multiple servers on behgalf of the client until the IP is found.
 - Iterative query: Resolver asks servers for the best answer available
 - Non-Recursive query : Resolver queries a server that already has the record in it's cache

DNS Queries:

Recursive Query : If Resolver is unable to find record stored in cache, it follows the established heierachy and queries the other servers until it finds the record and returns to browser

Iterative Query : Resolver is unable to find IP in cache and then finds the ebst possible refferal the client neeeds to click through until they can get to the correct IP address

Non-Recursive Query: Occurs when a DNS Resolver querries a DNS server for a record that is already in cache and readily accessible

## DNS Caching and TTL

DNS caching - -Mechanism that allows for a faster browser experience and reduced network traffic by storing DNS Records locally to avoid querying external DNS records repeatedly for the sma e info

TTL (Time to Live) - amount of time a DNS Record is cached on the local system before it expires
- when TTL becomes expired the cache is cleared and a fresh DNS query is made
-TTL is defined by the Authoritative DNS Server, which adjusts TTL based on the Nature of the Domain

## DNS Security and DNSSEC (DNS Securtiy Extension)
 - common risk(s) :
    DNS cache poisoning : 
        - Malicius actors inject DNS Rceords in cache, that redirect users to malicious websites

DNSSEC
 - Protocol used and designed to address these risks 
 - Adds cryptographic signatures to DNS Records, allowing resolver to verify authenticity and the integrity of DNS Response 
 - Ensures information a user recieves has not been tampered with

Reverse DNS Lookup
  - Mapping an IP address back to it's corresponding Ip address, often used for:
              - Network Diagnostics : Identify source of incoming network traffic
              - Email Security : Prevents Spam and Fraud by verifying that the incoming emails come from legitamate sources

## DNS Record Types

- A Record : maps a domain name to an IPV4 address

- CNAME Record : Canonical Name Record allows you to alias one domain name to another
e.g
   www.jeyjet.com = jeyjey.com

- MX Record : Mail Exchange record defines which mail servers are responsible for recieving emails for a domain

- TXT Record : Stores text based information, commonly used for verifying domain ownership and used to implement email security protocls
