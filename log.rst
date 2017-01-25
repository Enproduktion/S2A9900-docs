=====
 LOG
=====

LOG  Displays a log of previous system messages.

This command is used to display a log of previous system messages.  The
log is saved in non-volatile memory and will automatically roll over
when full.

CHECKCLEAR
    Clears the Check Condition Log.

CHECKCONDITION|CHECKCONDITION=MORE
    Displays the Check Condition Log.  'MORE' will display additional
    information concerning the check condition.

CLEAR
    Allows the user to clear the log of all previous messages.

DISKFAILCLEAR
    Clears the Disk Fail Log.

DISKFAIL|DISKFAIL=MORE
    Displays the Disk Fail Condition Log.  'MORE' will display additional
    information concerning why the disk failed.

FILTER=EMERG|ALERT|CRITICAL|ERROR|WARNING|NOTICE|INFO|DEBUG
    Allows the user to filter the display of the MLS log according to
    what level of message they would like to view.  When using the FILTER
    command the log will show messages at the specified priority level
    and all of the messages above the specified priority level.

FILTERCPU
    Allows the user to filter the display of the MLS log according to
    what card slot the message came from.  When using the FILTERCPU
    command the log will show messages of the specified slot ID.

LINES=x
    Specifies the number of lines that should be displayed from the end
    of the log specified.
