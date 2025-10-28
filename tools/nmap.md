# Args
## -sn
sends a ping scan
## -sT
tries to complete a TCP three way handshake with every target TCP port
## -sS
a SYN scan also known as a stealth scan completes only the first step of the three way handshake, it does such on every target TCP port
## -sN -sF -sX
NULL, FIN and Xmas scan are all supposed to be more sneaky port scanning methods
## -sU
scans every target UDP port
## -F
fast mode, only scans 100 most common ports instead of 1000
## -p\[range]
allows you to specify the range of ports to scan where -p10-1024 will do ports 10 to 1024 and -p-25 will do ports 1 to 25 and -p- will do all ports
## -O
attempts to detect the OS version of the system
## -sV
version detection of each service
## -T
0-4 range of how fast one wishes the scan to go
## -Pn
removes the initial ping to the device

| Timing          | Total Duration |
| --------------- | -------------- |
| T0 (paranoid)   | 9.8 hours      |
| T1 (sneaky)     | 27.53 minutes  |
| T2 (polite)     | 40.56 seconds  |
| T3 (normal)     | 0.15 seconds   |
| T4 (aggressive) | 0.13 seconds   |
## --min-parallelism and --max-parallelism
specifies the minimum and maximum amount of probes that can be sent at once
## --min-rate and --max-rate
specifies the minimum and maximum rate of packets nmap sends in packets per second
## --host-timeout
specifies the amount of time to wait for a host to respond
## -v
specifies the verbosity level nmap uses
## -d
sets the debugging level nmap uses
## -oN -oX -oG -oA
saves output into a file in a normal output, XML output, grep-able output, all major formats respectively

# Supplying ranges
when supplying nmap with an IP range, one can do a range like 192.168.128.0-255 or 192.168.128.0/24