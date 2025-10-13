# Syntax
`john [options] [file-path]`
try using alongside hash-id.py
to get to ppzips use `zip2john zip > out`
to get to pprars use `rar2john rar > out`
to get a password from a ssh private key use `ssh2john id_rsa > out`
# Args
## --wordlist

--wordlist=\[path-to-wordlist\]: specifies the wordlist for John to use
## --format
--format=\[format]: specifies the hash format
## --single
--single: uses single crack mode which uses word mangling on the same password to attempt to crack variations of a possible word
## --rule
--rule=\[rule]: used to call custom rules 
# Caveats
Sometimes, when dealing with standard hash types, you need to prefix it with raw-, to check use --list=formats
# Modifying rules
https://www.openwall.com/john/doc/RULES.shtml
rules can be located at /etc/john/john.conf
- `Az`: Takes the word and appends it with the characters you define
- `A0`: Takes the word and prepends it with the characters you define
- `c`: Capitalises the character positionally
- - `[0-9]`: Will include numbers 0-9  
- `[0]`: Will include only the number 0
- `[A-z]`: Will include both upper and lowercase  
- `[A-Z]`: Will include only uppercase letters
- `[a-z]`: Will include only lowercase letters