=======
 STATS
=======

STATS  Displays the system performance statistics.

This command will display the performance statistics for the host ports,
disk channels, and the cache memory.  The command will show the read and
write performance of each of the host ports.  Read hits shows the
percentage of read I/O requests where the data was already in the cache.
Prefetch hits shows the percentage of read I/O requests where the data
was already in the cache because of prefetching.  Prefetches shows the
percentage of host read I/O requests to the disks which are due to
prefetching.  The bottom of the screen shows the read and write
performance of the disks.  Disk pieces shows the total number of disk
I/O requests from the host ports.  BDB pieces is the number of host I/O
blocking deblocking requests.  Cache writeback data shows the percentage
of the cache which contains writeback data which must be written to the
disks.  Cache rebuild data shows the percentage of the cache in use for
rebuild operations, and Cache data locked shows the percentage of the
cache which is locked by the locked LUNs.

CLEAR
    This parameter resets all the statistics back to zero.

DELAY
    This parameter displays a histogram of the time it takes for the host
    and disk I/O requests to complete. The disk queue delay includes the
    time the disk commands were queued up waiting to be sent to the
    disks.

DISKPIECES
    This parameter displays a histogram of the number of transfer pieces
    per disk command by disk command type.  The system will combine
    several host I/O requests into a single disk I/O request.  This
    histogram shows how often this is occurring.

DISK|DISK=[t|c|tc] [CLEAR
    This parameter displays a histogram of which disks in the system have
    taken an unusually long time to complete an I/O request.  The count
    is incremented for a disk if the disk took longer than the other
    disks to finish an I/O request.  This command is used to determine if
    a disk in the array is slowing down the system performance.  Normally
    all the disks in a tier should have similar counts.  A disk with a
    significantly higher count indicates that the disk may be slower or
    it may have problems.
    Optionally a specific tier ('t'), channel ('c') or drive ('tc') can
    be used to narrow the scope.
    The optional CLEAR can be used to clear (instead of displaying) these
    statistics on a drive, channel, tier or whole system basis.

DUAL
    This parameter displays the statistics for the dual mode messages.

HOSTDELAY
    This parameter displays a histogram of the time delay between when a
    data transfer is set ready and the host interface completes the
    transfer.

INTERVAL=x
    This parameter determines how many seconds the system will wait
    before displaying the repeating statistics information.  This
    parameter is not saved.
    The valid range for 'x' is 1 to 60 seconds.

    Default is 2 seconds.

LENGTH
    This parameter displays a histogram of the length of the host I/O
    requests in 16 KiB intervals.

OFFSET
    This parameter displays a histogram of the offset of the host I/O
    requests into the cache segments.  Host I/O requests with offsets
    that are not in the 0x0 column may require blocking/deblocking which
    can slow down the performance of the system.

REPEAT=MAIN|MBS|IOS|OFF
    Allows the user to enable/disable the repeating statistics display,
    where:

    * MAIN  - display the normal STATS display.
    * MBS   - displays MiB/s.
    * IOS   - displays IO/s.
    * OFF   - turns off the repeating displays.

SAMPLES=x
    This parameter allows the user to specify how many times the
    repeating statistics display should repeat before turning off.
    Setting this value to a non-zero value will automatically enable the
    repeating statistics.
    The valid range for 'x' is 0 to 65535 samples.
    Default is 0.

TIERDELAY|TIERDELAY=[t|c|tc] [CLEAR]
    This parameter displays a histogram of the time it takes for the disk
    I/O requests to complete for all the disks in the specified tier,
    't', or specified channel, 'c', or specified drive, 'tc''.  If
    nothing is specified, then all valid tiers will be displayed.

    The CLEAR option will allow for selective clearing of these
    statistics.The optional CLEAR will allow for selective clearing
    (instead of displaying) of these statistics.

TIERLENGTH|TIERLENGTH=n
    This parameter displays a histogram of the length of the disk I/O
    requests for each tier in 8 KiB intervals.
