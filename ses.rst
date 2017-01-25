=====
 SES
=====

SES  Displays all current disk enclosure faults.

This command will display a list of all current enclosure faults
detected by the SCSI Enclosure Services (SES) as well as provide a means
to access SES specific functions such as disk, channel, lun, or tier
visual identification.

DOWNLOAD
    Allows the operator to Download firmware to the enclosures. During
    downloading, SES will suspend enclosure monitoring.

ENCLRESET=tc
    This parameter commands the system to send a RESET command to a
    specific enclosure, 'tc', where 't' is the tier and 'c' is the
    channel of the enclosure.
    The valid range for 't' is <1..128>.
    The valid range for 'c' is <ABCDEFGHPS>.

EVENTLOG=tc
    This parameter commands the system to get and print to the console an
    Event Log from the specified enclosure, 'tc', where 't' is the tier
    and 'c' is the channel of the enclosure.
    The valid range for 't' is <1..128>.
    The valid range for 'c' is <ABCDEFGHPS>.

ID=OFF
    This parameter clears the visual indication task that is currently in
    progress and restores the system to its original visual state.

IDCHANNEL=c
    This parameter commands the system to provide a visual indication of
    the specified channel, 'c'.
    The valid range for 'c' is <ABCDEFGHPS>.

IDDISK=tc
    This parameter commands the system to provide a visual indication of
    the specified drive, 'tc', where 't' is the tier and 'c' is the
    channel.
    The valid range for 't' is <1..128>.
    The valid range for 'c' is <ABCDEFGHPS>.

IDLUN=n
    This parameter commands the system to provide a visual indication of
    the specified LUN, 'n'.
    The valid range for 'n' is <0..the max. number of LUNs> (which is set
    at 128 in the current system).

IDTIER=t
    This parameter commands the system to provide a visual indication of
    the specified tier, 't'.
    The valid range for 't' is <1..128>.

MUTE=c
    This parameter commands the system to mute the enclosure alarms on
    the specified channel, 'c'.
    The valid range for 'c' is <ABCDEFGHPS>.

M_WAIT
    This parameter displays the current value for the SES device
    monitoring rate.  The value is given in seconds.

M_WAIT=x
    This parameter sets the SES device monitoring rate for the system to
    'x'.  The monitoring rate is given in seconds.
    The valid range for 'x' is <4..90>.

    .. warning::

	Improper use of this command can prevent the SES monitors
	from detecting an enclosure fault before the enclosure automatically
	shuts down.

OFF
    Allows the user to save the SES state to the parameter blocks, and
    shutdown the SES monitors.

ON
    Allows the user to save the SES state to the parameter blocks, and
    startup the SES monitors.

SHOW=tc
    Allows the user to display the configuration information and the
    status information returned from an SES Enclosure Status page for the
    SES device for the specified drive, 'tc', where 't' is the tier and
    'c' is the channel.
    The valid range for 't' is <1..128>.
    The valid range for 'c' is <ABCDEFGHPS>.

SHOWALL
    Allows the user to display all configuration information for all the
    SES devices on all channels.

SHOWDEVICES
    Allows the user to display all the SES devices on all channels.

UNMUTE=c
    This parameter commands the system to unmute the enclosure alarms on
    the specified channel, 'c'.
    The valid range for 'c' is <ABCDEFGHPS>.
