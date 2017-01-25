=======
 ROUTE
=======

ROUTE  Displays/Updates the unit's IP routing table.

This command allows the user to display/update the current IP routing
table of the unit.

ADD[[=aaa.bbb.ccc.ddd] [GATEWAY=aaa.bbb.ccc.ddd]]
    Allows the user to add a host route to the network routing tables,
    where 'aaa.bbb.ccc.ddd' represents a standard Internet address.
    For example:
    To indicate that the machine with Internet address 91.0.0.3 is the
    gateway to the destination host 90.0.0.0, enter:
    ROUTE ADD=90.0.0.0 GATEWAY=91.0.0.3
    Up to 6 permanent routes can be added to the routing table.

DEL|DELETE[[=aaa.bbb.ccc.ddd] [GATEWAY=aaa.bbb.ccc.ddd]]
    Allows the user to delete a gateway from the network routing table,
    where 'aaa.bbb.ccc.ddd' represents a standard Internet address.

GATEWAY[=aaa.bbb.ccc.ddd]
    Sets the current gateway in the network routing table to the supplied
    Internet address.  The gateway is where IP datagrams are routed when
    there is no specific routing table entry available for the
    destination IP network or host.
    If an empty gateway value is provided then the current gateway is
