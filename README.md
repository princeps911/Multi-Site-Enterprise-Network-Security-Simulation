# Multi-Site-Enterprise-Network-Security-Simulation
I recently completed a deep-dive simulation of an Enterprise WAN for a downstream oil &amp; gas scenario. I built a multi-site network from scratch, configured static routing between regional depots and headquarters, and implemented Extended ACLs to secure executive endpoints.

##Objective: To design, configure, and secure a Wide Area Network (WAN) connecting a regional petroleum depot to a corporate headquarters, simulating real-world logistics operations .

1. The Architecture (Virtual Lab Setup)
Using Cisco Packet Tracer, I built a three-tier network environment:

Depot Segment: A Local Area Network (LAN) consisting of a 2911 Router (Gateway), a 2960 Switch, a Manager’s Laptop, and a Sales Database Server.

Lagos HQ Segment: A corporate LAN with a 2911 Router, a 2960 Switch, and a CEO’s Laptop.

The WAN Link: A serial/crossover connection between the two gateways using a dedicated 10.0.0.x IP subnet to simulate inter-state connectivity.

2. Network Configuration (The Logic)
I configured the devices using the Cisco IOS Command Line Interface (CLI):

IP Addressing: Assigned static IPv4 addresses across different subnets (192.168.1.0/24 for the Depot and 192.168.2.0/24 for HQ).

Interface Management: Successfully brought up interfaces using no shutdown and assigned gateway addresses.

Static Routing: Implemented routing tables on both gateways (ip route) to ensure packets could find the path between the Depot and the Head Office.

3. Security Hardening (The "Officer" Layer)
To protect sensitive executive data, I implemented Extended Access Control Lists (ACLs):

The Rule: Created a security policy named BLOCK_DEPOT_TO_CEO.

The Logic: Specifically denied traffic from the Depot Manager’s IP to the CEO’s IP while permitting all other essential business traffic (permit ip any any).

Placement: Applied the ACL to the inbound interface of the Lagos Gateway to filter traffic at the network perimeter.

4. Testing & Validation
I validated the build through three rigorous tests:

Connectivity Test: Successful ping from the Depot to the HQ, proving the routing logic was sound.

Security Test: Verified the ACL by attempting a ping to the CEO’s laptop, resulting in a "Destination Host Unreachable"—proving the security policy was active.

Remote Management: Configured VTY lines and passwords to allow secure remote access for troubleshooting regional hardware from a central location.
