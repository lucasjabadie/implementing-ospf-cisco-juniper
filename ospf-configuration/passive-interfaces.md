# Passive Interfaces on OSPF

In this project, we will utilize OSPF passive interfaces on routers that are connected to external networks. The interfaces that are configured as passive will not send or receive OSPF hello packets. This feature could be useful for variety of reasons, such as:

- Resource optimization: By not sending or receiving OSPF hello packets, we can reduce the CPU and memory usage on the router.
- Security: Passive interfaces can prevent unwanted adjacencies or peering sessions from being established on the network, providing an additional layer of security.

### Network Diagram

By looking at the diagram, we can see that the interfaces we should configure as passive are <b>Cr1 e0/3</b> and <b>Cr5 e0/1</b>

## Cisco configuration example:

In Cisco, we configure passive interfaces at the OSPF process level, not at the interface level.

```commandline
router ospf 1
passive-interface GigabitEthernet0/2
```

## Juniper configuration example:

In Juniper, we configure passive interfaces at the protocols level.

```commandline
set protocols ospf area 1 interface ge-0/0/1.0 passive
commit
```
