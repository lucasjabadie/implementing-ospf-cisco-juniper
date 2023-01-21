# Basic OSPF Configuration

One of the benefits of using OSPF is that it's a link state protocol. This means it keeps track of the state of each link in the network and uses this information to find the best path for data to travel. This makes configuring OSPF simple and easy.

## Cisco Configuration

In terms of configuring OSPF on Cisco routers, there are two main methods. The first, and older method, is to enable OSPF on specific interfaces using the command "network x.x.x.x", where x.x.x.x represents the IP address range of the interface. However, there is a newer method of configuring OSPF on Cisco routers, which involves enabling OSPF on an interface with a simple command such as "ip ospf 1 area 0". This command is more concise and easier to understand, especially when configuring multiple interfaces.
