======
 DISK
======

DISK  Displays information about the disks in the system.

This command is used to change the configuration settings for the disks
in the system and monitor the status of the disk channels.  The command
will display the current disk configuration settings and the status of
each disk channel.  The INFO= parameter can be used to display all of
the information about a disk in the system.  The LIST parameter will
display a list of the disks installed in the system and indicate how
many were found.

AGINGLIMIT=x|OFF
    Sets the maximum time a command should wait in the disk command queue
    for.
    This parameter is for Hitachi SAS drives only.
    Each unit of this timer is 50 ms, where 0 is 50 ms.
    Range: 0 to 4 (50 to 250 milliseconds) or OFF.
    Default is 3, (200 milliseconds)

AUTOREASSIGN=ON|OFF
    Allows the user to turn on or off whether bad blocks will be
    reassigned when a medium error occurs on a healthy tier.
    Default is ON.

CMD_TIMEOUT=x
    This parameter sets the retry disk timeout (in seconds) for an I/O
    request.  The retry timeout value indicates the maximum amount of
    time that is allotted to receive a reply for each retry of an I/O
    request. If the I/O request does not complete within this time, it is
    aborted and potentially retried: if there is still time remaining in
    the overall disk timeout to allow for another retry, it is retried;
    if not, it completes with an error status.
    This parameter must be smaller than or equal to TIMEOUT.
    Valid range is 1 to 512 seconds.
    Recommended value for SAS drives is 11 seconds.
    Recommended value for SATA drives is 31 seconds.  Setting the timeout
    below the recommended values can cause disk failures.
    Default is 31 seconds.

DEFECTLIST[=tc]
    Allows the user to display the number of defects in the defect list
    for the specified disk. The defect list contains all the physical
    sectors on the disk that the drive has identified as bad, and to
    which the disk's hardware prevents access.  The list is classified
    into two types: the permanent list and the grown list.  The permanent
    list consists of the bad sectors that are identified by the disk
    manufacturer; the grown list consists of the bad sectors that are
    found after the disk has left the factory (and which can be added to
    at any time).
    The disk is specified by its tier and channel locations, 'tc', where:
    't' indicates the tier in the range <1..128>, and
    'c' indicates the channel in the range <ABCDEFGHPS>.

DIAG[=tc]
    Performs a series of diagnostics tests on the specified disk.
    The disk is specified by its physical tier and channel locations,
    'tc', where:
    't' indicates the tier in the range <1..128>, and
    'c' indicates the channel in the range <ABCDEFGHPS>.

FAIL[=tc]
    This parameter tells the system to fail the specified disk at the
    physical tier and channel locations indicated by 'tc', where:
    't' indicates the tier in the range <1..128>, and
    'c' indicates the channel in the range <ABCDEFGHPS>.
    When a non-SPARE disk is specified:
    If failing the disk won't cause a multi-channel failure, the disk
    is marked as failed, and an attempt is made to replace it with a
    spare disk.
    When a SPARE disk is specified:
    If the spare disk is currently in use as a replacement for a
    failed disk, then the disk that the spare is replacing is put back to
    a failed status, and the spare is released, but it is marked as
    unhealthy and unavailable.

FAST_FAIL=[ON|OFF]
    This parameter turns on/off the fast fail mode for disks that are
    slow to respond to data access commands. The fast fail parameters can
    be customized to a particular need. Default is OFF.

FAST_FAIL_THRESHOLD='num cmds'
    This parameter indicates how many consecutive commands in the fast
    fail algorithm must occur before failing the drive for this reason.
    The default value is 5.
    Valid range = 2 - 20.

FAST_FAIL_WINDOW_END='t'
    This parameter indicates the timeout in seconds for when a disk
    response is received outside of a window in the future. If the
    command finishes outside of this time value, it is not aggregated in
    the slow disk algorithm as it is considered a separate instance of
    the event and the counter will restart. The default value is 90
    seconds.
    Valid range = 3 - 180.

FAST_FAIL_WINDOW_START='t'
    This parameter indicates the timeout in seconds for when a disk
    response is considered slow and will count against the drive in the
    slow disk fail algorithm. The default value is 5 seconds.
    Valid range = 2 - 179.

INFO[=tc]
    This parameter displays the information and status about a specific
    disk in the system.
    The disk is specified by its physical tier and channel locations,
    'tc', where:
    't' indicates the tier in the range <1..128>, and
    'c' indicates the channel in the range <ABCDEFGHPS>.

LIST[=SAS_ID|SPEED]
    This parameter displays a list of all the disks installed in the
    system and indicates how many were found of each type.
    The optional SAS_ID parameter will display the SAS ID of the device
    instead of the serial number.
    The optional SPEED parameter will display the link speed of the
    device instead of the RPM.

LLFORMAT[=tc]
    Allows the user to perform a low level format of a disk drive.
    The disk is specified by its tier and channel locations, 'tc', where:
    't' indicates the tier in the range <1..128>, and
    'c' indicates the channel in the range <ABCDEFGHPS>.

MAXCMDS=x
    Sets the maximum command queue depth to a tier of disks.
    Range: 1 to 32 commands per tier.
    Default: 16 commands.
    Setting should be as follows:
    - 16 if any SATA drives are used.
    - 32 for everything else.

MAXREADLEN=x
    Sets the maximum read command length for SATA drives in KiB.
    This parameter is used to increase throughput on systems with a large
    number of SATA tiers by reducing the contention for the SAS lanes.
    128K is the recommended setting for systems with 16 tiers or more of
    SATA disks.
    2048K is the recommended setting for systems with SAS disks.
    Range is 128 to 2048.
    Default is 128.

MAXWRITELEN=x
    Sets the maximum write command length to the drives in KiB.
    This parameter is provided for testing only and should normally not
    be changed.
    Range is 128 to 2048.
    Default is 2048.

PLS[=[t][c]]
    Requests/displays the PHY Link Error Status Block information for the
    specified drive.  Note that SATA and SAS drives report PHY errors
    differently. The PHY information consists of the following items:

    ======= =====================================================================
    ERROR   SATA AAMUX PHY ERRORS Explanation
    ======= =====================================================================
    H-RX    Number of SATA FIS CRC errors received on the host port of the AAMUX

    H-TX    Number of SATA R_ERR primitives received on the host port indicating
	    a problem with the transmitter of the AAMUX

    H-Link  Number of times the PHY has lost link on the host port

    H-Disp  Number of frame errors for the host port of the AAMUX.
	    These include:
	    code error,
	    disparity error,
	    or realignment

    O-RX    Number of SATA FIS CRC errors received on the other host port of
	    the AAMUX

    O-TX    Number of SATA R_ERR primitives received on the other host port
	    indicating a problem with the transmitter if the AAMUX

    O-Link  Number of times the PHY has lost link on the other host port

    O-Disp  Number of frame errors for the other host port of the AAMUX.
	    These include:
	    code error,
	    disparity error,
	    or realignment

    D-RX    Number of SATA FIS CRC errors received on the device port of the
	    AAMUX

    D-TX    Number of SATA R_ERR primitives received on the device port
	    indicating a problem with the transmitter of the AAMUX

    D-Link  Number of times the PHY has lost link on the device port

    D-Disp  Number of frame errors for the device port of the AAMUX.
	    These include:
	    code error,
	    disparity error,
	    or realignment
    ======= =====================================================================

    ======= =====================================================================
    Error   SAS PHY ERRORS Explanation
    ======= =====================================================================
    InvDW   Invalid DWORD Count - The number of invalid dwords received outside
	    of the PHY reset sequence.

    RunDis  Running disparity Count - The number of dwords containing running
	    disparity errors received outside of the PHY reset sequence.

    LDWSYN  Loss of DWORD synchronization count - The number of times the PHY
	    has lost synchronization and the link reset sequence.

    PHYRES  PHY Reset Problem count - The number of times the PHY reset sequence
	    has failed.
    ======= =====================================================================

    The disk is specified by its physical tier and channel locations,
    'tc',where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

    If neither the tier nor the channel are specified, the PLS
    information is requested from all drives.
    If only the tier is specified, the PLS information is requested from
    all the drives on the specified tier.

PMBIT=ON|OFF
    When ON this parameter sets the PM (performance mode) bit in Seagate
    SAS drives mode pages. When OFF the Seagate drive uses its default
    performance mode settings.
    Default is OFF.

QUARANTINE
    Displays the of number quarantine events on this controller for each
    disk in the system. Only tiers with quarantine counts will be
    displayed.
    Use QUARANTINECLEAR to reset the quarantine counts.

QUARANTINE=[ON|OFF]
    Enables/disables the disk quarantine feature for all of the disks. A
    disk cannot be quarantined unless FASTAV is enabled for the LUN.
    Default is OFF.

QUARANTINECLEAR
    Resets the quarantine counts for all of the disks.

QUARANTINECMDLIMIT=x
    Sets the maximum number of outstanding disk commands after a good
    response before a quarantined disk can be put back into service.
    Range 0 to 32 where 0 indicates no delay before putting the disk back
    into service.
    Default is 0.

QUARANTINETIMEOUT=x
    Sets the minimum timeout before a disk can be quarantined in 16.6
    millisecond increments. A disk cannot be quarantined unless FASTAV is
    enabled and has timed out on the command.
    Range 6 to 65535.
    Default is 12 (200 milliseconds)

REASSIGN[=tc] [0xh
    Allows for the reassigning of defective logical blocks on a disk to
    an area of the disk reserved for this purpose.
    The disk is specified by its tier and channel locations, 'tc', where:
    't' indicates the tier in the range <1..128>, and
    'c' indicates the channel in the range <ABCDEFGHPS>.
    0xh is the hexadecimal value of the LBA (Logical Block Address) to be
    reassigned.

REBUILD[=tc]|ALL
    This parameter tells the system to start a rebuild operation on a
    (presumably) already failed disk.  A rebuild operation restores a
    failed disk to a healthy status once it completes.  Note that this
    operation can take several hours to complete depending on the size of
    the disk and the speed of the rebuild operation.  The speed of the
    rebuild operation can be adjusted with the DELAY and EXTENT
    parameters of the TIER command.
    In addition, the rebuild operation can be stopped, or paused and
    resumed with the TIER STOP, TIER PAUSE, and TIER RESUME commands.
    The TIER AUTOREBUILD command can be used to automate the rebuild
    process.
    Note that SPARE disks are handled slightly differently from other
    disks, in that SPARES that are not in use as an active replacement
    for a failed disk elsewhere in the system are simply returned to a
    normal healthy status by this command; SPAREs that are in use are
    already considered healthy and are not rebuilt.
    The failed disk to be rebuilt is specified by its physical tier and
    channel locations, 'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

    All failed and replaced disks can be rebuilt using the ALL parameter.

REBUILDNOJOURNAL[=tc]|ALL
    This parameter tells the system to start a rebuild operation on a
    (presumably) already failed disk without using the journal.  A
    rebuild operation restores a failed disk to a healthy status once it
    completes.  Note that this operation can take several hours to
    complete depending on the size of the disk and the speed of the
    rebuild operation.  The speed of the rebuild operation can be
    adjusted with the DELAY and EXTENT parameters of the TIER command.
    In addition, the rebuild operation can be stopped, or paused and
    resumed with the TIER STOP, TIER PAUSE, and TIER RESUME commands.
    The TIER AUTOREBUILD command can be used to automate the rebuild
    process.
    Note that SPARE disks are handled slightly differently from other
    disks, in that SPARES that are not in use as an active replacement
    for a failed disk elsewhere in the system are simply returned to a
    normal healthy status by this command; SPAREs that are in use are
    already considered healthy and are not rebuilt.
    The failed disk to be rebuilt is specified by its physical tier and
    channel locations, 'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

    All failed and replaced disks can be rebuilt using the ALL parameter.

REBUILDVERIFY=ON|OFF
    This parameter determines if the system will send SCSI Write with
    Verify commands to the disks when rebuilding failed disks.  This
    feature is used to guarantee that the data on the disks is rebuilt
    correctly.
    Note: This feature will increase the time it takes for rebuilds to
    finish.

    Default is OFF.

REPLACE[=tc]
    This parameter tells the system to replace the specified failed disk
    with a spare disk or replace a healthy disk that is believed to be on
    the verge of failing.  The healthy disk replacement is referred to in
    the system as a proactive replacement operation. A replace operation
    is used to temporarily replace a disk with a healthy spare disk.
    This operation can take several hours to complete depending on the
    size of the disk and speed of the replace operation.  The speed of
    the replace operation can be adjusted with the DELAY and EXTENT
    parameters of the TIER command.
    The disk to be replaced is specified by its physical tier and channel
    locations, 'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHP>.

    (Note that spare disks themselves cannot be replaced with this
    command).

RESTART[=tc]
    This parameter tells the system to start a restart operation on a
    (presumably) already failed disk.The failed disk to be restarted is
    specified by its physical tier and channel locations, 'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

    All failed and replaced disks can be restart using the ALL parameter.

SCAN
    This parameter checks each disk channel in the system for any new
    disks and verifies that the existing disks are in the correct
    location.  It also starts a rebuild operation on any failed disks
    which pass the disk diagnostics.

STATUS
    Displays the loop status of each disk channel and a count of the
    fibre channel errors encountered on each channel.

STATUSCLEAR
    Resets the fibre channel error counts on each disk channel.

TIMEOUT=x
    This parameter sets the total disk timeout (in seconds) for an I/O
    request.  The total disk timeout value indicates the total overall
    length of time allotted to each I/O request to complete; if an I/O
    request has not completed within this time frame, then an error
    status is reported for it.
    This parameter must be greater than or equal to CMD_TIMEOUT.
    Valid range is 1 to 512 seconds.

    * Recommended value for SAS drives is 27 seconds.
    * Recommended value for SATA drives is 60 seconds.

    Default is 60 seconds.

WRITESAME=ON|OFF
    Enable and disables use of the SCSI Write Same command when
    formatting LUNs. The SCSI Write Same command is used by the system to
    format a LUNs faster. This parameter is provided for backwards
    compatibility with disks or enclosures that do not support the SCSI
    Write Command.

    Default is OFF.
