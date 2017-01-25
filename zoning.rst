========
 ZONING
========

ZONING  Displays and changes the default host port LUN zoning.

This command is used to change the default LUN zoning for the anonymous
users on each host port.  LUN zoning indicates which internal LUNs the
user will have access to and where the internal LUN will appear to the
user.  The users are identified by their 64-bit World Wide Name.  The
system can store the configuration of up to 512 users.  Any user
accessing the system without having a World Wide Name entry in the
configuration table will be considered anonymous and will only be
granted the default LUN zoning for the host port they are connected to.
Note that users can be added to and configured for the system using the
USER command.

DEFAULT[=x|ALL]
    This parameter is used to restore the zoning on a host port to the
    default settings. If no host port is specified, the user will be
    prompted for one.

DLM[=x|ALL]
    This parameter displays the direct LUN mapping information for the
    host port(s) designated by 'x', or ALL.  'x' will display the LUN
    mapping information for a single host port; ALL will display the LUN
    mapping information for all host ports with DLM enabled.
    If no host port is specified, the user will be prompted for one.
    Note that all LUNs that are mapped for the port(s) are displayed,
    regardless of whether or not the LUNs currently exist in the system.

DLM_DISABLE[=x|ALL]
    This parameter disables the direct LUN mapping for the host port(s)
    designated by 'x', or ALL.  'x' will disable the direct LUN mapping
    for a single host port; ALL will disable the direct LUN mapping for
    all host ports.
    If no host port is specified, the user will be prompted for one.

DLM_ENABLE[=x|ALL]
    This parameter enables the direct LUN mapping for the host port(s)
    designated by 'x', or ALL.  'x' will enable the direct LUN mapping
    for a single host port; ALL will enable the direct LUN mapping for
    all host ports.
    If no host port is specified, the user will be prompted for one.

DLM_LUN_DISABLE[=ALL]
    This parameter disables the direct LUN mapping for specified LUNs for
    the specified host port; ALL will disable the direct LUN mapping for
    all LUNs for the specified host port.
    If ALL is not specified, the user will be prompted for LUNs.
    Note that LUNs can be disabled for DLM, regardless of whether or not
    the LUNs currently exist in the system.

DLM_LUN_ENABLE[=ALL]
    This parameter enables the direct LUN mapping for specified LUNs for
    the specified host port; ALL will enable the direct LUN mapping for
    all LUNs for the specified host port.
    If ALL is not specified, the user will be prompted for LUNs.
    Note that LUNs can be enabled for DLM, regardless of whether or not
    the LUNs currently exist in the system.
    DLM must be enabled via the DLM_ENABLE command before LUNs can
    be enabled.

EDIT[=x]
    This parameter is used to edit the default LUN zoning on each host
    port. If no host port is specified, the user will be prompted for
    one.
