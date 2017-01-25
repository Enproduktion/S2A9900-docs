=======
 POWER
=======

POWER  Configures and displays the power information in the system.

Configures and displays the power information in the system.

STATUS[=ALL]
    Displays the current system power status. If only status is provided
    a text display will be provided. If STATUS=ALL is input, then a text
    input and a graphical indication of the system power will be
    displayed.

UPS_IP=aaa.bbb.ccc.ddd
    Sets the IP for the UPS SNMP Server.

UPS_MONITOR=OFF|ON
    This parameter enables and disables the UPS monitoring via SNMP.
    Default is ON.

UPS_PROBE
    Performs a network probe for the UPS on the given IP address. The
    probe will only discover and talk to known and supported UPS devices.
