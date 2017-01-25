==========
 SETTINGS
==========

SETTINGS  Displays/Changes the CLI/Telnet session control settings.

This command allows the user to display/change the CLI's (and Telnet's)
various session control settings.

DEFAULTS
    Allows the user to reset all the CLI and telnet session control
    settings to their default values.

LINES[=x]
    This parameter displays or sets the number of lines displayed at a
    time in a page of screen information.  Pages provide a way to control
    the amount of information displayed to the user at one time.  The
    user is prompted to either press a specified key in order to scroll
    from one page to the next, or, (in certain circumstances) to
    terminate the display entirely.
    Valid range is 0 to 512 lines, where 0 indicates that no paging is to
    be performed on the output information.

    Default is 0.

PROMPTINFO=ON|OFF
    This parameter enables and disables extra status information in the
    CLI prompt.  When enabled, the CLI prompt will indicate if the system
    is booting (BOOTING), failed (FAILED) or waiting for a restart
    (RESTART NEEDED).

    Default is enabled.
