# Cryptographic scheme
when representing encryption on uses the following letters to represent parts
- E: Encryption method
- D: Decryption method
- P: Plaintext
- K_n: key
- C: ciphertext
# Kerckhoffs's principle
A cryptosystem should be secure, even if everything about the system, except the key, is public knowledge
# Symmetric encryption
## Cesear cipher
$E_n(x)=(x+n)\ mod\ 26$
$D_n(x)=(x-n)\ mod\ 26$
## Polyalphabetic cipher
Uses multiple substitution alphabets, each letter could be encrypted differently by position
## One-Time Pad
theoretically 100% secure stream cipher
OPT is a stream cipher where a message over an alphabet size l is encrypted with a  random key string 
essentially the key will be as large or larger than the size of the message and then each bit of the character is encrypted by combining it with a corresponding bit or character from the pad using modular addition (so essentially xor)
### Only perfect if
The key is perfectly random
at least as long as the message
never reused
## Transposition
Keeps the letters but reorders their positions
## Substitution
replaces characters with other characters
## Composite cipher
composite ciphers are combinations of both transposition and substitution ciphers
### Feistel Cipher
for this function you split the plaintext up into two blocks that alternate what is done do them
this is described as such
$L_{i+1}=R_i$
$R_{i+1}=L_i\oplus\ F(R_i,K_i)$
where F scrambles the value using a key
## Block cipher
ciphers that encrypt data in blocks of set size
## Issues with symmetric
- Key distribution
- every pair of users need their own secret
- evidence that a specific person created or approved a specific message so they cannot later deny doing so
# DES
Data encryption standard was the first cryptographic standard and was a block, 16 round feistel cipher
the security of DES has long been questioned as people fear the NSA has a secret backdoor in the cipher
## Why is DES insecure
a exhaustive key search can crack code in a reasonable time
# Cipher modes
## Electronic codebook (ECB)
encrypts each block with the same key which means identical plaintext blocks results in identical cipher text blocks
## Cipher Block chaining (CBC)
each plaintext block is XORed with the previous cipher text block
# Public key encryption (asymmetric)
## RSA
rsa relies on the presumed hardness of factoring large n=pq where p and q are both primes
it was inspired by the diffie-hellman's key exchange concept, rsa expanded the concept into an encryption system
### steps
1. choose two large primes p, q
2. compute n = p.q
3. compute phi(n) = (p-1)(q-1)
4. pick e; 1<e<phi(n), and gcd(e,phi(n)) = 1
5. compute d, e.d mod phi(n) = 1
the public key is n,e
the private key is d
### encryption and decryption
encrypting is `c = m^e mod n`
decrypting is `m = c^d mod n`