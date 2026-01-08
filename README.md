# GlobalTech-Ethernet-LAN-Design
# Designing an Ethernet LAN for GlobalTech Solutions

## Introduction

An IP network is the backbone of modern digital communication, enabling devices such as computers, phones, printers, and servers to communicate using the Internet Protocol (IP). The global Internet itself is a collection of interconnected IP networks, governed by protocols that ensure data is delivered accurately and efficiently.

Logical network design is a crucial phase in system and network development. It focuses on defining *what* the system should do rather than *how* it will be implemented. By using abstraction, logical design breaks a system into manageable components and clearly defines their relationships. In networking, this includes data modelling, IP addressing, routing, and security considerations.

Network addressing assigns unique identifiers to devices using IPv4/IPv6 and MAC addresses. Broadcast addresses enable communication with all devices in a subnet. With IPv4 address exhaustion, efficient address management using techniques such as VLSM is essential. Good IP planning ensures scalability, performance, and long-term infrastructure viability.

---

## Project Information

**Company:** GlobalTech Solutions
**Location:** Sydney, Australia
**Industry:** Semiconductor & Wireless Technologies (Wi-Fi, Bluetooth)

### Scenario

GlobalTech Solutions operates from two buildings:

* **Building 1:** Administration, Customer Service
* **Building 2:** Sales, Marketing, Research & Development

The company expects **10% growth over the next 5 years**, requiring a scalable and secure Ethernet LAN.

---

## Objectives

* Design a robust Ethernet LAN
* Support current and future growth
* Apply Cisco three-layer hierarchical model
* Implement VLSM-based IP addressing
* Ensure security, scalability, and cost efficiency

---

## Design Requirements

### Departments & Employees

| Department             | Employees |
| ---------------------- | --------- |
| Research & Development | 32        |
| Sales & Marketing      | 20        |
| Administration         | 12        |
| Customer Service       | 6         |

Each department includes:

* Minimum **2 network printers**
* Shared office spaces
* Manager office
* Reception area
* Meeting room
* Network equipment room

Each floor size: **30m × 16m**

---

## Network Architecture

* Cisco **Three-Layer Hierarchical Model**:

  * Core Layer
  * Distribution Layer
  * Access Layer
* FastEthernet fiber backbone (**100Base-FX**)
* Default Gateway: **192.168.40.39**
* Distinct subnet per department

---

## Security & Expansion

* Access control policies for sensitive departments
* Secure VPN-based remote access
* Scalable IP addressing using VLSM
* Secure Wi-Fi for staff and guest access

---

## Budget

* Total allocated budget: **$50,000 AUD**
* Includes:

  * Hardware
  * Installation & configuration
  * Project management

---

## Network Summary

| Network          | Total Hosts | Router Interfaces | Total IPs |
| ---------------- | ----------- | ----------------- | --------- |
| Administration   | 14          | 1                 | 16        |
| Customer Service | 8           | 1                 | 11        |
| Sales            | 22          | 1                 | 26        |
| Research         | 34          | 1                 | 40        |

---

## IP Subnetting Design (VLSM)

### Step 1: IP Requirements

| Network          | Required IPs            |
| ---------------- | ----------------------- |
| Administration   | 12 + 2 + 1 + 1 = **16** |
| Customer Service | 6 + 2 + 1 + 1 = **11**  |
| Sales            | 20 + 2 + 2 + 1 = **26** |
| Research         | 32 + 2 + 4 + 1 = **40** |

> Each subnet includes 1 Network ID and 1 Broadcast Address

---

### Step 2: Subnet Size Selection

| Department       | Required IPs | Subnet | CIDR |
| ---------------- | ------------ | ------ | ---- |
| Customer Service | 11           | 16     | /28  |
| Administration   | 16           | 16     | /28  |
| Sales            | 26           | 32     | /27  |
| Research         | 40           | 64     | /26  |

Total available IPs: **256** (189.70.7.0/24)
Total required IPs: **93**

---

### Step 3: Subnet Allocation (Largest to Smallest)

| Network ID   | CIDR | Size | Department       |
| ------------ | ---- | ---- | ---------------- |
| 189.70.7.0   | /26  | 64   | Research         |
| 189.70.7.64  | /27  | 32   | Sales            |
| 189.70.7.96  | /28  | 16   | Administration   |
| 189.70.7.112 | /28  | 16   | Customer Service |
| 189.70.7.128 | /26  | 64   | Unused           |
| 189.70.7.192 | /26  | 64   | Unused           |

---

## IP Addressing Plan

### Research & Development

* Subnet: /26
* Network: 189.70.7.0
* Broadcast: 189.70.7.63
* Host Range: 189.70.7.1 – 189.70.7.62
* Reserved for growth: 30 IPs

### Sales & Marketing

* Subnet: /27
* Network: 189.70.7.64
* Broadcast: 189.70.7.95
* Host Range: 189.70.7.65 – 189.70.7.94
* Reserved for growth: 5 IPs

### Administration

* Subnet: /28
* Network: 189.70.7.96
* Broadcast: 189.70.7.111
* Host Range: 189.70.7.97 – 189.70.7.110

### Customer Service

* Subnet: /28
* Network: 189.70.7.112
* Broadcast: 189.70.7.127
* Host Range: 189.70.7.113 – 189.70.7.126

---

## Router Interface IP Allocation

**Router R1**

| Interface | IP Address   | Department             |
| --------- | ------------ | ---------------------- |
| Gi0/0/0   | 189.70.7.120 | Switch                 |
| Gi0/1/1   | 189.70.7.65  | Sales & Marketing      |
| Gi0/1/2   | 189.70.7.97  | Administration         |
| Gi0/1/3   | 189.70.7.113 | Customer Service       |
| Gi0/2/1   | 189.70.7.2   | Research & Development |

---

## Project Deliverables

* **Phase 1:** Initial Network Design (15%)
* **Phase 2:** IP Addressing Scheme (15%)
* **Phase 3:** Implementation & Final Report (15%)
* **Presentation:** Session 11 (10%)

---

## Conclusion

This project delivers a scalable, secure, and cost-efficient Ethernet LAN for GlobalTech Solutions. By applying Cisco’s hierarchical design model and VLSM-based IP planning, the network supports future growth, improves performance, and ensures long-term sustainability.
