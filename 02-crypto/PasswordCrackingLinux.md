# Password Cracking Using John Linux

## Obtain Top 500 Passwords 
### Commands Used
```bash
git clone https://github.com/danielmiessler/SecLists.git
cp SecLists/Passwords/Common-Credentials/500-worst-passwords.txt wordlists/
```

## RockYou Password List

### Commands Used

```bash
cd /mnt/c/Users/ahusa/repos
wget https://gitlab.com/kalilinux/packages/wordlists/-/raw/kali/master/rockyou.txt.gz
gunzip rockyou.txt.gz
```

* Obtained from official Kali Linux repository. This is by default present on Kali Linux systems but will be required for other systems such as Ubuntu.

* Default Kali Location With Example Usage of John: john --wordlist=/usr/share/wordlists/ hash.txt

## Running John the Ripper

### Commands Used

```bash
# Top 500 passwords
john --wordlist=wordlists/500-worst-passwords.txt hashes.txt

# RockYou list
john --wordlist=wordlists/rockyou.txt hashes.txt

# RockYou with rules (Recommended)
john --wordlist=wordlists/rockyou.txt --rules hashes.txt

# Custom Pokémon list with rules
john --wordlist=wordlists/pokemon_custom.txt --rules hashes.txt

# Show cracked results
john --show hashes.txt

# Crack an encrypted pdf
pdf2john encrypted.pdf > hash.txt

john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt

john --show hash.txt
```

## WHAT
* John is an automated password cracker that uses words from lists

## WHO
* This is mostly used by bad guys to perpetrate accounts. Can be used by the good guys by preventing users from inputting bad passwords on online lists.

## WHY
* This can be used to crack passwords

## WHEN MAKING PERSONAL LISTS
* Try shorter and simpler passwords first
* Try different variations of uppercase lowercase and numbers. Using dates is also great. EX: john1999, John 1999, john1990.