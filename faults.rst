========
 FAULTS
========

FAULTS  Displays all current faults, warnings and errors.

This command will display a list of all current faults, warnings and
errors in the system.  This provides a convenient way to quickly check
the status of the system.

ARRAYPARITY
    Displays the number of LUN array parity errors detected by the
    system. The system saves the counts for each tier of all the LUNs.

ARRAYPARITYCLEAR
    Clears the counts of LUN array parity errors in the system.

BUSPARITY[=ALL]
    Displays the number of bus parity and data path errors detected by
    the system.
    =ALL Parameter shows the 7 day history for the bus parity errors.

BUSPARITYCLEAR
    Clears the counts of bus parity and data path errors in the system.

DISKECC
    Displays the number of ECC errors detected on the disk boards.

DISKECCCLEAR
    Clears the counts of ECC errors detected on the disk boards.

ECCSHUTDOWN=ON|OFF
    Enables or Disables the Shutdown for Unrecoverable ECC Errors.
    If set to ON indicates the system will shutdown for unrecoverable ECC
    errors.  If set to OFF indicates the system will not shutdown when
    receiving unrecoverable ECC errors.

    Default is ON.

EXCEPTIONSHUTDOWN=ON|OFF
    Enables or Disables the Shutdown for Task Exceptions.
    If set to ON indicates the system will shutdown for task exceptions.
    If set to OFF indicates the system will not shutdown on task
    exceptions.

    Default is ON.

MEMCLEAR
    Clears the values in the memory faults (ECC) statistics.

MEMORY
    Displays the current SDRAM memory faults (ECC).  Error counters will
    not be displayed if there are no errors.

RECOVERYCLEAR
    Clears the latched disk recovery fault code.

RESTARTCOUNT
    Display the number of I/O processor restarts that occured due to
    error
    conditions on the I/O processors.

RESTARTCOUNTCLEAR
    Clears the I/O processor restart counters.

SFP
    Displays the current status of the host and disk SFPs.

    .. note::

       A transmitter fault and a loss of signal on a disk channel or
       host port may indicate that there is no connection at the
       corresponding connector.
