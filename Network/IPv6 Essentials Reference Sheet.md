## IPv6 Addressing

| Address Type | IPv6 Notation | Binary Prefix |
| :--- | :--- | :--- |
| Unspecified | `::/128` | `0000...0 (128 bits)` |
| Loopback | `::1/128` | `0000...1 (128 bits)` |
| Multicast | `ff00::/8` | `1111 1111 XXXX XXXX` |
| Link-Local | `fe80::/10` | `1111 1110 1000 0000` |
| Global Unicast (GUA) | `2000::/3` | `001x xxxx XXXX XXXX` |
| Unique Local (ULA) | `fc00::/7` | `1111 110x XXXX XXXX` |
| 6to4 (tunnel) | `2002::/16` | |
| Teredo (tunnel) | `2001:0000::/32` | |
| IPv4-Mapped IPv6 | `0:0:0:0:0:ffff:a.b.c.d` | |
| NAT64 | `64:ff9b::/96` | |
| Documentation | `2001:0db8::/32` | |

## IPv6 Address Shorthand Notation

1. **Original:** `2001:0db8:0006:1ab5:0000:0000:0000:ba11`
2. **Remove leading zeros to achieve:** `2001:db8:6:1ab5:0:0:0:ba11`
3. **Additional reduction:** Replace consecutive fields of zeros with double-colon `::` option (can only be done once) to achieve: `2001:db8:6:1ab5::ba11`

## IPv6 Header

### Header Fields
* **Version (4):** IP version number, 6 for IPv6
* **Traffic Class (8):** Similar to IPv4 ToS field. Used by nodes to identify and distinguish between different classes or priorities of IPv6 packets
* **Flow Label (20):** Used by a source to label sequences of packets for which it requests special handling by the IPv6 routers
* **Payload Length (16):** Length of the IPv6 payload (may also include extension headers)
* **Next Header (8):** Identifies the type of header following the IPv6 header
* **Hop Limit (8):** Decremented by 1 by every router that forwards the packet
* **Source Address (128):** IPv6 address of the originator of the packet, will be a unicast address
* **Destination Address (128):** IPv6 address of the intended recipient or final destination of the packet, can be unicast or multicast address

## Well Known Multicast Addresses

| Address | Description | Scope |
| :--- | :--- | :--- |
| `ff01::1` | All Nodes Address | Interface-local |
| `ff02::1` | All Nodes Address | Link-local |
| `ff01::2` | All Routers Address | Interface-local |
| `ff02::2` | All Routers Address | Link-local |
| `ff05::2` | All Routers Address | Site-local |
| `ff02::4` | DVMRP Routers | Link-local |
| `ff02::5` | OSPF IGP Drothers | Link-local |
| `ff02::6` | OSPF IGP DRS | Link-local |
| `ff02::9` | RIPng Routers | Link-local |
| `ff02::a` | EIGRPv6 Routers | Link-local |
| `ff02::c` | Microsoft SSDP | Link-local |
| `ff02::d` | All PIM Routers | Link-local |
| `ff02::12` | VRRPv3 | Link-local |
| `ff02::16` | All MLDv2 Routers | Link-local |
| `ff02::1:2` | DHCPv6 Servers/Agents | Link-local |
| `ff05::1:3` | DHCPv6 Servers/Agents | Site-local |
| `ff0x::101` | Network Time Protocol | Variable |
| `ff02::1:ffxx:XXXX` | Solicited-Node Address | Link-local |

## Interface ID from MAC Address (Expanded to EUI-64)

1. **IEEE 48-bit MAC Address:** `00 18 41 23 6a 32`
2. **Insert `ff fe` in the middle:** `00 18 41 ff fe 23 6a 32`
3. **Invert 7th bit of 1st Byte (universal/local bit):** `00` (binary `00000000`) becomes `02` (binary `00000010`)
4. **Result:** `02 18 41 ff fe 23 6a 32`
5. **Modified EUI-64 Interface ID:** `0218:41ff:fe23:6a32`

## ICMPv6 Message Types

| Type | Description |
| :--- | :--- |
| 128 | Echo Request |
| 129 | Echo Reply |
| 130 | Multicast Listener Query |
| 131 | Multicast Listener Report |
| 132 | Multicast Listener Done |
| 133 | Router Solicitation |
| 134 | Router Advertisement |
| 135 | Neighbor Solicitation |
| 136 | Neighbor Advertisement |
| 137 | Redirect Message |
| 138 | Router Renumbering |
| 139 | ICMP Node Information Query |
| 140 | ICMP Node Information Response |
| 143 | Multicast Listener Report (MLDv2) |
| 144 | Home Agent Discovery Request |
| 145 | Home Agent Discovery Reply |
| 146 | Mobile Prefix Solicitation |
| 147 | Mobile Prefix Advertisement |

## IPv6 Next Header Fields (Extension Headers)

| Header Value | Description |
| :--- | :--- |
| 0 | IPv6 Hop-by-Hop Option |
| 41 | IPv6 encapsulation |
| 43 | Routing Header for IPv6 |
| 44 | Fragment Header for IPv6 |
| 50 | Encap Security Payload (ESP) |
| 51 | Authentication Header (AH) |
| 59 | No Next Header for IPv6 |
| 60 | Destination Options for IPv6 |

## IPv6 Address Types

### Scopes and Routing
* **Link-Local:** Automatically assigned per interface, not routable
* **Global Unicast Address (GUA):** Assigned by SLAAC, Stateful (DHCPv6), or manual, routable to Internet
* **Unique Local Address (ULA):** Assigned by SLAAC, Stateful (DHCPv6), or manual, not routable to Internet, is routable within enterprise (like private address)

### Transmission Types
* **Unicast:** one-to-one (link-local, unique local, global)
* **Anycast:** one-to-nearest (allocated from Unicast)
* **Multicast:** one-to-many (also replaces broadcast)

## IPv6 Neighbor Discovery Protocol

* **Neighbor Solicitation (NS):** Neighbor address resolution (similar to IPv4 ARP)
* **Neighbor Advertisement (NA):** Response to Neighbor Solicitation requests
* **Router Solicitation (RS):** Sent by nodes "looking" for IPv6 routers on-link
* **Router Advertisements (RA):** Sent periodically by routers and in response to RS
* **Duplicate Address Detection (DAD):** Sent to own Solicited-Node Multicast Address

## Wireshark Display Filters for IPv6

* `ipv6`: all IPv6 traffic
* `icmpv6`: all IPv6 ICMPv6 traffic
* `dhcpv6`: all DHCPv6 traffic
* `icmpv6.type == 133`: all router solicitations
* `icmpv6.type == 134`: all router advertisements
* `icmpv6.type == 135`: all neighbor solicitations
* `icmpv6.type == 136`: all neighbor advertisements
* `icmpv6.type == 137`: all redirect messages

## IPv6 HexSpeak

`BABE` : User's VLANs
`CAFE` : Transit Links
`BEEF` : Servers
`DEAD` : Deprecated interfaces
