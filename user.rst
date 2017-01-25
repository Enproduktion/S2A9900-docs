======
 USER
======

USER  Displays/Changes the host and anonymous users' information.

This command is used to display/change the system security settings for
all the host users accessing the system by specifying their LUN and port
mappings:

The LUN mapping indicates which internal LUNs the user will have
access to and where the internal LUN will appear to the user
(i.e. as its external LUN).

The Port mapping indicates those ports through which the user may
gain access to the unit.

The host users are identified by their 64-bit World Wide Name.  The
system can store the configuration of up to 512 host users.  Any user
accessing the system without a World Wide Name entry in the
configuration table will be considered anonymous and will be granted the
default LUN zoning for the host port they are connected to.  The default
LUN zoning for each host port can be changed with the ZONING command.
Known host users may be assigned either their own unique LUN mapping, or
the default LUN zoning for the host port they are connected to.  A
listing of the system's internal LUNs can be displayed with the LUN
command.

ADD
    This parameter adds and configures a new host user for the system.
    Users who are currently logged in anonymously may be specified simply
    by their current ID value; otherwise a World Wide Name value is
    required to identify the new host user.

AUDIT[=ON|OFF]
    This parameter enables and disables the host user auditing, if ON or
    OFF is specified, respectively.  Otherwise, it will display the
    current host user auditing setting.  When auditing is turned ON, the
    system will display a message whenever a host user logs into or out
    of the system.  Anonymous users are included.

    Default is OFF.

CONNECTIONS
    This parameter displays all the current host and anonymous user
    connections.  Note that only LUNs which currently exist in the system
    are displayed in the LUN Zoning/Mapping list for each user.

DEL|DELETE[=x]
    This parameter deletes an existing host user, 'x', from the system.
    If no host user is specified, the user is prompted for one.

DLM[=x|ALL]
    This parameter displays the direct LUN mapping information for the
    host user(s) designated by 'x', or ALL.  'x' will display the LUN
    mapping information for a single host user; ALL will display the LUN
    mapping information for all host users with DLM enabled.
    If no host user is specified, the user will be prompted for one.
    Note that all LUNs that are mapped for the user(s) are displayed,
    regardless of whether or not the LUNs currently exist in the system.

DLM_DISABLE[=x|ALL]
    This parameter disables the direct LUN mapping for the host user(s)
    designated by 'x', or ALL.  'x' will disable the direct LUN mapping
    for a single host user; ALL will disable the direct LUN mapping for
    all host users.
    If no host user is specified, the user will be prompted for one.
    Note that users can be disabled for DLM, regardless of whether or not
    the users currently exist in the system.

DLM_ENABLE[=x|ALL]
    This parameter enables the direct LUN mapping for the host user(s)
    designated by 'x', or ALL.  'x' will enable the direct LUN mapping
    for a single host user; ALL will enable the direct LUN mapping for
    all host users.
    If no host user is specified, the user will be prompted for one.
    Note that users can be enabled for DLM, regardless of whether or not
    the users currently exist in the system.

DLM_LUN_DISABLE[=ALL]
    This parameter disables the direct LUN mapping for specified LUNs for
    the specified host user; ALL will disable the direct LUN mapping for
    all LUNs for all users where DLM is enabled..
    If ALL is not specified, the user will be prompted for LUNs.
    Note that LUNs can be disabled for DLM, regardless of whether or not
    the LUNs currently exist in the system.

DLM_LUN_ENABLE[=ALL]
    This parameter enables the direct LUN mapping for specified LUNs for
    the specified host user; ALL will enable the direct LUN mapping for
    all LUNs for all users where DLM is enabled.
    If ALL is not specified, the user will be prompted for LUNs.
    Note that LUNs can be enabled for DLM, regardless of whether or not
    the LUNs currently exist in the system.
    DLM must be enabled via the DLM_ENABLE command before LUNs can
    be enabled.

EDIT[=x]
    This parameter edits the LUN mapping for an existing host user, 'x'.
    If no host user is specified, the user will be prompted for one.

SHOWMAP[=x|ALL]
    This parameter displays the detailed user LUN mapping information for
    the host user(s) designated by 'x', or ALL.  'x' will display the LUN
    mapping information for a single host user; ALL will display the LUN
    mapping information for all host users.
    If no host user is specified, the user will be prompted for one.
    Note that all LUNs that are mapped for the user(s) are displayed,
    regardless of whether or not the LUNs currently exist in the system.
