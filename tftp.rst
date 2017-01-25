======
 TFTP
======

TFTP  Performs an update of the firmware on the system using TFTP.

This command is used to update the firmware of the unit using TFTP.  The
system will download the new firmware image and save it in flash.  The
unit will need to be restarted before the new firmware can be used.

<IP_address> <Filename> <RESTART>
    Supplies the TFTP server the IP Address from which to transfer a copy
    of the filename containing the desired software upgrade.  Note that
    the user is prompted for this information if it is not explicitly
    given.

    <IP_address> is a string in the form: aaa.bbb.ccc.ddd,

    <Filename>   is a string value.

    If RESTART is entered with all the other parameters after a
    successful TFTP download, the unit will restart without prompting for
    any information.
