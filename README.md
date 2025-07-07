# 🛰️ Simple ISP Customer LAN with NAT & Port Forwarding (Packet Tracer Lab)

This lab simulates a **real-world scenario** an ISP Field Technician or Junior Network Engineer might handle:  
- Provisioning a customer LAN  
- Configuring DHCP  
- Verifying connectivity  
- Setting up NAT Overload (PAT)  
- Implementing Port Forwarding for a hosted service.

---

## ⚡ **Lab Topology**

- **Router0:** ISP edge router providing DHCP, PAT, and Port Forwarding.
- **Switch0:** Distributes connections to customer devices.
- **PC0:** End-user device.
- **Server0:** Hosted internal service for port forwarding.

---

## ✅ **Step 1: Initial Topology**

![image](https://github.com/user-attachments/assets/a9c2ea97-782f-4450-8121-73136d7fd037)
Shows Router0, Switch0, PC0, and Server0 placed in the workspace and connected logically.

---

## ✅ **Step 2: Basic Cabling**

![image](https://github.com/user-attachments/assets/0330afde-6917-4a5b-8f05-55e136bfcb1e) 
Shows devices connected:
- Router0 GigabitEthernet0/0 to Switch0
- PC0 and Server0 connected to Switch0
- Router0 GigabitEthernet0/1 connected to ISP-facing link.

---

## ✅ **Step 3A: Configure Router LAN Interface**

![image](https://github.com/user-attachments/assets/808c6f82-fd78-4ddf-b4fc-1fa7c8a72d4c) 
Configured `GigabitEthernet0/0` with IP `192.168.10.1/24` and brought the interface up (`no shutdown`).

Purpose:
- Sets default gateway for LAN devices.

---

## ✅ **Step 3B: Configure DHCP**

![image](https://github.com/user-attachments/assets/fefff467-0b4b-4384-a9b4-96ed689e5f43)
Created DHCP pool:
- Excluded `.1-.10` for static use.
- LAN_POOL assigns `.11` and up.
- Sets Router0 as default gateway and Google DNS.

Purpose:
- Automates client IP configuration.

---

## ✅ **Step 4A: Verify DHCP on Clients**

![image](https://github.com/user-attachments/assets/72ffc2f5-8d45-47da-859f-fb82ae528cd2)
![image](https://github.com/user-attachments/assets/5d81bc2a-e449-4f43-922e-5dcf16e640a6)
PC0 and Server0 both successfully received IPs via DHCP in the `192.168.10.0/24` network.

Purpose:
- Confirms DHCP server is working.

---

## ✅ **Step 4B: Verify LAN Connectivity**

![image](https://github.com/user-attachments/assets/3d133891-96dd-4ecf-b578-38e8a0c900c9) 
Ping results show:
- PC0 can reach Router0 (gateway).
- PC0 can reach Server0.

Purpose:
- Confirms Layer 2 & 3 connectivity is operational.

---

## ✅ **Step 5A: NAT Overload (PAT) Config**

![image](https://github.com/user-attachments/assets/6ac82238-98e3-4df6-8f07-9180d833f362)
Configured:
- GigabitEthernet0/1 as WAN link with public IP `20.0.0.2/30`.
- NAT ACL to allow LAN subnet to use NAT.
- Applied NAT Overload so multiple LAN devices can share one public IP.

Purpose:
- Provides internet access for LAN hosts.

---

## ✅ **Step 5B: Port Forwarding**

![image](https://github.com/user-attachments/assets/7f908a91-be8a-44d2-b58e-0ba1a341703d)
Configured static NAT to forward:
- External `20.0.0.2:8080` → Internal `192.168.10.12:80`.

Purpose:
- Simulates a customer hosting a web service or game server accessible from outside.

---

## 🗂️ **Key Skills Practiced**

- Basic router and switch provisioning.
- Interface IP configuration.
- DHCP setup and testing.
- NAT Overload (PAT).
- Static NAT (Port Forwarding).
- Verifying LAN connectivity.

---

## ✅ **Outcome**

This lab demonstrates readiness to troubleshoot common **customer network issues**:
- DHCP failures
- LAN communication
- Public-to-private port mapping

---

## 📌 **Next Steps**

- Test more services like HTTP and ping from “Internet side” to validate port forwarding.
- Extend with firewall ACLs for security.

---

**Thanks for checking out this lab!**  
Ideal for entry-level network engineer practice and showcasing real-world troubleshooting knowledge.

---

