# Network & DNS Guide for NCL (National Cyber League)

## 1. DNS Fundamentals
DNS (Domain Name System) translates human-readable domain names into IP addresses.
It operates in a hierarchical, distributed manner.

### DNS Hierarchy
- Root Servers
- TLD Servers (.com, .org, .edu, etc.)
- Authoritative Name Servers
- Recursive Resolvers

---

## 2. DNS Lookup
DNS lookups resolve domain names to records.

### Common Tools
- dig
- nslookup
- host
- whois

### Example
dig example.com A

Form: dig <domain> <record_type>

---

## 3. DNS Record Types

| Record | Purpose |
|------|--------|
| A | Maps hostname → IPv4 address |
| AAAA | Maps hostname → IPv6 address |
| CNAME | Alias to another hostname |
| MX | Mail server routing |
| NS | Authoritative name servers (zone delegation) |
| SOA | Zone authority & metadata |
| TXT | Arbitrary text (SPF, DKIM, verification) |
| DNSKEY | DNSSEC public keys |
| DS | Delegation Signer (DNSSEC trust chain) |
| RRSIG | DNSSEC signatures |

---

## 4. DNSSEC & Authorship
DNSSEC ensures authenticity and integrity of DNS data.

### Key Records
- DNSKEY → Stores public signing keys
- RRSIG → Cryptographic signature
- DS → Links child zone to parent zone

---

## 5. WHOIS
WHOIS provides domain registration metadata.

### Information Found
- Registrar
- Registrant
- Creation & expiration dates
- Name servers

### Command
whois example.com

---

## 6. Zone Delegation
Delegating a DNS zone means assigning authority to name servers.

### Key Concept
- Delegation occurs via NS records
- Parent zone lists child zone’s authoritative servers

Defined in RFC 1035

---

## 7. ICANN
ICANN oversees:
- Domain name allocation
- IP address space
- Root DNS operations

Does NOT resolve DNS queries directly.

ICANN is another web browser based tool. You can utilize it to obtain public registration data regarding domains.

Link: https://lookup.icann.org/en

---

## 8. NCL Exam Tips
- RFCs are authoritative
- If DNSSEC is mentioned → think DNSKEY, RRSIG, DS
- Zone delegation → NS record

---

## 9. DNS Cheat Sheet
IPv6 → AAAA  
DNSSEC key → DNSKEY  
Zone delegation → NS  
Email routing → MX  
Trust chain → DS  

