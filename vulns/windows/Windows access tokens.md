Access tokens are responsible for identifying and describing the security context of a process or thread running on a system. Windows access tokens are categorised based on the varying security levels assigned to them
typically it will be one of the following two:
- Impersonate-level tokens are created as a direct result of a non-interactive login on windows, typically through specific system services or domain logons
- Delegate-level tokens are typically created through an interactive login on windows primarily through a traditional login or through remote access protocols such as RDP
Impersonate-level tokens can be utilised to impersonate a token on the local system and not on any external system that ustilise the token
Delegate-level tokens can tho 

you can use incognito to steal le privilege if you have the correct privileges on meterpreter

```shell
list_tokens -u
```

```shell
impersonate_token "token name"
```