# Basic IP configuration

Before configuring OSPF on any device, it is essential to properly configure IP addresses on the interfaces. Additionally, to ensure proper identification and differentiation, it is a best practice to set a hostname on each device.

## Juniper example

Before making any changes on a Juniper device, it is necessary to establish root authentication. To configure root authentication on a Juniper device, use the following command:

```commandline
set system root-authentication plain text password
```
This command will prompt for a password to be entered twice.

After root authentication has been established, it is possible to proceed with configuring the hostname and IP addresses. The following commands can be used for this purpose:

```commandline
set system host-name Jr1
commit check

set interfaces ge-0/0/0 unit 0 family inet address 1.1.2.1/29
commit
```
It is highly recommended to use the command "commit check" before committing any changes. This command will verify if the changes can be committed and will provide detailed explanations in case of errors.

To view the configuration of interfaces, the following command can be used:
```commandline
show interfaces terse
```

## Cisco example

In Cisco routers, it is not necessary to set a password before making configuration changes. To configure basic IP addressing, start by setting the hostname of the device, then enter the configuration mode of the interface on which the IP address needs to be changed.

```commandline
hostname Cr1
interface e0/0
ip address 1.1.5.2 255.255.255.248
no shut
```

It is important to note that in Cisco routers, the subnet mask must be specified in octet notation, for example 255.255.255.248 for a /29 subnet. Additionally, by default, interfaces are shut down on Cisco routers, so the "no shutdown" command must be used to activate the interface.

To view the configuration of interfaces, use the following command:

```commandline
show ip interfaces brief
```
