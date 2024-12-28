# The Networking Behind Pivoting

## **Introduction**
Pivoting is a critical skill for penetration testers and red teamers. To master it, you must deeply understand foundational networking concepts. These concepts act as the building blocks of a strategy, enabling you to exploit paths, bypass restrictions, and maneuver within complex environments. Pivoting allows access to isolated networks and provides critical footholds for further exploration and exploitation.

---

## **IP Addressing and NICs: Understanding the Nodes**
Each system in a network requires an **IP address** to communicate. Without it, the system is isolated. IP addresses act as unique identifiers for systems, much like house addresses in the physical world. They can be:
- **Dynamic**: Assigned temporarily by a DHCP server. These are commonly used for workstations, IoT devices, and other non-critical systems. Their temporary nature can lead to changes in connectivity over time.
- **Static**: Assigned manually, often used for critical systems that require constant, predictable connectivity, such as:
  - **Servers**: File servers, web servers, database servers, etc.
  - **Routers**: Gateways for network traffic.
  - **Switches**: Devices that interconnect multiple devices in a network.
  - **Printers**: Office or production printers that must be consistently accessible.

### **Network Interface Controllers (NICs)**
- A NIC is the hardware or virtual interface that allows a device to connect to a network.
- **Single NIC**: A device with one NIC connects to only one network.
- **Multiple NICs**: A device with multiple NICs can connect to several networks simultaneously, making it an ideal pivot point.

> **Pro Tip**: When performing pivoting, always inspect for multiple NICs. These indicate that the host may have access to different network segments, allowing you to bypass segmentation.

---

### **Identifying NICs**

#### **Linux (ifconfig Output)**
To view network interfaces on a Linux system, use:
```bash
ifconfig
