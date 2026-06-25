# Lab 02 — DHCP and IPv4 ACLs


## Objective
In this lab, I have configured DHCP services and IPv4 Access Control Lists (ACLs) on a Cisco router to dynamically assign IP addresses and control traffic between multiple IPv4 networks.

Upon completion, I am able to:

•	Configure DHCP address pools on a router

•	Verify DHCP address assignment

•	Configure standard and extended IPv4 ACLs

•	Apply ACLs to router interfaces

•	Verify ACL functionality using IOS CLI commands



---

## Topology
Design the network topology using Cisco packet tracer. The network consists of:

•	One router (R1)

•	One switch (S1)

•	Three LANs

•	Multiple end devices

All devices are properly connected.

<img width="700" height="426" alt="image" src="https://github.com/user-attachments/assets/b3b1bede-fbed-463b-a6b0-d64885f4b240" />

---

## Scenario

Router R1 connects three separate IPv4 networks.

One IPv4 network is connected through a switch (S1), while the other two networks are directly connected to the router.
R1 is responsible for:

•	Assigning IP addresses dynamically using DHCP

•	Controlling inter network traffic using ACLs

No routing protocols or additional security configuration are required.

## Requirements
Addressing Information 
Router Interfaces:
<img width="593" height="107" alt="image" src="https://github.com/user-attachments/assets/173c2fb3-30a6-4fdd-b566-da926729906b" />

End Devices (DHCP Clients)
PC-A, PC-B, PC-C, PC-D must obtain their IPv4 addressing information automatically. 

Part 1: Configure DHCP on R1
Configure R1 as a DHCP server to provide IP addresses for:

•	192.168.30.0/24

•	192.168.40.0/24

•	192.168.50.0/24
The default gateway for each subnet must be the router interface address.

a.	Exclude IP addresses that should not be assigned dynamically (e.g., router interfaces).
Command Template 

ip dhcp excluded-address <START_IP> <END_IP>
b.	Create one DHCP pool per IPv4 network.

Command Template 
ip dhcp pool <POOL_NAME>
network <NETWORK_ADDRESS> <SUBNET_MASK>
default-router <DEFAULT_GATEWAY>

c.	Configure all PCs to use DHCP and verify successful address assignment.

Verification Command  

show ip dhcp binding

You can record addressing details for one PC in the below table:

<img width="562" height="486" alt="image" src="https://github.com/user-attachments/assets/9bf254f8-a254-4fb9-ad03-9af2455ee54b" />

Part 2: Verify Network Connectivity                                                      
Before configuring ACLs, verify end to end connectivity.

From PC A, test connectivity to:

•	PC B

•	PC D

Part 3: Configure a Standard IPv4 ACL                                                                            
Security Requirement

•	Only PC A is permitted to access the 192.168.40.0/24 network

•	All other hosts from the 192.168.30.0/24 network must be denied

•	Access to other networks must not be affected

a. Create the Standard ACL

•	Use a numbered standard ACL 

Command Template 
access-list <ACL_NUMBER> permit <SOURCE_IP> <WILDCARD_MASK>
access-list <ACL_NUMBER> deny <NETWORK_ADDRESS> <WILDCARD_MASK>

b. Apply the Standard ACL

•	Apply the ACL to the correct interface and in the correct direction.
Command Template 

interface <INTERFACE_ID>
ip access-group <ACL_NUMBER> <in | out>

Part 4: Configure an Extended IPv4 ACL                                                                          [4 Marks]
Security Requirement

•	Permit ICMP traffic from the 192.168.30.0/24 network to the 192.168.50.0/24 network 
•	Deny HTTP traffic between these networks 

•	Permit all other IP traffic between these networks

a. Create and apply the Extended ACL

•	Use a named extended ACL and apply it closest to the source.

Command Template 
ip access-list extended <ACL_NAME>
permit icmp <SOURCE_NETWORK> <WILDCARD> <DEST_NETWORK> <WILDCARD>
deny tcp <SOURCE_NETWORK> <WILDCARD> <DEST_NETWORK> <WILDCARD> eq 80
permit ip <SOURCE_NETWORK> <WILDCARD> <DEST_NETWORK> <WILDCARD>

interface <INTERFACE_ID>
ip access-group <ACL_NAME> <in | ou

Part 5: Verification and Testing                                                                                       
Use IOS commands to verify DHCP and ACL operation.

Command Template 

show ip dhcp binding
show access-lists
show ip interface <INTERFACE_ID>



---

## Configuration

cisco
Part 1: Configure DHCP on R1:
A.
<img width="940" height="1181" alt="image" src="https://github.com/user-attachments/assets/12936986-c0e3-4d90-8048-ee613cbf1b70" />
B.
<img width="940" height="204" alt="image" src="https://github.com/user-attachments/assets/d9350b41-487c-49bf-8591-8c4db9385fe4" />
C.
<img width="940" height="456" alt="image" src="https://github.com/user-attachments/assets/1a5fd786-a4c8-4030-bf9d-ef5fa85e3920" />
<img width="940" height="465" alt="image" src="https://github.com/user-attachments/assets/8b2d7eaa-d575-4e19-bd35-69ba36e8f07a" />
<img width="940" height="481" alt="image" src="https://github.com/user-attachments/assets/afeeea85-d5db-4072-bb65-72997bbde0d8" />
<img width="940" height="454" alt="image" src="https://github.com/user-attachments/assets/61fef2fb-48ec-4008-90ad-32b3e497206d" />

Verification Command  
show ip dhcp binding
<img width="940" height="202" alt="image" src="https://github.com/user-attachments/assets/b8ba73e1-e687-48cc-a92a-46758f9936e0" />

Part 2: Verify Network Connectivity 

<img width="940" height="948" alt="image" src="https://github.com/user-attachments/assets/eb921c2d-f8cf-4c65-9603-4c3735ea52b8" />
<img width="940" height="360" alt="image" src="https://github.com/user-attachments/assets/80bda23d-f0c4-4046-a5ad-6c5c2930e81c" />
<img width="940" height="809" alt="image" src="https://github.com/user-attachments/assets/55a3971b-8117-42f1-bbb9-6a2bf42c5420" />

Part 3: Configure a Standard IPv4 ACL                                                                             

A.
<img width="820" height="170" alt="image" src="https://github.com/user-attachments/assets/8aae29be-3c79-48c5-8bcd-f99662cc0f37" />
B.
<img width="580" height="53" alt="image" src="https://github.com/user-attachments/assets/1167e513-30dd-4671-98e1-183b714cc60e" />

Part 4: Configure an Extended IPv4 ACL                                                                          

<img width="920" height="270" alt="image" src="https://github.com/user-attachments/assets/90611e06-b09e-4ce0-b72a-4e3bd21be3c6" />

Part 5: Verification and Testing

<img width="940" height="1173" alt="image" src="https://github.com/user-attachments/assets/aa7a59e9-9a9a-4ba7-87de-2e80c1c19530" />
<img width="940" height="189" alt="image" src="https://github.com/user-attachments/assets/036682fb-ac08-4ab0-a65c-cbc6eb71d997" />


---


## Result
<img width="360" height="126" alt="image" src="https://github.com/user-attachments/assets/9473cdee-3d23-4c49-a19b-7d1ec202d6c6" />
<img width="985" height="67" alt="image" src="https://github.com/user-attachments/assets/5a1dd35e-a56d-44d9-9936-4d61d520e844" />
