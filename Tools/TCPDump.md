# Args
## -i
-i any : listens on all available interfaces
-i eth0 : listens on eth0
## -w
-w packets.pcap : saves the captured packets to a file
## -r
-r packets.pcap : reads captured packets from a file
## -c
-c 10 : captures up to 10 packets
## -n
-n : stops IP addresses being resolved to domain names
## -nn
-nn : does what -n does and stops resolving port numbers to their names
## -v
-v : produces a verbose output which can be expanded up to -vvv
## -q
-q : shows quick output with brief packet information
## -e
-e : prints the link-level header
## -A
-A : shows the packet data in ASCII
## -xx
-xx : shows the packet data in hexadecimal format
## -X
-X : shows the packet headers and data in hex and ASCII
# Filtering output
## Host
host IP or host HOSTNAME will only show packets exchanged with the given IP or hostname
can be prefixed with src or dst to state whether the filtered hosts should be the source or the destination
## Port
port PORT will limit the packets to those on the specified port
can be prefixed with src or dst to state whether the filtered ports should be the source or the destination
## Protocols
using protocols such as ip, ip6, udp, tcp, icmp can filter packets that use that specific protocol
## Logical operators
- and captures packets where both conditions are true
- or captures packets when either condition is true
- not captures packets when the condition is not true
## Length
greater and less both sort packets that have equal or greater/less size than a given number
## Binary 
using proto\[expr:size] where proto is the protocol, expr is the byte offset where it starts at 0 and size is the amount of bytes that are to be used
for example
ether\[0] & 1 != 0
### TCP
tcp has some basic offsets built in
tcp\[tcpflags] == tcp-syn
there are also all the other flags
