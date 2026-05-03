# Snort Cheat Sheet
Based on the TryHackMe Snort Room.

## Command Line Modes

### Global Commands
| Description | Command |
| :--- | :--- |
| Display version | `snort -V` or `snort --version` |
| Do not display the version banner | `snort -q` |
| Use specific interface | `snort -i eth0` |
| Verbose mode | `snort -v` |

### Sniffer Mode
| Description | Command |
| :--- | :--- |
| Display link-layer headers | `snort -e` |
| Display data payload | `snort -d` |
| Display full packet details in HEX | `snort -X` |
| Multiple flag usage (all packet details) | `snort -eX` |
| Sniff "N" number of packets | `snort -v -n 10` |

### Logger Mode
| Description | Command |
| :--- | :--- |
| Default log path | `/var/log/snort` |
| Use alternative log path | `snort -l /home/username/Desktop` |
| Log in ASCII Format | `snort -v -K ASCII` |
| Read snort files | `snort -v -r snort.log` |
| Read "N" number of packets | `snort -v -r snort.log -n 10` |
| Filter packets with BPF (TCP) | `snort -v -r snort.log tcp` |
| Filter packets with BPF (UDP & Port) | `snort -v -r snort.log 'udp and port 53'` |

### PCAP Processing
| Description | Command |
| :--- | :--- |
| Process single pcap file | `snort -c /etc/snort/snort.conf -q -r file.pcap -A console` |
| Process multiple pcap files | `snort -c /etc/snort/snort.conf -q --pcap-list="file1.pcap file2.pcap" -A console` |
| Process pcaps from folder | `snort -c /etc/snort/snort.conf -q --pcap-dir=/home/pcap-folder -A console` |
| Show processed pcap name | `snort -c /etc/snort/snort.conf -q --pcap-list="file1.pcap file2.pcap" -A console --pcap-show` |

### IDS/IPS Mode
| Description | Command |
| :--- | :--- |
| Use configuration file | `snort -c /etc/snort/snort.conf` |
| Test instance and configuration file | `snort -c /etc/snort/snort.conf -T` |
| Disable logging | `snort -c /etc/snort/snort.conf -N` |
| Run Snort in background | `snort -c /etc/snort/snort.conf -D` |
| Alert mode 1 (No output) | `snort -c /etc/snort/snort.conf -v -A none` |
| Alert mode 2 (Console output 1) | `snort -c /etc/snort/snort.conf -v -A console` |
| Alert mode 2 (Console output 2) | `snort -c /etc/snort/snort.conf -v -A cmg` |
| Alert mode 3 (File output 1) | `snort -c /etc/snort/snort.conf -v -A fast` |
| Alert mode 3 (File output 2) | `snort -c /etc/snort/snort.conf -v -A full` |
| Use rules without configuration file | `snort -c /etc/snort/rules/local.rules -v -A console` |

### Example Rule
```
alert tcp $EXTERNAL_NET any -> $HOME_NET $HTTP_PORTS ( msg:"Directory Traversal Attempt!"; flow:established; nocase; content:"HTTP"; fast_pattern; content:"| 2E 2E 2F|"; content:"/.."; session:all; reference:CVE,XXX; sid:100001; rev:1;)
```

## Snort Rule Breakdown

| Logical Part | Category | Component | Example | Description |
| :--- | :--- | :--- | :--- | :--- |
| **RULE HEADER** | | Action | `alert` | Action, this option tells Snort what to do in a rule match |
| | | Protocol | `tcp` | Protocol to be analysed. Supported protocols: TCP, UDP, ICMP, IP. |
| | | Source IP | `$EXTERNAL_NET` | Source IP addresses. |
| | | Source Port | `any` | Source ports. |
| | | Direction | `->` | Direction operator. Identify the orientation of traffic. |
| | | Destination IP | `$HOME_NET` | Destination IP addresses. |
| | | Destination Port | `$HTTP_PORTS` | Destination ports. |
| **RULE OPTIONS** | **GENERAL RULE OPTIONS** | Message | `msg` | Display message for rule match. |
| | | Reference | `reference` | Provide additional information or reference for the rule. |
| | | Rule id | `sid` | Unique rule number. |
| | | Revision info | `rev` | Revision information for the rule. |
| | **NON-PAYLOAD RULE OPTIONS** | Flow | `flow` | TCP stream direction. |
| | **PAYLOAD DETECTION RULE OPTIONS** | Nocase | `nocase` | Disable case sensitivity to enhance the content match. |
| | | Content | `content` | Filter the payload data and look for an exact match. |
| | | Fast-pattern | `fast-pattern` | Prioritise the content search to speed up the payload search. This option is required when using multiple "content" options. |
| | **POST-DETECTION RULE OPTIONS** | Session | `session` | Extract user data from TCP sessions. |