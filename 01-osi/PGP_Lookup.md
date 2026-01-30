# PGP Lookup 

## Core Concepts

### What is PGP (Pretty Good Privacy)?
- **Encryption standard** for securing email communications
- Uses **public-key cryptography** (asymmetric encryption)
- Each user has a **key pair**: public key + private key

### How Public-Key Cryptography Works
1. **Public Key**: Shared openly, used by others to encrypt messages TO you
2. **Private Key**: Kept secret, used by you to decrypt messages sent to you
3. **The Process**:
   - Alice wants to send Bob a secure message
   - Alice encrypts the message using Bob's **public key**
   - Only Bob's **private key** can decrypt it
   - Even Alice cannot decrypt it after encryption!

## PGP Key Components

### Key Fingerprint
- **Unique identifier** for a PGP key (like a hash/checksum)
- Format: Long hexadecimal string (e.g., `7A39A56B73D1E097D57435CFCDE2DE1DCB2077F2`)
- Used to verify you have the correct public key
- Prevents man-in-the-middle attacks

### Key Information Fields
- **Key ID**: Shorter version of fingerprint (last 8-16 characters)
- **Algorithm/Bit Length**: e.g., `rsa4096` (RSA algorithm, 4096-bit key)
- **UID (User ID)**: Email address and/or name associated with the key
- **Creation Time**: When the key was generated
- **Expiry Date**: When the key expires (security best practice)

## Public Key Servers

### Purpose
- **Centralized databases** storing public keys
- Allow people to find and verify public keys for email encryption
- **Decentralized**: No single authoritative source

### Popular PGP Key Servers (Tools)
1. **keyserver.ubuntu.com** - Ubuntu's key server
2. **keys.openpgp.org** - Modern OpenPGP key server
3. **pgp.mit.edu** - MIT's PGP public key server

### Why Multiple Servers?
- Keys may be uploaded to different servers
- **Cross-reference** results for verification
- Redundancy in case one server is down

## Performing Lookups

### Search Methods
- **By email address**: Find keys associated with an email
- **By key fingerprint**: Verify specific key details
- **By name**: Find all keys for a person/organization

### Important Considerations
- **Verify fingerprints** through trusted channels
- Keys can be **revoked** if compromised
- Check **expiry dates** - expired keys shouldn't be used
- Be aware of **key collisions** (rare but possible)

## Security Best Practices

1. **Always verify fingerprints** through a second channel (phone, in-person, etc.)
2. **Check expiry dates** before using a key
3. **Use multiple key servers** to cross-verify
4. **Keep private keys secure** - never share them
5. **Generate strong keys** (4096-bit RSA minimum)

## Real-World Applications

- **Email encryption** (most common use)
- **Code signing** (verify software authenticity)
- **Document signing** (prove authorship)
- **SSH authentication** (secure server access)

---

## How to Answer Questions

- **Question 1** 
    - Go to keyserver.ubuntu.com and lookup the given email. In the two containers there will be fields called pub the characters after rsa4096/ are the keys (There are two)
    -Answer = DED38747CEEF C789FDC3A6154CF279C5C0424907 and B6709B4CC6F42077F69841919521BEDCABD94DDF

- **Question 2** 
    - On the same website enter the given key into the search area and look for uid. The uid contains the name and email of the keys owner
    - Answer = hx@liber8tion.cityinthe.cloud

- **Question 3**
    - Use the same key given for question two, under uid it will say sig cert and there will be two time stamps the one on the right hand side is the expiration one. 
    -Answer = 2050-12-26T20:36:17Z (T through Z is the TIME)
---
