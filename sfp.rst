=====
 SFP
=====

SFP  Displays information about the host SFPs.

This command is used to display information about the host SFPs.

    HOSTDIAG
    This parameter specifies that the SFP diagnostic information for
    ports specified by the PORT parameter will be displayed.
    If PORT is not supplied, it will prompt for port(s).

    HOSTINFO
    This parameter specifies that the SFP information for ports specified
    by the PORT parameter will be displayed.
    If PORT is not supplied, it will prompt for port(s).

PORT=x|ALL
    This parameter specifies the specific host port(s) to be displayed
    when used in combination with any of the following other parameters:

    * HOSTINFO,
    * HOSTDIAG.

    (If PORT is left unspecified, the user is prompted for his choice of
    host ports).

    Valid port values, 'x', are 1 to 4.
