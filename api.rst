=====
 API
=====

API  Display/Change the enabling/disabling of API connections.

Allows the user to display/change whether API connections are currently
(temporarily) ENABLEd or DISABLEd.  Note that this command only provides
control over API connections during the current power cycle.  To
'permanently' disable or enable API connections (i.e. across
power-cycles), the user is referred to the NETWORK [[API_SERVER=ON|OFF]
command.  Note that the default setting for this command at power-on is
ENABLEd.

CLEARSTATS
    Resets the collected statistics on API connections.

DISABLE
    Allows the user to (temporarily) disable the establishment of
    connections to the API Server.
    Users at remote locations will be unable to establish a new API
    connection until an API ENABLE command is issued.

ENABLE
    Allows the user to (re-)enable the establishment of connections to
    the API Server.

RESTART
    Allows the user to do a full restart on the API server.

SHUTDOWN
    Allows the user to totally shutdown the API server. This command
    should not be used under normal circumstances, use API DISABLE to
    just turn off API accesses.
    Note: This command will only shutdown the API server during the
    current power cycle, refer to NETWORK API_SERVER in order to make
    command permanent.

START
    Allows the user to start the API server the was shutdown using the
    API SHUTDOWN command.  This command should not be used under normal
    circumstances.  For most circumstances API ENABLE and API DISABLE are
    appropriate.
    Note:  NETWORK API_SERVER must be set to ON for this command to work.

STATS
    Displays the collected statistics on API connections.
