# **Networking Fundamentals**

---

## **What is a Network?**

A computer network connects devices (phones, laptops, TVs) to share data and resources via a common connection (e.g., Wi-Fi).

### **Types of Networks**
- **LAN (Local Area Network):** Small area (home/office).
- **WAN (Wide Area Network):** Connects multiple LANs over large distances (e.g., the Internet).

---

## **Why Networks Matter**
- **Communication:** Emails, chats, calls.
- **Resource Sharing:** Files, printers, servers.
- **Internet Access:** Browsing, streaming, apps.
- **App Functionality:** Data exchange between devices and servers.

### **Role in DevOps**
- Server communication, deployment, monitoring, optimization.

**Key Idea:** Networks are the backbone of digital communication.

---

## **Core Components**

### **Devices**
- **Switches:** Connect devices in a LAN; direct internal traffic.
- **Routers:** Connect networks; route data to correct destinations.
- **Firewalls:** Protect network by filtering unauthorized traffic.

### **Addresses**
- **IP Address:** Device identifier on a network (IPv4/IPv6).
- **MAC Address:** Hardware identifier for network interfaces.

**IP vs MAC Analogy:** IP = postal address (can change), MAC = fingerprint (permanent).

### **Ports & Protocols**
- **Ports:** Logical endpoints for services (HTTP=80, HTTPS=443).
- **Protocols:** Rules for communication (TCP, UDP, HTTP, FTP).

| Feature | TCP | UDP |
|--|--|--|
| Connection | Oriented | Connectionless |
| Reliability | High | Low |
| Speed | Slower | Faster |
| Use Cases | Web, email, file transfer | Streaming, gaming, DNS |

---

## **OSI & TCP/IP Models**

### **OSI 7 Layers**
- **1. Physical:** Responsible for wires + signals. Sends raw bits over cable, fiber, or WiFi.
- **2. Data Link:** Handles MAC address. Organizes bits info frames, ensure devices in same network communicate.
- **3. Network:** Responsible for routing packets using IP addresses and routers.
- **4. Transport:** TCP/UDP 
- **5. Session:** Manages communication sessions.
- **6. Presentation:** Handles encryption and data format translation.
- **7. Application:** Closest to user and apps. 

### **TCP/IP 4 Layers**
- **1. Application:** Handles netowork apps & protocols (HTTP, DNS).
- **2. Transport:** Manages end to end communication with TCP/UDP.
- **3. Internet:** Responsible for logical addressing and routing. Same as `OSI Network` layer.
- **4. Network Access:** Handles LAN, ethernet, WiFi. Combines OSI `Physical + Data Link` layer.

**Key Idea:** OSI = conceptual; TCP/IP = practical.

---

## **DNS**
- Translates domain names → IP addresses.
- Without it, we will have to remember IP addresses for every website.

### **DNS Hierarchy:**
- **Root** -> Top level. Does not hold domain details, only points to **TLD Servers**
- **TLD Server** -> Handles domains under extension like .com, .org etc
- **Authorative Name Server** -> Hold actual DNS records for a domain
- **Domain & Zones** -> Contains zone files with records

### **DNS Query Process:**
1. User types a domain (eg: google.com) into browser
2. Browser asks local *DNS Resolver*
3. Resolver checks cache; If not found:
- Queries *Root Server* -> gets *TLD Server* info
- Queries *TLD Server* -> gets *Authorative Server* info
- Queries *Authorative Server* -> Gets the final IP
4. Resolver returns IP to browser -> browser connects to website

### **DNS Resource Records:**
- They are individual entries in a zone file containing specific info about a domain, host or service.

**Components:**
- Record name -> Domain being queried
- TTL -> Time to live. How long a record is cached
- Class -> Namespace of the record
- Type -> Kind of record (A, AAAA, CNAME)
- Data -> Actual info corresponding to the record type (IP, mail server)

**Common Record Types:**
- A Record -> Maps domain to IPv4 address. Most common.
- AAAA Record -> Maps domain to IPv6 address.
- CNAME -> Canomincal Name Record. Creates an alias for a domain. Points multiple names to the same IP.
- MX -> Mail Exchange Record. Stores email server info.
- TXT -> Used for domain verification or policies.

### **DNS Debugging Tools:**
- **`nslookup <domain.com>`** Basic DNS query tool. Returns DNS info such as server, address, and whether answer is authorative.
- **`dig <domain.com>`** Domain Information Grouper. More detailed output.
- **`dig +short <domain.com>`** Brief IP result.
- **`dig +short Ns <domain.com>`** Shows name servers.
- **`/etc/hosts/`** Local file on your computer that maps domain names to IP address. Your computer checks this file when you type a domain in your browser. Can manually override.

---

## **Routing**
- **Definition:** Determines best path for data.
- **Types:** Static vs Dynamic.
- **Protocols:** OSPF (internal), BGP (between networks).

---

## **Subnetting & CIDR**
- Splits networks into smaller segments.
- CIDR: /n = network bits.
 
*Example: `192.168.1.0/26`*
- `/26` -> *26 network bits* out of 32 bits (Ipv4 always contains 32 bits)
- `32 - 26 = 6` -> *6 host bits* left
- `2^6 = 64` -> Total number of addresses
- `64 - Network address(192.168.1.1) + Broadcast address(192.168.1.63)` -> Leaves us with *62 usable IPs*

### **Decimal -> Binary**
`IP: 192.168.1.0`

|*Octet*|128	|64	|32	|16	|8	|4	|2	|1	|*Binary*|
|-------|-------|---|---|---|---|---|---|---|--------|
|192	|1	    |1	|0	|0	|0	|0	|0	|0	|11000000|
|168	|1	    |0	|1	|0	|1	|0	|0	|0	|10101000|
|1	    |0	    |0	|0	|0	|0	|0	|0	|1	|00000001|
|0  	|0	    |0	|0	|0	|0	|0	|0	|0	|00000000|

`11000000.10101000.00000001.00000000`

### **Binary -> Decimal**
`00001010.00010100.00011110.00101000`

|*Octet*|128	|64	|32	|16	|8	|4	|2	|1	|*Decimal*|
|-------|-------|---|---|---|---|---|---|---|--------|
|00001010|0	    |0	|0	|0	|1	|0	|1	|0	|8 + 2 = 10|
|00010100|0	    |0	|0	|1	|0	|1	|0	|0	|16 + 4 = 20|
|00011110|0	    |0	|0	|1	|1	|1	|1	|0	|16 + 8 + 4 + 2 = 30|
|00101000|0	    |0	|1	|0	|1	|0	|0	|0	|32 + 8 = 40|

`IP: 10.20.30.40`

---

## **NAT**
- Translates private → public IPs for internet access.
- Purpose: Conserves IPs, improves security, simplifies network design.

**Types:**
- **Static** -> One to one mapping. One private IP permanently mapped to 1 public IP
- **Dynamic** -> Private IP mapped to any free public IP. Changes depending on what's available.
- **PAT** -> Port Address Translation. Many private devices share 1 public IP using ports. Mostly used in homes.

---

## **Troubleshooting**
- **Common Issues:** Connectivity loss, slow performance, IP conflicts, DNS failures.
- **Tools:** ping, traceroute, nslookup, dig.
- **Workflow:** Observe → Check hardware → Verify configs → Test → Logs.

---

## **Cloud Networking**
- **Definition:** Virtualized networks in cloud environments.
- **VPC:** Private network in cloud.
- **Subnets:** Organize resources, control traffic.
- **Gateways:** Connect VPC to external networks.
