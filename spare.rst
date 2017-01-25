=======
 SPARE
=======

SPARE  Displays information about the spares in the system.

This command is used to change the configuration settings for the spare
background diagnostics in the system.  The command will display the
current spare configuration settings as well as task status.  The INFO
parameter can be used to display all of the information about a specific
spare in the system.  The default output will provide a snapshot of the
current test status of all spares, any tests in progress, and the status
of the spare task.
Spare diagnostics are automatically disabled when the unit is in a
failed state.  When the diagnostics are started, a search algorithm is
run to select a disk for testing.  Disks will be selected with the
following restrictions:

1. the disk must pass diagnostics, ie. cli command disk diag
2. the disk has not been tested within the present calendar month

If no disks are found for testing within the search algorithm, the test
software will sleep for 24 hours before searching for disks to test
again. If the user wants to force a new search algorithm to run, the
spare start command can be executed and that will awaken the test
software immediately.

CLEAN[=tc]
    This parameter will erase any previous test data stored on the disk.
    The disk is specified by its physical tier and channel locations,
    'tc', where:

    * 't' indicates the tier in the range <1..128>, and
    * 'c' indicates the channel in the range <ABCDEFGHPS>.

COVERAGE=x
    This parameter sets the spare diagnostic coverage of the blocks being
    tested as a percent of the total number of blocks available for test.
    Note that increasing the coverage to higher numbers means that more
    blocks on the disk will be tested for better coverage but it also
    will take a longer time for the test to complete.  This parameter can
    be tuned to provide an optimal test time for a single disk in the
    system such that all spares are tested in a reasonable amount of
    time.  The parameter is limited to a discrete set of values.
    The valid parameters for 'x' are [1, 5, 10, 20, 40, 80, 100] Percent.

    Default is 1 Percent.

DELAY=x
    This parameter sets the system spare diagnostics delay.  The test
    delay determines how long a test operation will pause after it
    reaches the test EXTENT.  This parameter slows down the spare test so
    it will not affect the performance of the system.  Any changes
    applied to delay will affect tests in progress as well as future
    testing.
    This system spare diagnostic delay value is given in 100 millisecond
    increments.
    The valid range for 'x' is 0..10 which translates into a time delay
    of 0..1 seconds in 100 millisecond increments.

    The default is 0.

EXTENT=x
    This parameter sets the spare diagnostic extent in MiB.  The
    diagnostic extent determines how much data can be tested before the
    test must sleep. This parameter slows down the test operations so
    they will not affect the performance of the system.  Increasing the
    EXTENT will allow more data to be tested in a single pass.  Any
    changes applied to extent will affect tests in progress as well as
    future testing.
    The valid range for 'x' is 1..32 MiB.

    Default is 8 MiB.

INFO[=tc]
    This parameter displays the information and status about a specific
    spare in the system.
    The disk is specified by its physical tier and channel locations,
    'tc', where:
    't' indicates the tier in the range <1..128>, and
    'c' indicates the channel in the range <ABCDEFGHPS>.

PATTERN=x
    This parameter sets the system spare diagnostics pattern.  The test
    pattern determines the pattern written to the disks during the test.
    The system supports the following patterns:

    * UNIQUE    - includes unique information including timestamp
    * AA        - A pattern of 0xAA is written to each byte
    * 55        - A pattern of 0x55 is written to each byte
    * FF        - A pattern of 0xFF is written to each byte
    * 00        - A pattern of 0x00 is written to each byte
    * COUNTUP   - A pattern of counting up is written to each byte
    * COUNTDOWN - A pattern of counting down is written to each byte

    The default is UNIQUE.

    .. note::
       Tests in progress are not affected by this parameter setting.
       Changing the pattern only applies to tests started after the
       parameter was modified.

PAUSE
    This parameter will pause any ongoing diagnostic operation only on
    the unit from which the command is run.  If a test is being run from
    the other unit in a dual, the pause command will NOT affect that
    test.

RESUME
    This parameter will release any paused diagnostic operations and
    allow them to continue only on the unit from which the command is
    run.  If a test has been paused on the other unit in a dual, the
    RESUME command will NOT affect that test.

START
    This parameter will start the spare diagnostics task if it is not
    running. Note that this will start diagnostics on both units in a
    dual as this is a system parameter.

STOP
    This parameter will abort any ongoing diagnostic operations.  Note
    that this command will stop them and then the task will be idle until
    the RESTART command is executed.  Note that this will stop
    diagnostics on both units in a dual as this is a system parameter.
