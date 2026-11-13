# Network Security & Hardening Using Cisco Packet Tracer

![Cisco Packet Tracer](https://img.shields.io/badge/Network-Cisco%20Packet%20Tracer-blue)
![Security](https://img.shields.io/badge/Focus-Network%20Security-red)
![Status](https://img.shields.io/badge/Status-Completed-success)

## Project Overview

This project demonstrates the design, implementation, and hardening of an enterprise network for a simulated organisation called **SecureTech Solutions** using Cisco Packet Tracer.

The network is divided into separate departments using VLANs. Security controls such as Extended Access Control Lists (ACLs), SSH secure remote management, switch port security, and unused-port shutdown were implemented to improve network protection.

## Objectives

- Design an enterprise network topology.
- Implement department-based network segmentation using VLANs.
- Configure inter-VLAN routing using Router-on-a-Stick.
- Control communication between departments using Extended ACLs.
- Enable secure remote administration using SSH version 2.
- Configure switch port security.
- Disable unused switch ports.
- Verify network connectivity and security policies.

## Network Architecture

The simulated organisation contains four network segments:

| Department | VLAN | Network |
|---|---:|---|
| Human Resources | 10 | 192.168.10.0/24 |
| Information Technology | 20 | 192.168.20.0/24 |
| Finance | 30 | 192.168.30.0/24 |
| Company Server | 40 | 192.168.40.0/24 |

### Devices Used

- 1 Cisco 2911 Router
- 1 Cisco 2960 Switch
- 6 End-user PCs
- 1 Company Server

### Network Topology

![Network Topology](screenshots/01-network-topology.png)

## Technologies and Tools

- Cisco Packet Tracer
- Cisco IOS CLI
- VLAN
- IEEE 802.1Q
- Router-on-a-Stick
- Extended ACL
- SSH Version 2
- Switch Port Security
- Sticky MAC Address Learning

## Security Implementations

### 1. VLAN Segmentation

Four VLANs were configured to separate HR, IT, Finance, and Server networks. This provides logical network separation between departments.

### 2. Inter-VLAN Routing

Router-on-a-Stick was configured using router subinterfaces and 802.1Q encapsulation to enable communication between VLANs.

### 3. Access Control Lists

Extended ACLs were configured to restrict communication:

**HR Security Policy**
- Deny access to IT.
- Deny access to Finance.
- Permit access to the company server.
- Deny other destinations.

**Finance Security Policy**
- Deny access to HR.
- Deny access to IT.
- Permit access to the company server.
- Deny other destinations.

The IT network was not restricted by these two ACLs.

### 4. SSH Secure Remote Management

SSH version 2 was configured on the router and switch.

Remote access was verified from IT-PC1 to:
- Router: `192.168.20.1`
- Switch: `192.168.20.2`

### 5. Switch Port Security

Port security was configured on the seven active access ports.

- Maximum of one MAC address per port.
- Sticky MAC address learning.
- Restrict violation mode.

### 6. Unused Port Shutdown

Unused switch ports were administratively disabled to reduce the risk of unauthorised physical connections.

## IP Addressing

| Device | IP Address | Default Gateway |
|---|---|---|
| HR-PC1 | 192.168.10.10 | 192.168.10.1 |
| HR-PC2 | 192.168.10.11 | 192.168.10.1 |
| IT-PC1 | 192.168.20.10 | 192.168.20.1 |
| IT-PC2 | 192.168.20.11 | 192.168.20.1 |
| FIN-PC1 | 192.168.30.10 | 192.168.30.1 |
| FIN-PC2 | 192.168.30.11 | 192.168.30.1 |
| SRV-COMPANY | 192.168.40.10 | 192.168.40.1 |

## Testing and Results

| Test Scenario | Expected Result | Result |
|---|---|---|
| HR to HR Gateway | Allowed | Passed |
| HR to Company Server | Allowed | Passed |
| HR to IT | Blocked | Passed |
| HR to Finance | Blocked | Passed |
| Finance to Company Server | Allowed | Passed |
| Finance to HR | Blocked | Passed |
| Finance to IT | Blocked | Passed |
| Finance to Finance PC | Allowed | Passed |
| SSH to Router | Successful Login | Passed |
| SSH to Switch | Successful Login | Passed |
| Unused Switch Ports | Disabled | Passed |

## Project Evidence

Implementation screenshots and configuration verification are available in the [`screenshots`](screenshots/) folder.

## Project Files

- [Cisco Packet Tracer Project](SecureTech_Network_Security_Hardening.pkt)
- [Implementation Screenshots](screenshots/)

## Learning Outcomes

Through this project, I gained practical experience in:

- Enterprise network design and configuration.
- VLAN segmentation and inter-VLAN routing.
- Network traffic filtering using ACLs.
- Secure network device administration using SSH.
- Switch port security configuration.
- Network troubleshooting and connectivity testing.
- Documenting and verifying network security implementations.

## Conclusion

This project demonstrates the implementation of fundamental enterprise network security controls using Cisco Packet Tracer. It provided practical experience in network segmentation, access control, secure device administration, and switch hardening.

**Project Status:** Completed
