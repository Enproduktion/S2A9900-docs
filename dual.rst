======
 DUAL
======

DUAL  Displays information about the dual system configuration.

Displays information about the dual system configuration.

COHERENCY=ON|OFF
    Enables/Disables the cache coherency between the two units.
    Warning: Enabeling cache coherency will cause a cache restart to
    occur that will temporarily halt all IO activity until it completes.

FAIL
    Fails the partner unit in the system.

HEAL
    Restores the partner unit in the system to a healthy status.
    Warning: This operation will cause a cache restart to occur that will
    temporarily halt all IO activity until it completes.

LABEL=x
    This parameter allows the user to change the label assigned to each
    unit.  This allows the user to uniquely identify each unit in the
    system.  The CLI prompt for each unit is built by adding a colon and
    a space at the end of the label.
    Each unit can have a label up to 31 characters long.
    Entering DEFAULT will restore the label of the unit to its default
    setting.

    Valid values for 'x' are 1 and 2.

SINGLET
    This parameter tells the system that it is in singlet mode and not in
    couplet mode and only unit 1 is installed.  This command will disable
    cache coherency, heal unit 1 if it is failed and fail unit 2 before
    attempting to remove it.  The system may automatically add unit 2 if
    it is connected to the system so unit 2 should be powered off and
    removed from the system after the command is finished.

TIMEOUT=x
    Sets the dual cache coherency timeout for cache node requests.  The
    timeout value is given in seconds.  A value of zero allows for only
    one retry.  It is recommended that this timeout value be smaller than
    the host timeout (HOST TIMEOUT=x).
    The valid range for 'x' is 0 to 255 seconds.

    Default is 0 seconds.
