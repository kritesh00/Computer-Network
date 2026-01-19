# LAB 4: Subnetting and Supernetting Using Cisco Packet Tracer

## Objectives
1. To understand the logical division of IP networks through Subnetting and the aggregation of networks through Supernetting.
2. To design a variable length or fixed length subnet mask scheme and implement the topology using Cisco Packet Tracer to visualize the flow of packets between different subnets via a Router.

## Software and Hardware Requirements
1. Cisco Packet Tracer (Version 6.2 or higher)
2. Windows PC/Laptop

## Theory

### 1. Subnetting
Subnetting is the practice of dividing a single physical network into two or more smaller logical sub-networks (subnets). It involves borrowing bits from the host portion of the IP address to create a subnet field.

*   **Operation:** It works by applying a subnet mask that extends the default network portion. For example, borrowing 2 bits from a Class C /24 network creates 4 subnets. The router uses the subnet mask to determine which network segment an IP address belongs to.
*   **Application:** Used to improve network performance and security by reducing the size of the broadcast domain. It ensures that traffic meant for a local subnet stays local.

### 2. Supernetting
Supernetting, also known as Classless Inter-Domain Routing (CIDR) or route summarization, is the inverse of subnetting. It allows multiple smaller networks to be combined into a single larger network.

*   **Operation:** It involves manipulating the subnet mask to move the network boundary to the left (reducing the number of network bits). This creates a summary address that represents a block of contiguous networks.
*   **Application:** Used primarily to reduce the size of routing tables on routers, which reduces CPU and memory usage and speeds up the routing process on the Internet.

---

## Network Design

### Subnetting Calculations
*   **Base network:** 192.168.1.0/24
*   **Required number of subnets:** 4
*   **Number of IP addresses per subnet:** 64 (Block size)
*    /26 (Borrowed 2 bits: $2^2 = 4$ subnets)
*   **Subnet Mask:** 255.255.255.192

### Subnet Calculation Table

| Subnet | Network ID | 1st Host | Last Host | Broadcast ID |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 192.168.1.0 | 192.168.1.1 | 192.168.1.62 | 192.168.1.63 |
| 2 | 192.168.1.64 | 192.168.1.65 | 192.168.1.126 | 192.168.1.127 |
| 3 | 192.168.1.128 | 192.168.1.129 | 192.168.1.190 | 192.168.1.191 |
| 4 | 192.168.1.192 | 192.168.1.193 | 192.168.1.254 | 192.168.1.255 |

### Network Topology

**Subnetting:**
A topology was created using Router0 to connect two subnets: 192.168.1.0/26 and 192.168.1.64/26. Switch0 connects PC0, PC1, and PC2 in the first subnet, while Switch1 connects PC3, PC4, and PC5 in the second subnet. Both switches are connected to the router interfaces.

**Supernetting:**
The topology consists of one router, one switch, and four PCs (PC6–PC9). All PCs connect to the switch, which is connected to the router.

---

## Configuration Tables

### Subnetting Configuration

| Device | IPv4 | Subnet Mask | Default Gateway |
| :--- | :--- | :--- | :--- |
| Router0 (FastEthernet0/0) | 192.168.1.1 | 255.255.255.192 | N/A |
| Router0 (FastEthernet0/1) | 192.168.1.65 | 255.255.255.192 | N/A |
| PC0 (Subnet 1) | 192.168.1.2 | 255.255.255.192 | 192.168.1.1 |
| PC1 (Subnet 1) | 192.168.1.3 | 255.255.255.192 | 192.168.1.1 |
| PC2 (Subnet 1) | 192.168.1.4 | 255.255.255.192 | 192.168.1.1 |
| PC3 (Subnet 2) | 192.168.1.66 | 255.255.255.192 | 192.168.1.65 |
| PC4 (Subnet 2) | 192.168.1.67 | 255.255.255.192 | 192.168.1.65 |
| PC5 (Subnet 2) | 192.168.1.68 | 255.255.255.192 | 192.168.1.65 |

### Supernetting Configuration

| Device | IPv4 | Subnet Mask | Default Gateway |
| :--- | :--- | :--- | :--- |
| Router0 (FastEthernet0/0) | 192.168.0.1 | 255.255.252.0 | N/A |
| PC6 | 192.168.0.10 | 255.255.252.0 | 192.168.0.1 |
| PC7 | 192.168.1.10 | 255.255.252.0 | 192.168.0.1 |
| PC8 | 192.168.2.10 | 255.255.252.0 | 192.168.0.1 |
| PC9 | 192.168.3.10 | 255.255.252.0 | 192.168.0.1 |

---

## Connectivity Testing

*   **Ping PC0 to PC2:** Successful
*   **Ping PC0 to PC5:** Successful
*   **Ping PC6 to PC9:** Successful

## Result
The network was successfully configured. To verify the connectivity, a ping request was sent from PC0 (192.168.1.2) in Subnet 1 to PC2 (192.168.1.4) in Subnet 1 and again from PC0 (192.168.1.2) to PC5 (192.168.1.68) in Subnet 2. All packets were sent and received successfully, which validates the connection is correct. Similar testing was performed for the supernetting connection with successful results.

## Discussion and Conclusion
During the lab session, we implemented the concepts of subnetting and supernetting to better understand IP address management and network design. Subnetting allowed us to divide a large network into smaller subnets for efficient address utilization, while supernetting helped in combining networks to simplify routing.

Hence, the lab was completed with proper knowledge and implementation of subnetting and supernetting using Cisco Packet Tracer.