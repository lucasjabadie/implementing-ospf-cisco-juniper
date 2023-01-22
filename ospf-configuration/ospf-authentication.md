# OSPF Authentication

For this project, we will use OSPF MD5 authentication. For simpler testing or lab environments, a basic plaintext authentication can be used. In real-world scenarios where more security is needed, we can use encryption protocols like IPsec to add an extra layer of security to OSPF.

## Cisco Configuration

- Authentication of OSPF neighbor relationships must be configured at the interface level, not on the OSPF process.
- Configuration must be performed on both interfaces that will establish the neighbor relationship.
- The key password must be matched on both neighboring interfaces.
- The key number must be matched on both neighboring interfaces.

```commandline
interface g0/1
ip ospf authentication message-digest
ip ospf message-digest-key 1 md5 cisco123
```
We do the same commands on both neighboring interfaces.
### Show command

```commandline
show ip ospf interface g0/1
```
You can see it has sucessfully paired a key because of the "Youngest key id is 1" and that the adjancency is up because of the "Adjacent neighbor count is 1"

## Juniper Configuration

- Authentication of OSPF neighbor relationships must be configured beneath the protocols level and then at the interface level.
- Configuration must be performed on both interfaces that will establish the neighbor relationship.
- The key password must be matched on both neighboring interfaces.
- The key number must be matched on both neighboring interfaces.

```commandline
edit protocols ospf area 1 interface ge-0/0/1.0
set authentication md5 1 key juniper123
commit
```
We do the same commands on both neighboring interfaces.

### Show command

```commandline
show ospf interface ge-0/0/.1 extensive
```
You can see it has sucessfully paired a key because of the "Auth type: MD5" and that the adjancency is up because of the "Adj count: 1"
