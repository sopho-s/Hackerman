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