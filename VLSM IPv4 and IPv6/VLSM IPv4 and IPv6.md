# Lab 01 — VLSM IPv4 and IPv6


## Objective
In this lab, I have designed and implemented an efficient IP addressing scheme using Variable Length Subnet Masking (VLSM) for both IPv4 and IPv6 networks.
After completing this lab, I am able to:

•	Analyse network requirements to determine appropriate subnet sizes

•	Apply VLSM techniques to subdivide an IPv4 address space

•	Assign IPv4 and IPv6 addresses to network devices

•	Configure IPv4 and IPv6 addresses on routers, switches, and hosts

•	Verify network connectivity using Cisco Packet Tracer and IOS commands



---

## Topology
<img width="820" height="312" alt="image" src="https://github.com/user-attachments/assets/d6dccdb0-48bf-4ba8-9058-c74e1aae2080" />

---

## Scenario

•	An organisation has been allocated a single IPv4 network and an IPv6 prefix and must divide these address spaces to support multiple networks with different host requirements.

•	To maximise address efficiency, the network administrator must use Variable Length Subnet Masking (VLSM) for IPv4 and appropriate subnetting techniques for IPv6.

•	In this lab, you will:

•	Subnet an IPv4 address block using VLSM based on specific host requirements

•	Create multiple IPv6 subnets from a given IPv6 prefix

•	Assign IP addresses to network devices

•	Implement the network using Cisco Packet Tracer

•	Verify connectivity using IPv4 and IPv6

•	No routing protocols are required, as all networks are directly connected.

## Requirements

Part 1: Develop an IP Addressing Scheme			

a. Based on the above topology, subnet the IPv4 network below to provide IP addresses to two subnets (networks) that will support the required number of hosts. All work must be shown using the IP Addressing worksheet below. 
<img width="627" height="263" alt="image" src="https://github.com/user-attachments/assets/6102e7be-8cf4-4fde-a588-6e6959b46248" />
<img width="652" height="252" alt="image" src="https://github.com/user-attachments/assets/b1e01129-465f-45ad-b029-847eba350252" />

b. Record your subnet assignment in the table below.  
1)	Assign the first IPv4 address of each subnet to a router interface.
(i)	subnet A is hosted on R1 G0/0/1
(ii)	subnet B is hosted on R1 G0/0/0
2)	Assign the last IPv4 address of each subnet to the PC NIC
3)	Assign the second IPv4 address of subnet A to S1
<img width="528" height="170" alt="image" src="https://github.com/user-attachments/assets/94944869-631b-409f-9890-e34a85f56620" />

c. Use the IPv6 address 2001:db8:acad::/48 and create two subnets for use in this network. Increment the subnet ID field consecutively by two. Record the IPv6 addresses in the table.
<img width="507" height="131" alt="image" src="https://github.com/user-attachments/assets/9be66a50-a352-4dcb-b2e7-7fe7702561f5" />

d. Record the IPv6 address information for each device. 
Note: use FE80::1 as the link-local address on both router interfaces. 
<img width="505" height="187" alt="image" src="https://github.com/user-attachments/assets/05331f48-1111-4537-ae7a-4cff4f233f9f" />

Part 2: Implement the Provided Topology, Configure Device IP Address and Security Settings using Cisco Packet Tracer

Step 1: Configuration tasks for R1 on Packet tracer include the following:
<img width="511" height="492" alt="image" src="https://github.com/user-attachments/assets/8ae61c5a-d5de-4530-aa15-2158aabcded1" />

Step 2: Configuration tasks for S1 on Packet tracer include the following:
<img width="525" height="402" alt="image" src="https://github.com/user-attachments/assets/6e414bea-8657-4521-9baa-b68721bdacf0" />

---

## Configuration

cisco
Step 3: Configuration tasks for host computers
After configuring each host computer, record the host network settings with the ipconfig /all command.
<img width="605" height="285" alt="image" src="https://github.com/user-attachments/assets/a3c44f6d-1692-4c22-afb4-1f54ca5ba0af" />
<img width="940" height="722" alt="image" src="https://github.com/user-attachments/assets/72111814-e4d3-4028-9a1b-e03c588a7612" />
<img width="596" height="277" alt="image" src="https://github.com/user-attachments/assets/d8d0e971-f86f-4faf-b76c-fac984dd15fd" />
<img width="940" height="675" alt="image" src="https://github.com/user-attachments/assets/1f841de5-8da0-4194-add8-41ac5b652ce2" />

Step 4: Test and Verify IPv4 and IPv6 End-to-End Connectivity 
Use the ping command to test IPv4 and IPv6 connectivity between all network devices.
<img width="557" height="487" alt="image" src="https://github.com/user-attachments/assets/209726e7-e14e-478c-8293-f29c3f2de7a2" />

Part 3: Use the IOS CLI to Gather Device Information using Cisco Packet Tracer                                                                                     
Enter the appropriate CLI command needed to display the following on R1:
<img width="523" height="335" alt="image" src="https://github.com/user-attachments/assets/a0216d1a-7846-42f2-859a-e9aab22622b7" />


---


## Result

<img width="395" height="138" alt="image" src="https://github.com/user-attachments/assets/a5571d4c-aafa-4785-867b-b5adb71e6ecc" />
<img width="985" height="67" alt="image" src="https://github.com/user-attachments/assets/5a1dd35e-a56d-44d9-9936-4d61d520e844" />


