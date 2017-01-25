==========
 SHUTDOWN
==========

SHUTDOWN  Performs a shutdown of the system.

This command will prepare the system to be shutdown. All hosts and users
actively using this system should be safely shutdown before using this
command.  The system will halt all I/O requests and save the data to the
disks.  The unit can be safely turned off after using this command. Once
shutdown is complete, either all power supplies must either first be
switched off, or else their plug should be pulled out of its socket.
Power must be removed from the system for at least 10 seconds before it
will start up again.

DELAY=x
    Performs a shutdown of the unit in 'x' minutes.
    'x' may be any number between 0 and 255.

DUAL
    Will shutdown both this unit and the other unit.

KILL
    Stops a timed shutdown that is in progress.

RESTART[=x]
    Performs a Hard Restart of the unit by cycling the power, where 'x'
    indicates the number of seconds before the unit powers up again.
    'x' may be any number between 1 and 127.
    If a time, 'x', is not specified, the default delay will be 15
    seconds.
    Note: you can not use both the DUAL and RESTART parameters together
    with this command.

SPINDOWN
    Spindown all non-PB SATA drives before performing a shutdown.
