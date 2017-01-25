=====
 IHD
=====

IHD  Displays and adjusts the IHD settings.

This command is used to format, display, and trigger IHD activities in
the system.

AUTO_BACKUP=[ON|OFF]
    This parameter enables and disables the automatic backups of the
    cache to occur is a power event is detected.

    Default is OFF.

BACKUP
    Cache will be backed up on the Internal Hard Drive. Host I/O will not
    be accepted after running this command.

FORMAT
    This parameter will format an internal hard drive to a default state
    for use in an S2A. This command will prompt for the hard drive and
    will look at the drive ownership state to determine if the format
    request can be processed at this time.

IHD_APP=[ON|OFF]
    This parameter enables and disables the IHD Application. A restart is
    required for the change to take an effect.

    Default is OFF.

RESTORE[=x]
    Cache will be restored from the Internal Hard Drive. Host I/O will be
    accepted after running this command. An optional parameter LUN can be
    provided to the call to ONLY restore and clear that LUN information
    from the IHD. Host I/O will be accepted after running this command.
    This command accepts the following :

    * No parameter means RESTORE ALL
    * =ALL parameter means RESTORE ALL
    * ='x' where x is a lun means RESTORE LUN x

RESTORE_REPORT[=x]
    The IHD will be scanned and provide a report of what is available on
    the IHD for data. An optional parameter LUN can be provided to the
    call to ONLY check for a single LUNs information from the IHD. Host
    I/O will be accepted after running this command.
