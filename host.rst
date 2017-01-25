======
 HOST
======

HOST  Displays information about the host fibre channel ports.

This command is used to change the configuration settings for the host
fibre channel ports in the system and monitor their status.  The command
will display the current settings and status for each host port.  This
command will also display a list of the host users currently logged into
the system.

CONTROLPAGE
    This command allows the user to view the current settings of the SCSI
    Control Mode page (0x0A) for each host port.

ERRORPAGE
    This command allows the user to view the current settings of the SCSI
    Error Recovery Mode page (0x01) for each host port.

FRAME_SIZE
    This parameter allows the user to set/change the maximum transmitdata
    frame size per host port(s). The user is prompted for the desired
    transmit size as well as for the choice of the host port(s).

GUIDS
    Displays additional information about the GUIDs of our HCAs.

IBUSERS
    Displays additional information about all IB users logged in.

ID=x
    This parameter changes the hard loop ID of a host port.  The supplied
    value, 'x', is the fibre channel AL PA value which will be used by
    the host port.  The system will select a soft ID if the hard loop ID
    is already taken by another device.
    Refer to the manual for a list of valid loop IDs.
    This parameter is entered as an 8-bit hex value.

    Default is EF.

LIPINFO
    Shows the last LILP payload for all host ports.

PORT=x|ALL
    This parameter specifies the specific host port(s) to be affected
    when used in combination with any of the following other parameters:

    * ID,
    * TIMEOUT,
    * WWN.

    (If PORT is left unspecified, the user is prompted for his choice of
    host ports).
    Valid port values, 'x', are 1 to 4.

    Default is ALL host ports.

QERR=0|1
    This parameter allows the user to change the queue error management
    (QERR) field in the SCSI Control Mode page. This parameter determines
    what action is taken when a host command is terminated with check
    condition. When QERR=0, all outstanding host commands will resume
    after the ACA condition is cleared. When QERR=1, all outstanding host
    commands for the affected initiator will be aborted.
    The system only supports a TAS bit of 1 so no other initiators are
    affected.

    Default is 0.

SPEED
    This parameter allows the user to set/change the port speed on the
    host port(s). The user is prompted for the desired speed as well as
    for the choice of the host port(s).
    Note: When displaying the speed settings (which can be done using the
    'HOST' command), the following acronyms are used:

    * Gbps - Gigabits per second
    * NA   - Not Applicable

STATUS
    Displays the loop status of each host port and a count of the fibre
    channel errors encountered on each port.

STATUSCLEAR
    Resets the fibre channel error counts on each port.

TIMEOUT=x
    This parameter sets the host command timeout for an I/O request to
    the value specified by 'x'.
    The valid range for 'x' is 1 to 512 seconds.

    Default is 75 seconds.

WWN=x|DEFAULT
    This parameter is used to override the system ID and specify a
    different World Wide Name for a host port.
    The new World Wide Name value may be entered as one of:

    * 'x'     : a 64-bit hex value,
    * DEFAULT : Resets the World Wide name back to the default settings.
