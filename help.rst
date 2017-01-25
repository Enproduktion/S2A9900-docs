======
 HELP
======

HELP  Displays help information about system commands.

By default, this command will display a list of all the available system
commands.  This command will also display detailed information about a
specific command if one is specified.  Information about the specific
parameters of a command can be displayed if the command is specified
followed by the parameters of interest.

Usage:

.. code-block:: bash

    HELP|?
    HELP|? <command>
    HELP|? <command> <parameter, parameter, ...>
    (and as a special exception to the usual method of command order:
    <command> HELP|?
    <command> HELP|? <parameter, parameter, ...>

For example:

.. code-block:: bash

    # To display detailed help on the help command:
    HELP HELP
    # To display detailed help on any parameters beginning
    # with a 'P' for the help command:
    HELP HELP P

SHORT
    Displays a shorter form of help for the command(s) and/or
    parameter(s).
    This flag only applies to the current HELP command's execution.
    It must appear immediately adjacent to the HELP command in order to
    be honored with it.
