# Inter-Area Summarization

Inter-Area summarization is used to reduce the amount of routing information exchanged between OSPF areas. This helps to reduce the size of the OSPF routing table and improve the scalability of the network.

If we take a look at the  network diagram, inter-area summarization can be implemented to provide a summarized version of the routes within Area 1 to OSPF areas 0, 2, and 3, rather than transmitting the entire routing table.

---

To simplify the routes in Area-1, you need to use summarization commands on router Cr2 (the router connecting Area-1 and Area-0). This is because only the router directly connected to the area with the specific addresses has the power to simplify those addresses.

```commandline
router ospf 1
area 1 range 1.1.0.0 255.255.240.0
```

<b> Show command: </b>

- show ip route ospf 

![image](https://user-images.githubusercontent.com/118945715/215362120-81082ffe-eb18-4879-9fc9-d8724f8b2d18.png)

We can see now that <b> Cr3 </b> now has the routes for Area 1 all summarized.

# OSPF Redistribution


```commandline
router ospf 1
redistribute bgp 1023 subnets
```

Cisco:
- show ip route
- show ip route ospf

Juniper:
- show route
- show route | find **


![image](https://user-images.githubusercontent.com/118945715/215743949-8add2fce-0a56-43a7-acd0-ba982f1f2022.png)

After activating redistribution on <b> Cr1  </b> we can see now that Jr2 has learned all the routes to Jr1 via OSPF.

---

After doing the same configuration on <b> Cr5 </b>, we can see now that <b> Cr4 </b> has learned all the routes from <b> Cr6 </b> via OSPF. And, it has also learned the routes from Jr1 from the previous configuration.

![image](https://user-images.githubusercontent.com/118945715/215745252-edb935fa-1beb-4f02-9946-34716f708e7c.png)
