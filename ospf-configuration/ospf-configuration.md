# Basic OSPF Configuration

One of the benefits of using OSPF is that it's a link state protocol. This means it keeps track of the state of each link in the network and uses this information to find the best path for data to travel. This makes configuring OSPF simple and easy.

## Cisco Configuration

In terms of configuring OSPF on Cisco routers, there are two main methods. The first, and older method, is to enable OSPF on specific interfaces using the command "network x.x.x.x", where x.x.x.x represents the IP address range of the interface. However, there is a newer method of configuring OSPF on Cisco routers, which involves enabling OSPF on an interface with a simple command such as "ip ospf 1 area 0". This command is more concise and easier to understand, especially when configuring multiple interfaces.

### Example
```commandline
interface fa0/0
ip ospf 1 area 0
```
- This configures OSPF with a process ID of 1 and assigns the interface FastEthernet0/0 to area 0.
- You can also configure OSPF on multiple interfaces using the following command:

```commandline
int range FastEthernet0/0 - 3
ip ospf 1 area 0
```
![image](https://user-images.githubusercontent.com/118945715/213869413-3585e0cd-0cbd-4ae8-a6dd-e9c84deea886.png)

Cr2 is an ABR, it will be responsible for managing multiple areas within the OSPF network. It is important to note that for this purpose, it is not necessary to utilize separate process IDs for different areas as the router ID is an internal configuration. A successful OSPF adjacency can be determined by observing the OSPF state transition from LOADING to FULL.

### Show commands:
- show ip ospf neighbor
- show ip ospf interfaces
- show ip protocols

If the loopback interface has been previously correctly configured, the output of the command "show ip protocols" should indicate this:

![image](https://user-images.githubusercontent.com/118945715/213870135-087ae199-184c-46aa-8a06-658a5652dca9.png)


## Juniper Configuration

In Juniper, there are two methods for configuring OSPF protocol. The first method involves entering the "edit protocols ospf" command and subsequently configuring interfaces and areas. The second method, which I personally find more convenient, involves using the full command to configure OSPF on multiple interfaces. This can be done by pressing the "up" key and editing the relevant interface and area. 

### Example
```commandline
set protocols ospf area 0.0.0.0 interface ge-0/0/0.0
commit
```
- This configures OSPF on the interface ge-0/0/0.0 and assigns it to area 0.0.0.0 (area 0)
- You can also configure OSPF on multiple interfaces using the following command:
```commandline
set protocols ospf area 0.0.0.0 interface ge-0/0/0.0, ge-0/0/1.0
commit check
commit
```
And like I said, I find more convenient just pressing the "up" key and editing the previous command. But you can do whatever feels more confortable for you.

### Show commands:
- show ospf neighbor
- show ospf interface [brief | detail]
- show ospf overview
- show route protocol ospf

If the loopback interface has been previously correctly configured, the output of the command "show ospf overview" should indicate this:
![image](https://user-images.githubusercontent.com/118945715/213872067-cc5df1fb-79fc-4e6d-9793-076fbd68b3cf.png)
