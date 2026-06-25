# Lab 03 — VLAN segmentation with DHCP and Access Control

## Objective
In this lab, I have designed and implemented a VLAN segmented network using Cisco Packet Tracer and configure VLAN aware DHCP and VLAN based IPv4 Access Control Lists (ACLs) to control address allocation and inter VLAN traffic.

After completing this lab, you will be able to:

•	Design a VLAN based switched network

•	Create and assign VLANs on a Cisco switch

•	Configure trunking and inter VLAN routing

•	Configure DHCP services for multiple VLANs

•	Apply IPv4 ACLs to enforce VLAN based access policies

•	Verify correct operation using IOS CLI commands

---

## Topology

<img width="943" height="633" alt="image" src="https://github.com/user-attachments/assets/faa8340f-2458-470f-a733-4ff48bfb33d4" />


---

## Scenario

An organisation requires logical separation of users while maintaining a shared physical network infrastructure. To achieve this, VLANs are implemented at Layer 2, with inter VLAN routing providing controlled communication between user groups.

To fully integrate the design:

•	DHCP must be configured per VLAN

•	Access control policies must be enforced between VLANs

## Requirements
Part 1: VLAN Design and Layer 2 Segmentation 			              

Design and build the network topology using Cisco Packet Tracer with the following requirements:

•	One switch named S1

•	One router named R1

•	Four PCs: PC A, PC B, PC C, PC D

•	Two VLANs: 

o	VLAN 10 – Staff

o	VLAN 20 – Students

•	PC A and PC B belong to VLAN 10

•	PC C and PC D belong to VLAN 20

•	S1 is connected to R1 using a single physical link

Part 2: VLAN Creation and Port Assignment   

a. Create and name the required VLANs on S1, then assign all PC connected ports as access ports in the correct VLAN. Configure VLAN 10 and VLAN 20 using appropriate names.

Command Template 
vlan <VLAN_ID>
name <VLAN_NAME>

b. For Access Port Configuration (S1)
Command Template 
interface <ACCESS_INTERFACE>
switchport mode access
switchport access vlan <VLAN_ID>
no shutdown

Part 3: Trunking and Inter-VLAN Routing         

a. Enable communication between VLANs using router on a stick

Command Template for Trunk configuration (S1)
interface <TRUNK_INTERFACE>
switchport mode trunk
no shutdown

b. For router sub interface configuration (R1), create one sub interface per VLAN ensuring each VLAN uses a unique gateway address

Command Template 
interface <PHYSICAL_INTERFACE>.<VLAN_ID>
encapsulation dot1Q <VLAN_ID>
ip address <GATEWAY_IP> <SUBNET_MASK>
no shutdown

Part 4: VLAN-Aware DHCP Configuration                                                                

Configure DHCP services per VLAN on R1. Each VLAN must use its corresponding router sub interface as the default gateway.

a. Exclude gateway addresses (R1): Exclude all router interface IP addresses from dynamic allocation
Command Template 
ip dhcp excluded-address <START_IP> <END_IP>

b. DHCP Pool Configuration (R1): Create one DHCP pool per VLAN ensuring PCs in each VLAN receive IP addresses from the correct subnet.

Command Template 
ip dhcp pool <POOL_NAME>
network <NETWORK_ADDRESS> <SUBNET_MASK>
default-router <VLAN_GATEWAY_IP>

c. DHCP Verification

Command Template 
show ip dhcp binding

Part 5: VLAN-based IPv4 Access Control                                                                          [2 Marks]
Apply access control policies between VLANs.

Security Policy

•	Staff VLAN (VLAN 10): Full access

•	Student VLAN (VLAN 20): 

o	ICMP access to Staff VLAN is permitted

o	HTTP access to Staff VLAN is denied

a. Extended ACL Configuration (R1)

Command Template 
ip access-list extended <ACL_NAME>
permit icmp <STUDENT_NETWORK> <WILDCARD> <STAFF_NETWORK> <WILDCARD>
deny tcp <STUDENT_NETWORK> <WILDCARD> <STAFF_NETWORK> <WILDCARD> eq 80
permit ip any any

b. Apply ACL to VLAN Sub interface (R1), and choose the correct direction based on traffic flow. 

Command Template 
interface <SUBINTERFACE_ID>
ip access-group <ACL_NAME> <in | out>

Part 6: Verification              

Verify the network operation using the commands below:   

show vlan brief

show interfaces trunk

show ip dhcp binding

show access-lists

---

## Configuration

<img width="928" height="1143" alt="image" src="https://github.com/user-attachments/assets/f5f3ac19-2398-4acd-a7d4-7873c0a9d670" />
<img width="417" height="109" alt="image" src="https://github.com/user-attachments/assets/5ca26928-41d2-4851-8e6b-b58b74d179ba" />
<img width="940" height="762" alt="image" src="https://github.com/user-attachments/assets/b14f4e1b-2882-4aab-bef2-da2f507d7ed1" />
<img width="940" height="788" alt="image" src="https://github.com/user-attachments/assets/ae58f028-d9d6-494c-bdb3-db9ca6c11ff1" />
<img width="940" height="355" alt="image" src="https://github.com/user-attachments/assets/8865db2a-5878-4dc4-be71-4a2f391d1950" />
<img width="824" height="298" alt="image" src="https://github.com/user-attachments/assets/28932bfd-3283-4b59-885f-ab689b97b1da" />
<img width="883" height="350" alt="image" src="https://github.com/user-attachments/assets/2177ab9d-0bd8-466a-879f-d0370aa06d6d" />
<img width="940" height="298" alt="image" src="https://github.com/user-attachments/assets/eb37aa24-90bc-4e48-b4bf-a910eb31b04c" />
<img width="940" height="213" alt="image" src="https://github.com/user-attachments/assets/0d213205-a469-4335-9ff9-20f63ad4301c" />
<img width="922" height="184" alt="image" src="https://github.com/user-attachments/assets/3be230b8-b488-44b9-a37f-b43510c54a06" />


---


## Result
<img width="352" height="36" alt="image" src="https://github.com/user-attachments/assets/0eea4323-52b2-4425-8c8f-2299fb17b7a7" />
<img width="985" height="67" alt="image" src="https://github.com/user-attachments/assets/5a1dd35e-a56d-44d9-9936-4d61d520e844" />
