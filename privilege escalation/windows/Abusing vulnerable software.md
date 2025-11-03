# Unpatched software
Software installed on the target system can present various privilege escalation opportunities. As with drivers, organisations and users may not update as often as they update the operating system. You can use `wmic` tool to list software installed on the target system and its versions. The command below will will dump information it can gather on installed software
```shell-session
wmic product get name,version,vendor
```
this may not return all installed program. depending on how they were installed they might not get listed