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
- **1. Physical:** Raw bits over cables/Wi-Fi.
- **2. Data Link:** Frames, local delivery.
- **3. Network:** IP addressing, routing.
- **4. Transport:** TCP/UDP delivery.
- **5. Session:** Manages communication sessions.
- **6. Presentation:** Data formatting, encryption.
- **7. Application:** User-facing apps.

### **TCP/IP 4 Layers**
- **1. Application:** Apps & protocols (HTTP, DNS).
- **2. Transport:** TCP/UDP.
- **3. Internet:** IP routing.
- **4. Network Access:** Physical + Data Link.

**Key Idea:** OSI = conceptual; TCP/IP = practical.

### **DNS**
- Translates domain names → IP addresses.
- Components: Name servers, zone files, resource records (A, AAAA, CNAME, MX, TXT).
- Tools: nslookup, dig, /etc/hosts.
- Process: Resolver → Root → TLD → Authoritative → IP → Browser.

---

## **Routing**
- **Definition:** Determines best path for data.
- **Types:** Static vs Dynamic.
- **Protocols:** OSPF (internal), BGP (between networks).

---

## **Subnetting & CIDR**
- Splits networks into smaller segments.
- CIDR: /n = network bits.
- Example: 192.168.1.0/26 → Usable IPs: 192.168.1.1–62.
- **Subnet Masks:** Divide network & host parts.

---

## **NAT**
- Translates private → public IPs for internet access.
- Types: Static, Dynamic, PAT.
- Purpose: Conserves IPs, improves security, simplifies network design.

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
