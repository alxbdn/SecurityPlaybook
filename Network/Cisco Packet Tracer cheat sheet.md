*All Essential Commands for Routers, Switches, and Network Basics*

***

### **Basic Device Navigation**

| Command              | Description                                |
| -------------------- | ------------------------------------------ |
| `enable`             | Enter privileged EXEC mode (admin access). |
| `configure terminal` | Enter global configuration mode.           |
| `exit`               | Go back one level.                         |
| `end`                | Exit configuration mode completely.        |

***

### **Device Setup**

#### **Set Hostname**

```bash
Router> enable  
Router# configure terminal  
Router(config)# hostname R1  # Rename router to "R1"  
```

#### **Set Banner Message**

```bash
R1(config)# banner motd #Unauthorized Access Prohibited#  
```

***

### **Interface Configuration**

#### **Assign IP Address to Interface**

```bash
R1(config)# interface gigabitethernet0/0  
R1(config-if)# ip address 192.168.1.1 255.255.255.0  
R1(config-if)# no shutdown  # Turn on the interface  
```

#### **Set Interface Description**

```bash
R1(config-if)# description "Connected to Office LAN"  
```

***

### **Password Security**

#### **Console Password**

```bash
R1(config)# line console 0  
R1(config-line)# password cisco  
R1(config-line)# login  
```

#### **Enable Secret Password**

```bash
R1(config)# enable secret class123  # Encrypted password  
```

#### **VTY (Remote Access) Password**

```bash
R1(config)# line vty 0 4  
R1(config-line)# password cisco  
R1(config-line)# login  
R1(config-line)# transport input ssh  # Restrict to SSH  
```

#### **Encrypt Passwords**

```bash
R1(config)# service password-encryption  
```

***

### **Routing Basics**

#### **Static Route**

```bash
R1(config)# ip route 192.168.2.0 255.255.255.0 10.0.0.2  
# Route traffic for 192.168.2.0 to next-hop 10.0.0.2  
```

#### **RIP Configuration**

```bash
R1(config)# router rip  
R1(config-router)# version 2  
R1(config-router)# network 192.168.1.0  
```

#### **OSPF Configuration**

```bash
R1(config)# router ospf 1  
R1(config-router)# network 192.168.1.0 0.0.0.255 area 0  
```

#### **EIGRP Configuration**

```bash
R1(config)# router eigrp 100  
R1(config-router)# network 192.168.1.0  
```

***

### **Switch Configuration**

#### **VLAN Setup**

```bash
Switch(config)# vlan 10  
Switch(config-vlan)# name Sales  
```

#### **Assign Port to VLAN**

```bash
Switch(config)# interface fastethernet0/1  
Switch(config-if)# switchport mode access  
Switch(config-if)# switchport access vlan 10  
```

#### **Trunk Port Configuration**

```bash
Switch(config-if)# switchport mode trunk  
```

***

### **SSH Configuration**

```bash
R1(config)# ip domain-name example.com  
R1(config)# crypto key generate rsa  # Use 1024-bit key  
R1(config)# username admin secret AdminPass  
R1(config)# line vty 0 4  
R1(config-line)# login local  # Use local username/password  
R1(config-line)# transport input ssh  
```

***

### **Troubleshooting Commands**

| Command                    | Description                     |
| -------------------------- | ------------------------------- |
| `show ip interface brief`  | Check interface status & IPs    |
| `show running-config`      | View current configuration      |
| `ping 192.168.1.1`         | Test connectivity               |
| `traceroute 8.8.8.8`       | Trace the path to a destination |
| `show cdp neighbors`       | Discover connected devices      |
| `show run \| section dhcp` | View DCHP configuration         |
| `show ip dhcp pool`        | View Pool configuration         |
| show ip route              | View routing table              |
|                            |                                 |

***

### **Save & Backup**

```bash
R1# copy running-config startup-config  # Save config  
R1# copy running-config tftp://192.168.1.5/backup.cfg  # Backup to TFTP  
```

***

### **Common Mistakes to Avoid**

❌ Forgetting `no shutdown` on interfaces.\
❌ Using weak passwords like "cisco" or "admin".\
❌ Missing subnet masks in `network` statements for routing protocols.

***

### **Step-by-Step Example: Basic Network Setup**

1. **Connect Devices**: Use copper straight-through cables for switches/hosts.
2. **Assign IPs**:

   ```bash
   PC> ipconfig 192.168.1.2 255.255.255.0 192.168.1.1  
   ```
3. **Verify Connectivity**:

   ```bash
   PC> ping 192.168.1.1  
   ```

***

### **Pro Tip**

Use **Packet Tracer’s Simulation Mode** to watch packets travel through your network!

***

### Save everything

```
copy running-config startup-config
```
or
```
do wr
```