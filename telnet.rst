========
 TELNET
========

TELNET  Display/Change the enabling/disabling of remote Telnet sessions.

Allows the user to display/change whether remote Telnet sessions are
currently (temporarily) ENABLEd or DISABLEd.  Note that this command
only provides control over Telnet sessions during the current power
cycle.  To 'permanently' disable or enable Telnet sessions (i.e. across
power-cycles), the user is referred to the NETWORK [TELNET=ON|OFF]
command.  Note that the default setting for this command at power-on is
ENABLEd.
The administrator is strongly advised to perform any commands affecting
the system's configuration from the CLI UART only (and not from a Telnet
session), and to only perform such commands after issuing the DISABLE
command, so that remote users cannot log in to the system in the middle
of an administrative command.

CLEARSTATS
    Clears the collected statistics on Telnet sessions.

DISABLE
    Allows the user to (temporarily) disable the establishment of remote
    Telnet sessions during the current power cycle.  Users at remote
    locations will be unable to start a new Telnet session until after a
    corresponding TELNET ENABLE command is issued.
    To disable the Telnet functionality completely and maintain that
    setting through a power-cycle, refer to the NETWORK TELNET=ON/OFF
    command.

ENABLE
    Allows the user to (re-)enable the establishment of remote Telnet
    sessions during the current power cycle.  Note that basic Telnet
    functionality for the system must already have been enabled with the
    NETWORK TELNET=ON/OFF command for this parameter to have any effect.

KILLPARTNER[=m] [DISABLE]
    Allows the user to cancel the currently active Telnet session on the
    other unit in a dual configuration, where 'm' specifies the number of
    minutes to pause after notifying the remote user of the impending
    termination before actually cancelling the session, and DISABLE, if
    present, indicates that the creation of future telnet sessions should
    be disabled after the current session is terminated.  Sessions can be
    re-enabled with the TELNET ENABLE command.
    Valid values for 'm' fall in the range: 0..15.
    An attempt is made to prompt the remote user to first complete any
    active CLI command, and then to logout of the telnet session.
    However, the remote session will be automatically cancelled within
    'm' minutes if there is no response; 'm' defaults to 1 if left
    unspecified.  If 'm' is 0, the remote user is notified, but the
    session is cancelled immediately without waiting for any response
    from the remote user.
    Note that if the remote session is KILLed while a CLI command is in
    progress, the rest of the command's interaction will be transferred
    back to the unit's serial CLI interface.

STATS
    Displays the collected statistics on Telnet sessions.
