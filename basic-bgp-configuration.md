# Basic BGP Configuration

### Cr6 Configuration
```commandline
interface Loopback1
 ip address 20.20.10.1 255.255.255.252
!
interface Loopback2
 ip address 20.20.20.1 255.255.255.248
!         
interface Loopback3
 ip address 20.20.30.1 255.255.255.240
 
 router bgp 2023
 redistribute connected
 neighbor 3.3.2.1 remote-as 1023
 
```

### Cr5 Configuration

```commandline
router bgp 1023
 bgp log-neighbor-changes
 neighbor 3.3.2.2 remote-as 2
 
```

### Cr1 Configuration

```commandline
router bgp 1023
 bgp log-neighbor-changes
 neighbor 1.1.2.1 remote-as 1

```

### Jr1 Configuration

```commandline
}
    ge-0/0/9 {
        vlan-tagging;
        unit 0 {
            vlan-id 1;
            family inet {
                address 10.10.10.1/30;
            }
        }
        unit 1 {
            vlan-id 2;                  
            family inet {
                address 10.10.20.1/29;
            }
        }
        unit 2 {
            vlan-id 3;
            family inet {
                address 10.10.30.1/28;
            }
        }
    }
    fxp0 {
        unit 0 {
            family inet;
        }
    }
}
routing-options {
    autonomous-system 1;
}
protocols {
    bgp {
        export BGP-Routes;              
        group INE {
            type external;
            peer-as 1023;
            neighbor 1.1.1.2;
            neighbor 1.1.2.2;
        }
    }
    lldp {
        interface all;
        interface ge-0/0/1;
        interface ge-0/0/2;
    }
}
policy-options {
    policy-statement BGP-Routes {
        term 1 {
            from protocol direct;
            then accept;
        }
    }
}
```
