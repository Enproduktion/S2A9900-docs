=====
 LUN
=====


LUN  Displays the status of, or Adds/Removes LUNs.
This command is used to change the configuration settings for the LUNs
in the system and to monitor their status.  This command allows the user
to create LUNs with the ADD parameter and delete LUNs with the DEL
parameter.  The FORMAT parameter can be used to format LUNs after they
are created.  A LUN must be formatted before it can be used.  The ADD
parameter will prompt the user to format a LUN after it has been added
to the system.  The speed of the LUN format operations can be adjusted
with the DELAY and EXTENT parameters of the TIER command.

ADD[=x]
    This parameter will add a 64-bit LUN to the system.  The system will
    prompt the user for all the necessary information to create the LUN
    and will indicate if the LUN was successfully added to the system.
    The system can support up to 1024 LUNs.
    The LUN to be added can be specified by 'x', where 'x' is in the
    range 0..1023.

ADD32[=x]
    This parameter will add a 32-bit LUN to the system.  The system will
    prompt the user for all the necessary information to create the LUN
    and will indicate if the LUN was successfully added to the system.
    The system can support up to 1024 LUNs.
    The maximum capacity of a 32-bit LUN is limited to 0xFFFF0000 host
    blocks.

    ========== ==================
    Block size Maximum Capacity
    ========== ==================
    512         2.097.120 MiB
    1024        4.194.240 MiB
    2048        8.388.480 MiB
    4096       16.776.960 MiB
    ========== ==================

    The LUN to be added can be specified by 'x', where 'x' is in the
    range 0..1023.

ADD64[=x]
    This parameter will add a 64-bit LUN to the system.  The system will
    prompt the user for all the necessary information to create the LUN
    and will indicate if the LUN was successfully added to the system.
    The system can support up to 1024 LUNs.

    The LUN to be added can be specified by 'x', where 'x' is in the
    range 0..1023.

APTPL
    This parameter allows the user to enable SCSI 3 persistant
    reservations support for AIX Host on a specific LUN

APTPL=ALL
    This parameter allows the user to enable SCSI 3 persistant
    reservations support for AIX Host on all valid LUNs

CONFIG
    Display the configuration information about all the valid LUNs in the
    system.

DELAY=x
    This parameter sets the system verify delay value to 'x'.  The verify
    delay value determines how long a verify operation will pause after
    it reaches the verify extent.  This parameter slows down the verify
    operation so that it will not affect the performance of the system.
    This value is in 100 millisecond increments.
    The range for 'x' is 0 to 1000.

DEL|DELETE[=x]
    This parameter will delete a LUN, 'x', from the system.  It will
    delete all of the data in the LUN.
    The LUN to be deleted can be specified by 'x', where 'x' is in the
    range 0..1023.

EXTENT=x
    This parameter sets the system verify extent value, 'x', in MiB.  The
    verify extent determines how much data can be verified before the
    verify operation must pause.  This parameter slows down the verify
    operation so that it will not affect the performance of the system.
    Increasing the extent value will allow more data to be verified in a
    single pass.
    The range for 'x' is 1 to 128 MiB.

FORMAT[=x]
    This parameter will perform a destructive initialization of a LUN by
    over-writing all the data on the LUN with zeroes.
    The LUN to be formatted can be specified by 'x', where 'x' is in the
    range 0..1023.

LABEL[=x]
    This parameter allows the user to change the label of the LUN.  A LUN
    label can be up to 16 characters long.
    The LUN to be labeled can be specified by 'x', where 'x' is in the
    range 0..1023.

LIST
    Display a list of all valid LUNs in the system.  The list shows the
    capacity, owner, status and serial number of each LUN.

    The following is a list of possible statuses and their definitions:

    * 'Not Installed'    - The LUN does not exist.
    * 'Config Error'     - The LUN has a configuration error.
    * 'Unavailable'      - Cache data for the LUN is being purged. This is
      done when the LUN is being deleted or mirrored by the other
      unit in the system.
    * 'Not Ready'        - The unit is still booting up.
    * 'Stopped'          - The unit was stopped.
    * 'Unformatted'      - The LUN has not been formatted.
    * 'Critical'         - The LUN has a failed disk.
    * 'Critical [GHS]'   - The LUN has a failed disk and a disk that
      is replaced by a spare.
    * 'Degraded'         - The LUN has a failed disk (8+2 Only).
    * 'Degraded [GHS]'   - The LUN has a failed disk and a disk that is
      replaced by a spare (8+2 Only).
    * 'Ready [GHS]'      - The LUN has a replaced disk.
    * 'Ready'            - The LUN is OK.

[LOCK[=x]]
    This parameter will lock a LUN in the data cache.  It will keep all
    of the data for the LUN in the cache for faster access.  Up to 50
    percent of the data cache can be used for locking LUNs.
    The LUN to be locked can be specified by 'x', where 'x' is in the
    range 0..1023.

LOCKOUT_CLEAR=type
    This parameter is is used to clear a lockout code on the prompted LUN
    so that admin can clear an event from a particular lun. Clearing this
    field will remove the lockout state from the LUN regardless of the
    enabled setting at the system level.

    * 'ALL' - Disables system from locking out LUNs from all reasons below
    * 'BBM' - Disables system from lockint out LUNs when BBM is enabled and
      crosses a shutdown threshold or becomes full.
    * 'UNIT_PROBLEM - Disables system from locking out LUNs when it is
      determined that the problem could cause potential data loss.

LOCKOUT_DISABLE=type
    This parameter specifies whether or not the system can determine when
    a LUN should NOT be locked out from new host accesses.  Regardless of
    what state the system determines, we cannot lockout host access at
    run time due to the lockout type.

    * 'ALL' - Disables system from locking out LUNs from all reasons below
    * 'BBM' - Disables system from locking out LUNs when BBM is enabled and
      crosses a shutdown threshold or becomes full.
    * 'UNIT_PROBLEM - Disables system from locking out LUNs when it is
      determined that the problem could cause potential data loss.

LOCKOUT_ENABLE=type
    This parameter specifies whether or not the system can determine when
    a LUN should be locked out from new host accesses.  Examples of when
    a LUN will be locked out internally would be when the BBM is enabled
    and becomes full.  Another example would be when a multi-channel
    failure exists on the LUN.  The default setting of the parameter is
    0, indicating no internal reasons can cause a lun to be locked out
    from a host.

    * 'ALL' - Allows system to restrict LUNs from all reasons below
    * 'BBM' - Allows system to restrict LUNs when BBM is enabled and
      crosses a shutdown threshold or becomes full.
    * 'UNIT_PROBLEM - Allows system to restrict LUNs when it is determined
      that the problem could cause potential data loss.

MOVE[=x]
    This parameter will change the ownership of a LUN from one unit to
    the other when the units are in dual mode.  This command will
    override all the configuration checks and allow the user to move any
    LUN.  The system will display a list of all the tiers and other LUNs
    that need to be moved in order to move the LUN specified.
    The LUNs should not be moved while any unit in the system has active
    format, verify, rebuild or mirror operations.
    The LUN to be moved can be specified by 'x', where 'x' is in the
    range 0..1023.

PAUSE[=x]
    This parameter will pause all active LUN maintenance operations
    including format, verify and mirror operations.
    A single LUN can be specified 'x', where 'x' is in the range 0..1023.

RELEASE[=x][=ALL]
    This parameter allows the user to release all SCSI reservations and
    registrations on the LUN.  The command LUN RESERVATIONS can be used
    to view the current SCSI reservations and registrations on the LUNs.
    All LUNs can be specified by RELEASE=ALL or a singe LUN can be
    specified by 'x', where 'x' is in the range 0..1023.

RESERVATIONS[=x]
    This command displays the current SCSI reservations and registrations
    on the LUNs in the system. The system supports the following types of
    SCSI reservations:

    * SPC-2 - Compatible with SPC-2
    * Wr_Ex - Write Exclusive
    * Excl  - Exclusive access
    * Wr_RO - Write exclusive registrants only
    * Ex_RO - Exclusive access registrants only
    * REG   - Indicates a SCSI registration on the LUN.

    The 'Port' column indicates the unit and host port the reservation or
    registration was made on.
    A specific LUN can be viewed by 'x', where 'x' is in the range
    0..1023.

RESUME[=x]
    This parameter will release all the paused LUN maintenance operations
    including format, verify and mirror operations.
    A single LUN can be specified 'x', where 'x' is in the range 0..1023.

START
    This parameter allows the user to start all the LUNs that have been
    stopped by a SCSI START/STOP request.
    This parameter is not related to the STOP parameter.

STOP[=x]
    This parameter will abort all active LUN maintenance operations
    including format, verify and mirror operations.
    A single LUN can be specified 'x', where 'x' is in the range 0..1023.
    Note that it does not, however, change the Background Verify setting
    for the affected LUN(s).  Use 'LUN VERIFY=OFF' to change the
    Background Verify setting for a LUN.

UNASSIGN_LIST
    This parameter allows the user to view the system LUNs that have not
    been assigned to a user or port.

UNLOCK[=x]
    This parameter will unlock a LUN and release the cache locked by the
    LUN.
    The LUN to be unlocked can be specified by 'x', where 'x' is in the
    range 0..1023.

VERIFY
    Displays the current background verify settings for all LUNs in the
    system.

VERIFY=ON|OFF
    Prompts the user for a list of LUNs on which background verify will
    be turned either ON or OFF.
    The 'VERIFY=ON' argument will turn on background verify for the
    specified LUN(s), optionally running in continuous mode. A
    'VERIFY=OFF' command, however, only turns off the Background Verify
    setting for the specified LUN(s).  Therefore, any verifies already
    active on the LUN(s) will not terminate until after the completion of
    that verify's current iteration.  To stop all Verify operations
    immediately, use 'LUN STOP'.

VERIFY=x
    Turns ON background verify for LUN 'x', where 'x' is in the range
    0..1023.

VERIFYCLEAR[=x|ALL]
    This parameter allows the user to clear the verify count and the time
    of last verify for a specific LUN designated by 'x' or all LUNs.
