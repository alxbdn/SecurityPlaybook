* **IPv4**: `192.168.1.1` (32-bit, decimal)
  * Private Ranges:
    * `10.0.0.0/8`
    * `172.16.0.0/12`
    * `192.168.0.0/16`
* **IPv6**: `2001:0db8:85a3::8a2e:0370:7334` (128-bit, hex)
  * Shorthand: Replace consecutive zeros with `::` once.

***

### **Subnetting Essentials**

#### **IPv4 Subnet Mask Shortcuts**

| CIDR | Subnet Mask       | Hosts per Subnet |
| ---- | ----------------- | ---------------- |
| /24  | `255.255.255.0`   | 254              |
| /30  | `255.255.255.252` | 2                |

**Formula**:

* Hosts = 2(32−CIDR)−22(32−CIDR)−2
* Example: `/26 = 64 - 2 = 62 hosts`.

***

### **Common Protocols & Ports**

| Protocol | Port  | Use Case                |
| -------- | ----- | ----------------------- |
| HTTP     | 80    | Unencrypted web traffic |
| HTTPS    | 443   | Encrypted web traffic   |
| SSH      | 22    | Secure remote access    |
| DNS      | 53    | Domain name resolution  |
| DHCP     | 67/68 | Dynamic IP assignment   |

***

### **Network Troubleshooting Commands**

* **`ping <IP>`**: Test connectivity.
* **`tracert <IP>` (Windows) / `traceroute <IP>` (Linux)**: Map path to destination.
* **`ipconfig` (Windows) / `ifconfig` (Linux)**: View interface details.
* **`netstat -ano`**: List active connections and ports.
* **`nslookup <domain>`**: Query DNS records.

***

### **Security Best Practices**

1. **Firewall Rules**:
   * Block all inbound traffic by default.
   * Allow only necessary ports (e.g., 443 for HTTPS).
2. **Use VLANs** to segment traffic (e.g., separate guest and internal networks).
3. **Disable unused ports** on switches/routers.
4. **Always use SSH** instead of Telnet.

***

### **Quick Reference Tables**

#### **OSI Model Layers**

| Layer | Name        | Example         |
| ----- | ----------- | --------------- |
| 7     | Application | HTTP, FTP       |
| 4     | Transport   | TCP, UDP        |
| 3     | Network     | IP, ICMP        |
| 2     | Data Link   | MAC addresses   |
| 1     | Physical    | Cables, signals |

***

### **Pro Tips**

🔹 Use **Wireshark** to analyze traffic patterns.\
🔹 Memorize private IP ranges to avoid conflicts.\
🔹 For labs: `/30` subnets = perfect for point-to-point links.

***

### **Where to Learn More**

* **Cisco NetAcad**: Free networking labs.
* **TryHackMe**: Hands-on network security rooms.
* **RFC 1918**: Private IP address standards.
* **Cisco Packet Tracer**

***

**Fun Fact**: The first RFC (Request for Comments) was written in 1969 to define ARPANET protocols—the precursor to the modern internet!

***


---

# Agent Instructions: Querying This Documentation

If you need additional information that is not directly available in this page, you can query the documentation dynamically by asking a question.

Perform an HTTP GET request on the current page URL with the `ask` query parameter:

```
GET https://recondock.gitbook.io/recondock/cybersecurity-playbook/connection-security/ip-addressing-basics.md?ask=<question>
```

The question should be specific, self-contained, and written in natural language.
The response will contain a direct answer to the question and relevant excerpts and sources from the documentation.

Use this mechanism when the answer is not explicitly present in the current page, you need clarification or additional context, or you want to retrieve related documentation sections.