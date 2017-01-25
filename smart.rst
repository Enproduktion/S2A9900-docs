=======
 SMART
=======

SMART  Control and Display SMART facilities on the disk.

This command is used to configure and display SMART facilities on the
disk. It can be used to enable and disable SMART, retrieve SMART data
from the disks and display to the user, start self tests on the disks
and retrieve test results and display to the user. It can also be used
to display the vendor specific SMART data on any specified disk.

ABORTSELFTEST=ALL
    Request to abort BACKGROUND SELF TESTS on all disks.
    This command only works for SAS Disks.

ABORTSELFTEST=tc
    Request to abort BACKGROUND SELF TESTS on the specified disk.
    This command only works for SAS Disks.
    The disk is specified by its physical tier and channel locations,
    'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

CLEAR=ALL
    Clears all SMART trips on all drives.

CLEAR=tc
    Clears SMART trips on specified drives.
    The disk is specified by its physical tier and channel locations,
    'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

DATA=tc
    Displays all the SMART information for the specified disk.
    The disk is specified by its physical tier and channel locations,
    'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

DISABLE
    Disables SMART for all the disks.

ENABLE
    Enables SMART for all the disks.

INTERVALTIME
    Displays the interval (in hours) that SMART Information will be
    polled for.

INTERVALTIME=h
    Sets the interval (in hours) that SMART Information polling will
    occur.
    'h' indicates the interval in hours in the range <1..24>.

LOG=ALL
    Displays the SELF TEST LOG stored on all installed disks.
    This command only works for SAS Disks.

LOG=tc
    Displays the SELF TEST LOG stored on the specified disk.
    This command only works for SAS Disks.
    The disk is specified by its physical tier and channel locations,
    'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

SELFTEST=ALL [testtype]
    Request to start a specified SELF TEST on all installed SAS disks.
    This command only works for SAS Disks.
    The type of test is specified as one of the following.

    * 0 : DEFAULT SELF TEST
    * 1 : BACKGROUND SHORT SELF TEST
    * 2 : BACKGROUND EXTENDED SELF TEST

SELFTEST=tc [testtype]
    Request to start a specified SELF TEST on the specified disk.
    This command only works for SAS Disks.
    The disk is specified by its physical tier and channel locations,
    'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

    The type of test is specified as one of the following.

    * 0 : DEFAULT SELF TEST
    * 1 : BACKGROUND SHORT SELF TEST
    * 2 : BACKGROUND EXTENDED SELF TEST

STATUS=tc
    Displays SMART ENABLE STATUS of the specified disk.
    Displays if the information exception is enabled and if
    Temperature warning is enabled or not.
    The disk is specified by its physical tier and channel locations,
    'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

TEST=OFF
    Disables the TEST Bit in the Information Exception Mode Page for
    all disks. TEST Bit disabled will stop simulating a SMART trip
    condition.

    .. note::

       This command currently works only with SAS Disks.

TEST=ON
    Enables the TEST Bit in the Information Exception Mode Page for all
    disks. TEST Bit set will simulate a SMART trip condition and a FALSE
    ALARM is raised.

    .. note::

       This command currently works only with SAS Disks.

UPDATE
    This parameter tells the system to recheck all of the mode parameters
    for the disks in the system.  This allows the user to update the disk
    mode parameters after changing the SMART capability instead of
    changing them one at a time.
