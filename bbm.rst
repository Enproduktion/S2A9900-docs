=====
 BBM
=====

BBM  Displays/Changes the Bad Block Manager (BBM) functionality.

This command is used to enable and disable the Bad Block Manager (BBM)
feature in the system.  The bad blocks can be displayed, defaulted, and
edited.  Each :doc:`lun` in the system can be configured to use the Bad Block
Manager independently.

CC_ONLY=[ON|OFF]
    This parameter is used to turn ON or OFF the Check Condition Only
    functionality. When ON, the Bad Block Manager generates a check
    condition SCSI status when attempting to read a host LBA that
    overlaps a bad block for the LUN specified. When OFF, the Bad Block
    Manager generates a check condition SCSI status but also gives the
    host the corrupted data when attempting to read a Host LBA deemed a
    BB on the system. The CC_ONLY option is defaulted to ON.

DEFAULT
    This parameter is used to default the configuration and all entries
    for all LUNs. When this command is done it will have performed a
    'clean' operation such that BBM will be in a completely defaulted
    power up state.  The default configuration is as follows :
    BBM top level is disabled.
    All LUNs are disabled for BBM processing at the LUN level.
    Check condition on BBM will be set to also provide back data.

DISABLE
    Disables the Bad Block Manager feature in the system. This is the
    disable that shuts down BBM tracking at the highest level.  When this
    is disabled, the BBM feature will not be in use for any part of the
    system.

ENABLE
    Enables the Bad Block Manager feature in the system. This is the
    highest level enable that allows the system to be able to start using
    the BBM.  To actually put the BBM feature in use, individual LUN
    enables must also be activated via the 'LUN_ENABLE' command.

LUN_DEFAULT
    This parameter is used to default lun entries in the BBM for
    specified LUNs.

LUN_DISABLE
    Disables the Bad Block Manager (BBM) feature in the system for all
    LUNs or a set of user specified LUNs where the Bad Block entries for
    that LUN will no longer be examined and no SCSI Check Condition (CC)
    status messages will be generated based upon the Bad Block entries
    for the LUN(s). While the BBM for a LUN is disabled, the user is
    still allowed to edit, default, and display Bad Block information on
    the LUN.  This is the default setting.

LUN_DISPLAY
    This parameter allows the user to display the Bad Block Manager data
    (including the entries in the bad block list) for all LUNs or a set
    of user specified LUNs.

LUN_EDIT[=x]
    This parameter allows the user to edit the Bad Block Manager for a
    specified LUN.  This will provide an interactive session for the user
    to make changes to the bad block entries.

LUN_ENABLE
    Enables the Bad Block Manager feature in the system for all LUNs or a
    set of user specified LUNs where unrecoverable data conditions will
    be added to this LUN and the bad block entries will be managed.  Bad
    block entries will be added for this LUN when data read from the
    disks do not provide enough information to recreate the host data.
    Bad block entries will be removed from this LUN when host data is
    written over an area that is considered a bad block. All reads and
    writes will be checked against the Bad Block Manager when the LUN is
    enabled for processing bad blocks. The default setting is disabled.

LUN_SUMMARY
    This parameter allows the user to display the Bad Block Manager
    summary for all LUNs or a set of user specified LUNs.
