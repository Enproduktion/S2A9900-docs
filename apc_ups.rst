=========
 APC_UPS
=========

APC_UPS  Displays the status of the APC UPS trap monitor.

This command is used to display the status of the APC UPS SNMP trap
monitor. The monitor may also be enabled or disabled by this command.
Any outstanding APC UPS traps may be also cleared through this command.
Note:  The SNMP community string on the UPS should be set to S2A.

CLEAR_FAULTS
    This parameter deletes all pending APC UPS faults from the fault
    list. All APC UPS events that disabled writeback caching will be
    cleared.

MONITOR=ON|OFF
    This parameter enables and disables the APC UPS monitor.
    Default is OFF.
