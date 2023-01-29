# Virtual Links in OSPF

In this project, in order to advertise area 3 to the different areas, we need to make <b>Cr4</b> an ABR.
An ABR in OSPF is responsible for connecting different areas of the network and distributing routing information between them. In order for a router to serve as an ABR, it must have at least one link to the backbone area (area 0).

In some cases, it may not be possible to physically connect a router to the backbone area. In these situations, virtual links come into play as a solution.

### In order to get virtual link running, we have to get the following in order:
- We need to have the router ids.
- Virtual links have to be configured on both sides of the link.

## Virtual links configuration

If we take a look at our diagram below, we can see that the link that we have to form is between Jr4 and Cr4. Right now, Area 3 doesn't know about Area 1 or Area 0.

![image](https://user-images.githubusercontent.com/118945715/215355081-e4b8e3c3-ba31-4ab3-800e-8b138b085c48.png)


<b> First, we need the router id on both routers</b>

Cisco:
```commandline
show ip ospf
```
Juniper:
```commandline
show ospf overview
```
![image](https://user-images.githubusercontent.com/118945715/215355357-b1dfb4fc-6cfa-4f89-8379-b091d4261767.png) ![image](https://user-images.githubusercontent.com/118945715/215355380-0c513921-7043-4cc8-a694-135734c6509f.png)



<b> Now we do the virtual link configuration </b>

## Cisco configuration
In Cisco, we do the virtual link configuration under the ospf process level.

```commandline
router ospf 1
area 2 virtual link 111.111.2.4
```
The area that we see in this command, is the transit area. Means that if you are configuring a link between Area 3 and Area 0 on the Diagram, the traffic Area where the virtual link packet travels is Area 2. That's the Area we're gonna use in Cisco.

## Juniper Configuration
In Juniper, we do the virtual link configuration under the protocols level.

```commandline
edit protocols ospf
set area 0 virtual link neighbor-id 111.111.1.4 transit-area 2
```
Creating virtual links on Juniper is different than Cisco. Cisco's command uses transit area, but Juniper needs area 0 first before the transit area.
