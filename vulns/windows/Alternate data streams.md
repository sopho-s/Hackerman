Alternate data streams is a NTFS file attribute and was designed to provide compatibility with MacOS HFS
any file created on a NTFS formatted drive will have two different forks/streams
- Data stream- default stream that contains the data of the file
- Resource stream typically contains the metadata of the file
attackers can use ADS resource streams to hide malicious code or executable in the file attribute resource stream of a legitimate file

```shell
notepad test.txt:secret.txt
```
now this cannot be directly executed so you gotta make a sym link
```shell
mklink newlink test.txt:secret.txt 
```
then you can run newlink with `start`