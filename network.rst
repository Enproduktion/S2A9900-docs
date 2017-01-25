=========
 NETWORK
=========

NETWORK  Displays/Changes the system's network and IP settings.

This commands displays the current network settings of the system and
allows the user to change them.

API_PORT=x
    Changes the API Server port number for this unit to that specified by
    'x'.
    The system must be restarted before the changes will take effect.
    Valid ports are 0 to 32767.  Note however, that the results may be
    unpredictable if the port number chosen is already in use (on this
    unit) by either the TELNET or SYSLOG facilities.

    Default port is 8008.

API_SERVER=ON|OFF
    Specifies whether or not the API Server capability is active.  The
    API interface relies on an active and enabled API Server for its
    communications with the system.
    The system must be restarted before the changes will take effect.
    Note: To affect the API Server connection availability only
    temporarily during the current power-cycle, refer to the API
    ENABLE/DISABLE command.

FIREWALL=ON|OFF
    Enables/disables the network firewall.

    Default value is ON.

GATEWAY=aaa.bbb.ccc.ddd
    Sets the current gateway in the network routing table to the supplied
    Internet address.  The gateway is where IP datagrams are routed when
    there is no specific routing table entry available for the
    destination IP network or host.
    Note that GATEWAY= (with no Internet address) will clear out the
    current gateway.

    IP=aaa.bbb.ccc.ddd
    Changes the IP address of the system.
    Warning: Changing the network IP address may temporarily shutdown
    cache coherency until the operation completes.

LEGACY_SNMP_TRAP=ON|OFF
    Specifies whether or not the SNMP generic traps will use a format
    that corresponds to the current MIB or an older format.

    Default is OFF.

LIMIT_SNMP=ON|OFF
    Specifies whether or not the SNMP functionality will only report
    component-level information, or all levels of information.

    Default is OFF.

NETMASK=aaa.bbb.ccc.ddd
    Changes the netmask of the system.

PING=PARTNER
    Attempts to ping the partner unit.

PING=aaa.bbb.ccc.ddd
    Attempts to ping the specified destination with a single packet.

PRIVATE
    Displays information about the private network device.

SNMP=ON|OFF
    Specifies whether or not the SNMP trap functionality is active.
    The system must be restarted before the changes will take effect.

SNMP_FIREWALL=ON|OFF
    Specifies whether or not SNMP is active or fully disabled.
    This function requires the main Firewall to be active.
    Turning on the SNMP Firewall will disable IHD functionality and
    will prevent communication with the UPS.

    Default is OFF.

SNTP=ON|OFF
    Specifies whether or not the system will periodically poll a STNP
    server for the time. The SNTP time server IP address is specified by
    NETWORK SNTPIP=aaa.bbb.ccc.ddd. The system will poll the timer server
    at 8 hour intervals. If the time update fails then the system will
    wait a minimum of 1 minute before polling again. An additional minute
    will be added to the delay after each failure until the maximum delay
    of 8 hours is reached. This will prevent the system from polling
    excessively on failures. An immediate update can be requested using
    the command TIME GETTIME or TIME GETTIME=aaa.bbb.ccc.ddd.

    The default setting is OFF.

SNTPIP=aaa.bbb.ccc.ddd
    Specifies an IP address of a SNTP time server for the system to poll.

SYSLOG=ON|OFF
    Specifies whether or not the Syslog capability is active.

SYSLOGIP=aaa.bbb.ccc.ddd or aaaa:bbbb:cccc:dddd:eeee:ffff:gggg:hhhh
    Changes the destination IP address for syslog packets. If the unit is
    coupled with a second unit and setup for dual mode, both units in the
    system will share the same syslog destination IP address but each
    unit can specify a different destination port.

SYSLOGPORT=x
    Changes the destination port number for syslog packets for this unit.
    If the unit is coupled with a second unit and setup for dual mode,
    both units in the system will share the same syslog destination IP
    address but each unit can specify a different destination port.
    Valid ports are 0 to 32767.  Note however, that the results may be
    unpredictable if the port number chosen is already in use (on this
    unit) by either the TELNET or API facilities.
    Default port is 514.

    TELNET=ON|OFF
    Specifies whether or not the Telnet capability is active.
    The system must be restarted before the changes will take effect.

    .. note::

        To affect telnet session availability only temporarily during
        the current power-cycle, refer to the TELNET ENABLE/DISABLE command.

TELNETLOGIN=x
    Changes the maximum number of seconds the system will wait for a new
    character during a Telnet login attempt to 'x'.  The system will
    allow 3 login attempts before disconecting the session.
    Valid wait times in seconds are 0 to 300 where 0 indicates to use the
    default of 120 seconds (2 minutes.)
    Default value is 0.

TELNETPORT=x
    Changes the Telnet port number for this unit to that specified by
    'x'.
    The system must be restarted before the changes will take effect.
    Valid ports are 0 to 32767.  Note however, that the results may be
    unpredictable if the port number chosen is already in use (on this
    unit) by either the API or SYSLOG facilities.
    Default port is 23.

TRAPIP=aaa.bbb.ccc.ddd or aaaa:bbbb:cccc:dddd:eeee:ffff:gggg:hhhh
    Changes the destination IP address for SNMP trap packets.
    The system must be restarted before the changes will take effect.

USAGE
    Displays the address resolution protocol map.  Also, displays ICMP
    (ping), general network, and IP, TCP, and UDP layer statistics.
