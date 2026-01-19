# LAB 3: SIMULATION OF NETWORK DEVICES USING CISCO PACKET TRACER

## Objective

1. To get introduced with the application of Cisco Packet Tracer and simulate various network devices including Hubs, Switches, Bridges, Routers, and Repeaters.
2. To visualize the flow of Protocol Data Units (PDUs) and understand the difference in data transmission between broadcast and unicast devices.

## Theory

### Cisco Packet Tracer
Cisco Packet Tracer is a network simulation tool that allows students to create network topologies and imitate modern computer networks. The software allows users to simulate the configuration of Cisco routers and switches using a simulated command line interface. It represents network hardware as software objects, allowing students to visualize the flow of data packets without the need for physical cabling or hardware.

### 1. Hub
A **Hub** is a physical layer (Layer 1) networking device that is used to connect multiple devices in a network. It acts as a multiport repeater. It is considered a non-intelligent device because it does not store any MAC addresses.

*   **Operation:** When a hub receives a data packet (frame) on one port, it broadcasts that packet to all other ports irrespective of the destination address.
*   **Application:** Used in small networks where high traffic and security are not primary concerns.

### 2. Switch
A **Switch** is a data link layer (Layer 2) device that connects devices on a computer network by using packet switching to receive, process, and forward data to the destination device. Unlike a hub, a switch is an intelligent device.

*   **Operation:** It uses a MAC address table to determine which port the data needs to be sent to. It performs unicast transmission after the initial learning phase.
*   **Application:** Used in enterprise networks to manage traffic efficiency and reduce collisions.

### 3. Bridge
A **Bridge** is a Layer 2 device used to connect two or more network segments (LANs). It works by inspecting the MAC address of the data packets.

*   **Operation:** It reads the destination MAC address and decides whether to forward the packet to the other segment or filter it out (keep it in the local segment). This helps in reducing traffic on the network.
*   **Application:** Used to extend a network or segment a large network into smaller, more manageable collision domains.

### 4. Router
A **Router** is a network layer (Layer 3) device that connects two or more different networks (e.g., connecting a LAN to a WAN or two different subnets). It uses IP addresses to make routing decisions.

*   **Operation:** It maintains a routing table to determine the best path for a packet to reach its destination. It acts as a gateway between networks.
*   **Application:** Used to connect home or office networks to the internet and to route traffic between distinct subnets.

### 5. Repeater
A **Repeater** is a Layer 1 device designed to regenerate or replicate a signal.

*   **Operation:** It receives a signal, cleans it of noise, amplifies it, and retransmits it. It does not look at packet data; it purely deals with signal strength.
*   **Application:** Used to extend the transmission distance of a network cable beyond its physical limitations (e.g., Ethernet limit of 100 meters).

### Gateway
A **Gateway** is a network node that serves as an access point to another network. It often involves a router that is configured to pass traffic from a local subnet to outside networks.

*   **Operation:** It translates protocols if necessary and routes data directed to IP addresses outside the local network range.

---

## Observation

### 1. Hub Implementation

| Device Name | Interface | IP Address | Subnet Mask |
| :--- | :--- | :--- | :--- |
| PC0 | FastEthernet0 | 192.168.1.1 | 255.255.255.0 |
| PC1 | FastEthernet0 | 192.168.1.2 | 255.255.255.0 |
| PC2 | FastEthernet0 | 192.168.1.3 | 255.255.255.0 |
| PC3 | FastEthernet0 | 192.168.1.4 | 255.255.255.0 |
| PC4 | FastEthernet0 | 192.168.1.5 | 255.255.255.0 |
| PC5 | FastEthernet0 | 192.168.1.6 | 255.255.255.0 |

In this simulation, a Star topology was created using a Hub. PC0 is connected to the Hub-PT, likewise PC1, PC2, PC3, PC4, and PC5 are connected to the remaining ports of the Hub using Copper Straight-Through cables. When a PDU was sent from PC5 to PC0, the Hub received the packet and broadcasted it to all connected devices (PC4, PC3, PC2, PC1, and PC0). The intended recipient accepted it, while others rejected it.

### 2. Switch Implementation

| Device Name | Interface | IP Address | Subnet Mask |
| :--- | :--- | :--- | :--- |
| PC6 | FastEthernet0 | 192.168.1.10 | 255.255.255.0 |
| PC7 | FastEthernet0 | 192.168.1.11 | 255.255.255.0 |
| PC8 | FastEthernet0 | 192.168.1.12 | 255.255.255.0 |
| Laptop0 | FastEthernet0 | 192.168.1.13 | 255.255.255.0 |
| Laptop1 | FastEthernet0 | 192.168.1.14 | 255.255.255.0 |
| Laptop2 | FastEthernet0 | 192.168.1.15 | 255.255.255.0 |

A Switch was used to connect multiple devices. PC6, PC7, and PC8 are connected to the Switch 2960-24TT, likewise Laptop0, Laptop1, and Laptop2 are connected to the switch ports. Unlike the Hub, once the Switch learned the MAC addresses, the message flow was observed to be unicast. The packet was sent directly from the source to the destination without disturbing other ports.

### 3. Bridge Implementation

| Device Name | IP Address | Subnet Mask |
| :--- | :--- | :--- |
| Switch0 | 192.168.1.2 | 255.255.255.0 |
| Switch1 | 10.10.10.2 | 255.255.255.0 |
| Bridge0 | 192.168.1.1 | 255.255.255.0 |

Two network segments were connected using a Bridge. The left segment switch is connected to Bridge-PT Port 0, likewise the right segment switch is connected to Bridge-PT Port 1. The simulation demonstrated how the Bridge filters traffic. It only allows traffic to cross to the other segment if the destination address belongs to a device on that side.

### 4. Repeater Implementation

| Device Name | Connection Type | Status |
| :--- | :--- | :--- |
| Repeater0 | Port 0 to Left Segment | Active |
| Repeater0 | Port 1 to Right Segment | Active |

A Repeater was placed between two long-distance segments. The left network wire is connected to the Repeater Port 0, likewise the right network wire is connected to Repeater Port 1. The signal propagation was observed, ensuring that the packet could travel the extended distance without signal degradation.

### 5. Router Implementation

| Device Name | Interface | IP Address | Subnet Mask | Gateway |
| :--- | :--- | :--- | :--- | :--- |
| Router0 | Gig0/0 (LAN 1) | 192.168.1.1 | 255.255.255.0 | N/A |
| Router0 | Gig0/1 (LAN 2) | 10.10.10.1 | 255.255.255.0 | N/A |
| PC-LAN1 | FastEthernet0 | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 |
| PC-LAN2 | FastEthernet0 | 10.10.10.2 | 255.255.255.0 | 10.10.10.1 |

A Router was configured to connect two different Local Area Networks (LAN 1: 192.168.1.x and LAN 2: 10.10.10.x). The Switch for LAN 1 is connected to Router interface GigabitEthernet0/0, likewise the Switch for LAN 2 is connected to Router interface GigabitEthernet0/1. The Router acted as a Gateway, allowing packets to travel from one network ID to another.

## Discussion and Conclusion

During the lab session, we implemented the concepts of network device configuration and traffic management to better understand how different devices operate within a network. We were able to configure different devices like Routers, Hubs. The PDU are sent to check the connectivity of the devices. Hence, the lab was completed with practical knowledge and implementation of Hubs, Switches, and Routers using Cisco Packet Tracer.