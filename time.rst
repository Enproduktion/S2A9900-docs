======
 TIME
======

TIME  Displays/Changes the current system time.

Displays/Changes the current system time.

GETTIME
    Instructs the system to get the time from the default SNTP time
    server. The default SNTP time server address can be changed with the
    command TIME SNTPIP=aaa.bbb.ccc.ddd

GETTIME=aaa.bbb.ccc.ddd
    This command instructs the system to get the time from the SNTP time
    server specified. This command will not update the SNTP address the
    system uses for periodic polling. The SNTP address the system uses
    for polling can be changed with the command TIME
    SNTPIP=aaa.bbb.ccc.ddd

SNTPIP=aaa.bbb.ccc.ddd
    Specifies an IP address of a SNTP time server for the system to poll.

TIMEZONE
    Sets the timezone-specific information for the system by prompting
    the user.
    The following fields will be requested interactively from the user:
    <name>      : is for display only.  It can be 3 characters,
    maximum, with no embedded whitespace.
    <UTC_offset>: is the offset in hours and minutes from
    Coordinated Universal Time (i.e. Greenwich
    Mean Time).
    Timezone offsets are represented as:

    * '+/-HH.MM'

    where:

    * HH: indicates the hours of the offset.
      The valid range is: 0..+/-12.
    * MM: indicates the minutes of the offset.
      The valid range is: 00..59.
      <DST_start> : indicates the start time for Daylight Savings.
      <DST_end>   : indicates the end time for Daylight Savings.
      Both the <DST_start> and <DST_end> times are
      given in the format: 'MMDDHH', where:
    * MM: indicates the month, in the range 1..12.
    * DD: indicates the day,   in the range 1..31.
    * MM: indicates the hour,  in the range 0..23.

    The user can verify the designated DST functionality, as follows:

    1. Ensure that SNTP updating is disabled, via the CLI command:
       'NETWORK SNTP=OFF'.
    2. Set the <DST end time> to a particular day at, e.g. 1:00am.
    3. Using the CLI DATE and TIME commands, set the system's current
       date and time to 23:55pm of the day before DST expiration.
    4. As the 1:00am. time is passed an hour later, the time will be
       automatically adjusted appropriately.
       Also, if the DST start date is set and is in effect, the effective
       offset will be adjusted by 1 hour.

    The TIMEZONE parameter is flexible enough to support any time zone in
    the world. However in order to support daylight saving time (DST) the
    administrator will need to update the time zone information each year
    because the start and end times change each year.

TIMEZONEDISABLE
    Clears the timezone.

hh:mm:ss
    Allows the user to change the system time to the new value indicated
    by 'hh:mm:ss', where:

    * hh: indicates the hour   in the range 0..23.
    * mm: indicates the minute in the range 0..59.
    * ss: indicates the second in the range 0..59.

    **Examples**

    To simply display the system time:  TIME
    To change the system time to noon:  TIME 12:00:00
