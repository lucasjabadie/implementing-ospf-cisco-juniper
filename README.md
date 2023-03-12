# Implementing OSPF on Cisco and Juniper

In this project, we will demonstrate the deployment of OSPF routing protocols on Cisco and Juniper devices using the Eve-NG virtualization platform. The goal is to provide a detailed guide that will guide you through each step of the process, including the setup of a virtual lab environment, configuration of OSPF and BGP protocols, and testing and verification of the configurations.


![image](https://user-images.githubusercontent.com/118945715/215745652-e4696eeb-9ec0-412f-b8a2-6bfb05eacf39.png)


I suggest starting with the basics of IP and BGP configuration before moving on to OSPF. So then we can fully focus on OSPF. There's also a documentation repository available if you want to see the configurations of all the devices we're using.


At the end of the project:
- Routers in area 1 should be able to ping area 3.
- Other areas should learn routes from area 1 in summarized form.
- BGP routes should be learned via OSPF.
- All OSPF connections should be secured with OSPF Authentication.
