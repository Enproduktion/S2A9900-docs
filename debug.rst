=======
 DEBUG
=======

DEBUG  Enables/Disables the system debug messages.

This command is used to display and change the settings controlling the
generation of the system debug messages.  Each system debug message is
assigned a general debug type and a specific debug level; enabling a
debug level for a given debug type causes all debug messages belonging
to that same type and level to be generated for display.
Previously generated messages can be viewed by using the LOG command on
the CLI.
This command is provided for diagnostic purposes and should only be used
by qualified service personnel.

DMT_IHD
    Saving of cache nodes to persistent internal memory debug messages:

    ===== ==========================================================
    Level  Description of Messages Output:
    ===== ==========================================================
    0     Displays save high level requests.
    1     -- Not used. --
    2     Displays save and load messages from persistent memory.
    3     Displays save list entry messages.
    4     -- Not used. --
    5     Displays save dual lockout messages.
    6     IHD_RETURN_VALUES
    7     IHD_FUNCTION_TRACE
    ===== ==========================================================
