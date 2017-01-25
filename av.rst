====
 AV
====

AV  Displays information about the Audio/Visual settings.

This command is used to change the Audio/Visual configuration settings
for the system. These parameters are used to tune the system and the
disks for better performance and a lower latency. The writeback and
prefetch settings for each :doc:`lun` are changed with the :doc:`cache` command.

FAILCC=ON|OFF
    This parameter will tell the host ports to report a check condition
    for all SCSI commands when the unit is in a failed state.  This
    command should only be used in AV environments when a check condition
    is required instead of taking the unit off the loop.
    Default is OFF.

FASTAV=ON|OFF
    This parameter enables and disables the disk fast Audio/Video read
    option for streaming data.  If the FASTAV parameter is ON, the system
    will start the data transfer for read operations before all of the
    disk commands have finished.  This feature reduces the latency for
    read operations but the system will be unable to check the integrity
    of the data.  The FASTAVTIMEOUT parameter indicates how long the host
    command must wait before the FASTAV mechanism will activate.
    Note: This parameter is saved on a per-LUN basis.  Use in combination
    with the LUN=x parameter to change the settings for a single LUN.
    Default is OFF.

FASTAVTIMEOUT=x
    This parameter sets the timeout before the FASTAV option will
    activate on a host read command.  The FASTAV mechanism will not be
    used until the host command takes longer than the timeout value.  A
    value of zero indicates that the system will start the data transfer
    as soon as a minimum number of drives are ready.
    This value is in 100 millisecond increments.
    The range for 'x' is 0 to 600.
    The default is 200.

LUN=x
    This parameter may be used in combination with the FAST_AV and RC
    parameters, in order to specify which LUN is to be changed.  By
    default, if no LUN is specified with this parameter, then all the
    LUNs in the system will be updated .
    Valid LUNs are 0 to 127.
    Default is all LUNs.

ORDEREDQUEUE=x
    Enables the use of ordered tags when communicating with the drives.
    The value 'x', indicates the number of disk commands that can be sent
    before an ordered tag must be sent to the disks:
    0 indicates no ordered tags,
    1 indicates every command has an ordered tag,
    2 indicates every second command has an ordered tag,
    3 indicates every third command has an ordered tag,
    4 indicates every fourth command has an ordered tag,
    etc...
    Valid range is 0 to 255.
    Default is 0.

RC=ON|OFF
    This parameter enables and disables the Read Continuous option for
    Audio/Video streaming data.  If the RC parameter is ON, the system
    will start the data transfer for read operations after RCTIMEOUT is
    reached even if the disks commands have not finished.  This feature
    is used to reduce the latency for read operations in Audio/Visual
    environments where latency is more important than data integrity.
    WARNING: This feature allows the system to return invalid data to the
    initiator.
    Note: This parameter is saved on a per-LUN basis.  Use in combination
    with the LUN=x parameter to change the settings for a single LUN.
    Enabling this feature will automatically enable FASTAV.
    Default is OFF.

RCTIMEOUT=x
    This parameter sets the host command timeout for the Read Continuous
    option for Audio/Video streaming data.  A timeout value of zero will
    disable the Read Continuous feature in the system.
    This value is in 100 millisecond increments.
    The range for 'x' is 0 to 255.
    The default is 250.

UA=ON|OFF
    This parameter enables and disables the initial Unit Attention
    condition when an initiator logs into the system.  If the UA
    parameter is ON, the system will report a Unit Attention condition on
    the first SCSI command after the initiator logs in.  If the UA
    parameter is OFF, the system will automatically clear the unit
    attention condition when an initiator logs in. Default is ON.
