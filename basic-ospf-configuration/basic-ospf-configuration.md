# Basic OSPF Configuration

Assuming you already did the basic ip config, we are gonna start configuring basic OSPF on both Cisco and Juniper.

Meaning of the address: 111.111 means nothing, just random number. Then, the 1 on the third octect is for Cisco, and 2 is for Juniper. And the 1 from the fourth octect is because is the first Router.

## On Cisco

To configure the loopback interface on a Cisco device:

```commandline
Interface lo0
ip address 111.111.1.1 255.255.255.255
```

## On Juniper

To configure the loopback interface on a Juniper device: 

```commandline
set interfaces lo0 unit 0 family inet address 111.111.2.1/32
```
