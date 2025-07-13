### 🎯 Common Options & Filters

| Command / Option                  | Purpose                                                 | Example                     |
|----------------------------------|---------------------------------------------------------|-----------------------------|
| `tcpdump -i INTERFACE`           | Capture on specific network interface                   | `tcpdump -i eth0`           |
| `tcpdump -w FILE`                | Write captured packets to file                          | `tcpdump -w capture.pcap`   |
| `tcpdump -r FILE`                | Read packets from a file                                | `tcpdump -r traffic.pcap`   |
| `tcpdump -c COUNT`               | Capture a specific number of packets                    | `tcpdump -c 100`            |
| `tcpdump -n`                     | Don’t resolve IP addresses                              | `tcpdump -n`                |
| `tcpdump -nn`                    | Don’t resolve IPs or port names                         | `tcpdump -nn`               |
| `tcpdump -v`, `-vv`, `-vvv`      | Increase verbosity level                                | `tcpdump -vv -i eth0`       |
| `tcpdump -s 0`                   | Capture full packets (no truncation)                    | `tcpdump -s 0 -w full.pcap` |
| `tcpdump port PORT_NUMBER`      | Filter by specific port                                 | `tcpdump port 80`           |
| `tcpdump src port PORT_NUMBER`  | Filter from a specific source port                      | `tcpdump src port 443`      |
| `tcpdump dst port PORT_NUMBER`  | Filter to a specific destination port                   | `tcpdump dst port 22`       |
| `tcpdump host IP_OR_HOSTNAME`   | Filter packets to/from a host                           | `tcpdump host 192.168.1.10` |
| `tcpdump src host IP`           | Filter packets from a source IP                         | `tcpdump src host 10.0.0.5` |
| `tcpdump dst host IP`           | Filter packets to a destination IP                      | `tcpdump dst host 10.0.0.10`|
| `tcpdump PROTOCOL`              | Filter by protocol (ip, ip6, icmp, etc.)                | `tcpdump icmp`              |



### 🖥️ Display Format Options

| Command / Option   | Purpose                                  |
|--------------------|------------------------------------------|
| `tcpdump -q`       | Quiet mode (brief output)                |
| `tcpdump -e`       | Show Ethernet (MAC) addresses            |
| `tcpdump -A`       | Show packets as ASCII text               |
| `tcpdump -xx`      | Show packets in hexadecimal              |
| `tcpdump -X`       | Show packets in hex + ASCII              |



### 🧠 Useful Analysis Commands

| Goal                          | Command                                                          |
|-------------------------------|------------------------------------------------------------------|
| Show only DNS queries         | `tcpdump -nn -r traffic.pcap port 53`                           |
| First DNS query hostname      | `tcpdump -nn -r traffic.pcap port 53 | grep " A? " | head -n 1` |
| Packets > 15000 bytes         | `tcpdump -nn -r traffic.pcap -s 0 -vv | awk '/length [1-9][5-9][0-9][0-9][0-9]/'` |
| Capture HTTP traffic          | `tcpdump -i eth0 port 80`                                       |
| Capture live DNS (UDP)        | `tcpdump -i eth0 udp port 53`                                   |
