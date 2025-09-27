# Terms
## Plaintext
Plaintext is the original, readable message or data before it’s encrypted. It can be a document, an image, a multimedia file, or any other binary data
## Ciphertext
Ciphertext is the scrambled, unreadable version of the message after encryption. Ideally, we cannot get any information about the original plaintext except its approximate size
## Cipher
Cipher is an algorithm or method to convert plaintext into ciphertext and back again. A cipher is usually developed by a mathematician
## Key
Key is a string of bits the cipher uses to encrypt or decrypt data. In general, the used cipher is public knowledge; however, the key must remain secret unless it is the public key in asymmetric encryption. We will visit asymmetric encryption in a later task
## Encryption
Encryption is the process of converting plaintext into ciphertext using a cipher and a key. Unlike the key, the choice of the cipher is disclosed
## Decryption
Decryption is the reverse process of encryption, converting ciphertext back into plaintext using a cipher and a key. Although the cipher would be public knowledge, recovering the plaintext without knowledge of the key should be impossible (infeasible)
## Symmetric encryption
Encryption that uses the same key to encrypt and decrypt
## Asymmetric encryption
Uses a private key for decryption and a public key for encryption
# Encryption algorithms
# PGP
PGP stands for pretty good privacy. It’s software that implements encryption for encrypting files, performing digital signing, and more. GnuPG or GPG is an open-source implementation of the OpenPGP standard.
# SSH
on first connect ssh confirms whether you recognise the server's public key fingerprint using ED25519, this warning is because a man in the middle attack is possible. after confirming ssh will add the fingerprint for the future
ssh supports username and password login, but also key login as well. It by default uses RSA keys for the login if a key is used
one can use ssh-keygen to generate the key pairs, of which it supports various algorithms
# Diffie-Hellman Key Exchange
Diffie-Hellman key exchange allows for two parties to establish a shared secret over an insecure connection without using asymmetric encryption
## Example
1. Alice and Bob agree on the **public variables**: a large prime number _p_ and a generator _g_, where 0 < _g_ < _p_. These values will be disclosed publicly over the communication channel. Although insecurely small, we will choose _p_ = 29 and _g_ = 3 to simplify our calculations.
2. Each party chooses a private integer. As a numerical example, Alice chooses _a_ = 13, and Bob chooses _b_ = 15. Each of these values represents a **private key** and must not be disclosed.
3. It is time for each party to calculate their **public key** using their private key from step 2 and the agreed-upon public variables from step 1. Alice calculates _A_ = _g^a_ mod _p_ = 313 mod 29 = 19 and Bob calculates _B_ = _g^b_ mod _p_ = 315 mod 29 = 26. These are the public keys.
4. Alice and Bob send the keys to each other. Bob receives _A_ = _g^a_ mod _p_ = 19, i.e., Alice’s public key. And Alice receives _B_ = _g^b_ mod _p_ = 26, i.e., Bob’s public key. This step is called the **key exchange**.
5. Alice and Bob can finally calculate the **shared secret** using the received public key and their own private key. Alice calculates _B^a_ mod _p_ = 2613 mod 29 = 10 and Bob calculates _A^b_ mod _p_ = 1915 mod 29 = 10. Both calculations yield the same result, _g^a^b_ mod _p_ = 10, the shared secret key.
## Symmetric
### RSA
RSA is based on the mathematically difficult problem of factoring a large number. Multiplying two large prime numbers is a straight forward operation, however finding the factors of a huge number takes much more computing power
#### Example
1. Bob chooses two prime numbers: _p_ = 157 and _q_ = 199. He calculates _n_ = _p_ × _q_ = 31243.
2. With _ϕ_(_n_) = _n_ − _p_ − _q_ + 1 = 31243 − 157 − 199 + 1 = 30888, Bob selects _e_ = 163 such that _e_ is relatively prime to _ϕ_(_n_); moreover, he selects _d_ = 379, where _e_ × _d_ = 1 mod _ϕ_(_n_), i.e., _e_ × _d_ = 163 × 379 = 61777 and 61777 mod 30888 = 1. The public key is (_n_,_e_), i.e., (31243,163) and the private key is $(n,d), i.e., (31243,379).
3. Let’s say that the value they want to encrypt is _x_ = 13, then Alice would calculate and send _y_ = _x__e_ mod _n_ = 13163 mod 31243 = 16341.
4. Bob will decrypt the received value by calculating _x_ = _y__d_ mod _n_ = 16341379 mod 31243 = 13. This way, Bob recovers the value that Alice sent.
# Rainbow tables
A rainbow table is just a lockup table of hashes to plaintexts, so you can quickly find what password a user had just from the hash
## How to prevent this
To protect against rainbow tables you can add salts to password
# Salts
Salts is essentially adding random characters to the end/start of a password to make it so that pre-calculated hashes don't work
# Hash recognition
Automated hash recognition tools such as hashID exist but are unreliable for many formats. For hashes that have a prefix, the tools are reliable. Most likely if you find the hash in a web application data base its more likely to be using MD5 than NTLM
## Context recognition
Sometimes (without context) it is impossible to tell two hashes apart, but using the origin context one can determine the hash function
- webapp: MD5
- MS Windows: NTLM
# HMAC
HMAC (Keyed-Hash Message Authentication Code) is a type of message authentication code that uses a cryptographic hash function in combination with a secret key to verify the authenticity and integrity of the data
## Steps
1. The secret key is padded to the block size of the hash function.
2. The padded key is XORed with a constant (usually a block of zeros or ones).
3. The message is hashed using the hash function with the XORed key.
4. The result from Step 3 is then hashed again with the same hash function but using the padded key XORed with another constant.
5. The final output is the HMAC value, typically a fixed-size string.
![[HMAC.svg|100%]]
