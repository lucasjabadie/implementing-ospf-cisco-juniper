# Basic BGP Configuration

This project is not focused on BGP specifically, therefore I will just provide a explanation of its purpose and the commands.

The utilization of BGP or another routing protocol is necessary in order to facilitate route redistribution.

## BPG AS 1
### Jr1 Configuration

```commandline
edit interfaces ge-0/0/9
set vlan-tagging
set unit 0 vlan-id 1
set unit 0 family inet address 20.23.0.1/30
set unit 1 vlan-id 2
set unit 1 family inet address 20.23.1.1/29
set unit 2 vlan-id 3
set unit 2 family inet address 20.23.2.1/28
commit

edit policy-options
edit policy-statement BGP-Routes
set term 1 from protocol direct
set term 1 then accept
commit

edit routing-options
set autonomous-system 1
commit

edit protocols bgp
set export BGP-Routes
set group LAB type external peer-as 1023 neighbor 1.1.6.2
commit
```

- The interface ge-0/0/9 is configured for VLAN tagging with multiple VLAN subinterfaces and assigned IP addresses. These subinterfaces will be useful for populating Cr1's IP route table with IP addresses learned from BGP.
- A policy-statement named "BGP-Routes" is created to accept direct protocol traffic and applied to the BGP configuration. A peer group is also defined with external type, peer AS 1023, and neighbor IP 1.1.6.2, which is Cr1.
- The device's autonomous system number is set to 1.

### Cr1 Configuration

```commandline
router bgp 1023
 bgp log-neighbor-changes
 neighbor 1.1.6.1 remote-as 1
```
- This setups BGP with an autonomous system number of 1023 and that he neighbor IP address is 1.1.6.1 and specifies that its autonomous system number is 1.
- And of course, BGP log-neighbor-changes which enables logging of BGP neighbor state changes:

![image](https://user-images.githubusercontent.com/118945715/215349897-d393dfbe-33b7-4740-b436-857ed22ae106.png)




## BGP AS 2
### Cr6 Configuration
```commandline
interface Loopback1
 ip address 15.0.0.2 255.255.255.252
!
interface Loopback2
 ip address 15.0.1.2 255.255.255.248
!         
interface Loopback3
 ip address 15.0.2.2 255.255.255.240
 
 router bgp 2
 redistribute connected
 neighbor 3.0.2.1 remote-as 1023
 
```

### Cr5 Configuration

```commandline
router bgp 1023
 bgp log-neighbor-changes
 neighbor 3.0.2.2 remote-as 2
 
```
