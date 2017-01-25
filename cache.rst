=======
 CACHE
=======

CACHE  Displays and adjusts the cache settings of the LUNs.

This command is used to change the performance of the system by
adjusting the cache settings for the LUNs.  This command will display
the current cache settings for each :doc:`lun` in the system and allow the user
to modify them.  These cache parameters are identical to the cache
parameters in the SCSI caching mode page.

DEFAULTS
    This parameter will load the default settings for all of the cache
    parameters for the specified LUNs.  This parameter will not change
    the WRITELIMIT or SIZE parameters.
    Note that when this parameter is used in combination with any of the
    following other parameters:
    WRITEBACK,
    PREFETCH,
    MAX,
    MF,
    that DEFAULTS is applied first to the specified LUNs, and these other
    parameters are applied after.

HOSTCHANGEABLE=ON|OFF
    This parameter enables and disables host changes to the SCSI cache
    mode page. When enabled (ON), the hosts are allowed to change the
    writeback cache setting through the SCSI cache mode page. When
    disabled (OFF), the host changes to the SCSI cache mode page will
    have no effect on the cache settings for the LUN. Default is ON.

LUN=x
    This parameter specifies the specific LUN(s) to be affected when used
    in combination with any of the following other parameters:
    DEFAULTS,
    MAX,
    MF,
    PREFETCH,
    WRITEBACK,
    If no LUN is specified then all LUNs will be updated by default.
    Valid LUN values, 'x', are 0 to 127.
    Default is ALL LUNs.

MAX=x
    This parameter sets the maximum prefetch ceiling, 'x', in blocks, for
    prefetches on read commands.  This parameter is used to set an upper
    limit on prefetching when the MF parameter is ON.  The system will
    automatically limit the amount of prefetching if the system is
    running low on resources.
    Valid range is 0 to 65535.
    Default is 65535.

MF=ON|OFF
    This parameter enables and disables the Multiplication Factor bit.
    If MF is OFF, the system will prefetch the number of blocks specified
    by the PREFETCH parameter after every read command.  If MF is ON,
    then the system will multiply the transfer length of the command by
    the PREFETCH parameter to determine how much data will be prefetched.
    Default is ON.

PREFETCH=x
    This parameter sets the prefetch that will occur on read commands.
    If the MF parameter is OFF, the system will prefetch the number of
    blocks specified by this parameter after every read command.  If the
    MF parameter is ON, then the system will multiply the transfer length
    of the command by this parameter to determine how much data will be
    prefetched.  A prefetch value of less than 8 is recommended when the
    MF parameter is ON.
    Valid range is 0 to 65535.
    Default is 1.

SIZE=x
    This parameter sets the cache segment size, 'x', in KiB, for the
    system.  This allows the user to adjust the performance of the system
    by changing the cache segment size to match the size of the host I/O
    requests.  A large cache segment size may give better performance for
    large I/O requests and a small cache segment size may give better
    performance for small I/O requests.  For the best performance, the
    cache segment size should be larger than the average host I/O request
    size.  Use the STATS LENGTH command to determine the average host I/O
    request size.  This command should not be used under heavy I/O
    conditions because the system will temporarily halt all I/O requests
    while the changes are taking effect.
    Warning: This operation will cause a cache restart to occur that will
    temporarily halt all IO activity until it completes.
    Valid segment sizes are 128, 256, 512, 1024, and 2048.
    Default is 1024.

WRITEBACK=ON|OFF
    This parameter enables and disables write back caching.  Write back
    caching allows the system to increase the performance of write I/O
    requests by storing the data in cache and saving the data to the
    disks at a later time.
    Default is OFF.

WRITELIMIT=x
    This parameter specifies the maximum percentage of the cache that can
    be used for write back caching. The system will force all writeback
    requests to be flushed to the disks immediately if the percentage of
    writeback data in the cache exceeds this value.
    Range is 0 to 100.
    Default is 75.
