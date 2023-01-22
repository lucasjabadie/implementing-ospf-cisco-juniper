# Virtual Links in OSPF

In this project, in order to advertise area 3 to the different areas, we need to make <b>Cr4</b> an ABR.
An ABR in OSPF is responsible for connecting different areas of the network and distributing routing information between them. In order for a router to serve as an ABR, it must have at least one link to the backbone area (area 0).

In some cases, it may not be possible to physically connect a router to the backbone area. In these situations, virtual links come into play as a solution.

### In order to get virtual link running, we have to get the following in order:
- We need to have the router ids.
- Virtual links have to be configured on both sides of the link.

