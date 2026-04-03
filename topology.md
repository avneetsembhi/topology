# Home Network Documentation

**Student Name:** Avneet Kaur Sembhi  
**Course:** Technical Writing and Documentation  

---

# 1. Physical Topology

##  Overview
The physical topology represents how network devices are physically arranged in the home environment, including their locations, cabling, and connection types (Ethernet and Wi-Fi).

---

##  Physical Topology Diagram

![Physical Topology](./physical-topology.png)

---

##  Device Locations

| Device           | Location      | Connection Type | Interface Used |
|------------------|--------------|----------------|----------------|
| Wireless Router  | Living Room  | Wired + Wi-Fi  | Internet Port |
| PC               | Bedroom      | Ethernet       | FastEthernet0 |
| Laptop           | Bedroom      | Ethernet       | FastEthernet0 |
| Printer          | Study Room   | Ethernet       | FastEthernet0 |
| Smartphone       | Anywhere     | Wi-Fi          | Wireless |
| Tablet           | Anywhere     | Wi-Fi          | Wireless |

---

##  Physical Connections

### Ethernet (Wired)
- PC → Router (FastEthernet0)
- Laptop → Router (FastEthernet0)
- Printer → Router (FastEthernet0)

### Wi-Fi (Wireless)
- Smartphone → Router  
- Tablet → Router

All wired devices use FastEthernet interfaces to connect to the router, while wireless devices use the router’s wireless interface.

---

##  Physical Layout Description
- The **Wireless Router** is centrally located in the **Living Room** to provide optimal wireless coverage.
- The **PC and Laptop** are located in the **Bedroom** and connected via Ethernet cables.
- The **Printer** is placed in the **Study Room** and connected via Ethernet.
- The **Smartphone and Tablet** connect wirelessly from any location within the home.

---

#  2. Logical Topology

##  Overview
The logical topology represents how data flows within the network and how devices communicate with each other.

---

##  Logical Topology Diagram

![Logical Topology](./logical-topology.PNG)

---

##  Network Design
- **Topology Type:** Star Topology  
- All devices connect to a **central wireless router**

---

##  Data Flow

```
Internet → ISP → Wireless Router (192.168.1.1)
            ↓
   ---------------------------------
   |        |        |             |
  PC     Laptop   Printer   Wireless Devices
                               |
                        Smartphone / Tablet
```

### 📡 Data Flow Explanation

- All incoming internet traffic first reaches the **ISP**, then passes to the **Wireless Router (192.168.1.1)**.
- The router performs **Network Address Translation (NAT)** to allow multiple devices to share a single public IP address.
- The router assigns IP addresses using **DHCP** to wireless devices (Smartphone and Tablet).
- Wired devices (PC, Laptop, Printer) use **static IP addresses** for stable communication.
- When a device sends data:
  - Internal communication (e.g., PC → Printer) stays within the local network
  - External communication (e.g., Laptop → Internet) is routed through the router
- The router also handles:
  - **DNS requests** (resolving domain names like google.com)
  - **Firewall protection** to secure the network
- Both wired and wireless devices communicate through the router, ensuring seamless connectivity across the network.
##  Network Characteristics
- Single LAN network (`192.168.1.0/24`)
- No VLAN segmentation
- Router manages all traffic and communication

---

#  3. Addressing Documentation

| Device        | IP Address    | Subnet Mask     | Default Gateway | DNS       |
|---------------|--------------|----------------|----------------|----------|
| Router        | 192.168.1.1  | 255.255.255.0  | N/A            | 8.8.8.8  |
| PC            | 192.168.1.2  | 255.255.255.0  | 192.168.1.1    | 8.8.8.8  |
| Laptop        | 192.168.1.3  | 255.255.255.0  | 192.168.1.1    | 8.8.8.8  |
| Printer       | 192.168.1.4  | 255.255.255.0  | 192.168.1.1    | 8.8.8.8  |
| Smartphone    | DHCP         | DHCP           | DHCP           | DHCP     |
| Tablet        | DHCP         | DHCP           | DHCP           | DHCP     |

---

#  4. Network Devices and Services

##  Wireless Router
The wireless router is the central device in the network and performs the following functions:
- Acts as a **Default Gateway**
- Provides **DHCP services**
- Enables **wireless connectivity**
- Routes traffic between internal network and the Internet

---

##  Network Services

| Service | Description |
|--------|------------|
| DHCP   | Automatically assigns IP addresses to wireless devices |
| DNS    | Resolves domain names using Google DNS (8.8.8.8) |
| Internet | Provides external connectivity via ISP |

---

#  5. Device Configurations

## 📡 Router Configuration
- Default Gateway: 192.168.1.1  
- DHCP Service: Enabled  
- DHCP Range: 192.168.1.100 – 192.168.1.200  
- DNS Server: 8.8.8.8  
- NAT: Enabled (allows multiple devices to access the internet)  
- Firewall: Enabled for network protection  
- Wireless SSID: Home_Network  
- Wireless Security: WPA2 Encryption  

---

## 🖥️ Wired Devices (PC, Laptop, Printer)
- Configured with **static IP addresses** for consistent connectivity  
- Manual configuration includes:
  - IP Address (e.g., 192.168.1.2, 192.168.1.3, 192.168.1.4)  
  - Subnet Mask: 255.255.255.0  
  - Default Gateway: 192.168.1.1  
  - DNS Server: 8.8.8.8  
- Connected using Ethernet cables via FastEthernet interfaces  

---

## 📱 Wireless Devices (Smartphone, Tablet)
- Configured using **DHCP (automatic configuration)**  
- Automatically receive:
  - IP Address  
  - Subnet Mask  
  - Default Gateway  
  - DNS Server  
- Connected to the network using Wi-Fi (SSID: Home_Network)  

---

## 🔄 Configuration Summary
- Combination of **static IP (wired devices)** and **dynamic IP (wireless devices)**  
- Router centrally manages all configurations  
- Ensures stable connectivity, easy management, and efficient network performance  

#  6. Credential Security

To securely manage login credentials:

- A **password manager** (e.g., Bitwarden) is used to store credentials securely
- Default router username and password have been changed
- Wi-Fi network is secured using **WPA2 encryption**
- No sensitive information is stored in plain text

---


# 7. Testing and Verification

The following tests were performed to verify network functionality and ensure proper communication between all devices:

### 🔍 Connectivity Testing
- Used ping command to test communication between devices:

```
ping 192.168.1.3   (PC → Laptop)
ping 192.168.1.4   (PC → Printer)
ping 192.168.1.2   (Laptop → PC)
```

---

### 🌐 Internet Testing
- Tested internet connectivity using external server:

```
ping 8.8.8.8
```

---

### 📡 Router Verification
- Verified connectivity to the default gateway:

```
ping 192.168.1.1
```

---

### 🖨️ Printer Testing
- Verified printer accessibility over the network:

```
ping 192.168.1.4
```

---

### 📶 Wireless Connectivity
- Smartphone and Tablet connected via Wi-Fi  
- Verified DHCP IP assignment and internet access  

---

All tests were successful, confirming that the network is fully functional and properly configured.
