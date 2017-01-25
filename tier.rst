======
 TIER
======

TIER  Displays information about the tiers in the system.

This command displays the current status and configuration of the tiers
in the system.  Tiers are automatically added to the system when the
disks are detected.  Tier ownership is determined when the first LUN is
added to a tier, and is unassigned when the last LUN resident on a tier
is removed. A tier will be automatically uninstalled if it is both not
in use by any of the LUNs and if all of the disks in the tier are
removed or moved to another location.

The status of the disks in each tier is shown as follows:

A single character in the range ABCDEFGHPS
indicates a healthy status for the disk on the channel
corresponding to that letter, where:

* 'S' indicates the spare channel,
* 'P' indicates the parity channel, and all remaining characters indicate data channels.
* An 'e' indicates the disk is served by an enclosure.
* A  '.' indicates that the disk was failed by the system.
* An 'r' indicates that the disk was failed by the system and replaced by a spare disk.
* A  '!' indicates that the disk is in the wrong location.
* A  '?' indicates that the disk has failed the diagnostics tests.
* A  '*' indicates that the disk is an enclosure device.
* A  ' ' indicates that the disk is not installed.

The speed of the rebuild and format operations can be adjusted with the
DELAY and EXTENT parameters.

8+1=t|ALL
    This parameter converts a tier into 8+1 mode. If the tier is
    currently an 8+2 Tier then the following applies:    If any LUNs
    exist on the tier then the system will need to fail the P channel.
    The disks on the P channel will need to be rebuilt.    The tier will
    not be converted if any other disks on the tier are failed. If the
    tier is currently a SPARE Tier then the following applies:    The
    tier will not be converted if any of the channel spares are currently
    replacing a failed disk on another tier. Specify the tier to convert
    with 't' or use 'ALL' to convert all the tiers in the system. The
    'ALL' parameter will also changed the default setting of missing
    tiers to be 8+1.

    Tiers are 8+2 mode by default.

8+2=t|ALL
    This parameter converts a tier into 8+2 mode. If the tier is
    currently an 8+1 Tier then the following applies:    If any LUN
    exists on the tier then the system will need to fail the P and S
    channels.    The disks on the P and S channels will need to be
    rebuilt.    The tier will not be converted if any other disks on the
    tier are failed.    The tier will not be converted if any disks are
    replaced by a spare or the spare disk is currently replacing a failed
    disk on another tier. If the tier is currently a SPARE Tier then the
    following applies:    The tier will not be converted if any of the
    channel spares are currently replacing a failed disk on another tier.
    Specify the tier to convert with 't' or use 'ALL' to convert all the
    tiers in the system. The 'ALL' parameter will also change the default
    setting of missing tiers to be 8+2.

    Tiers are 8+2 mode by default.

AUTOREBUILD=ON|OFF
    This parameter enables and disables the automatic disk rebuilding
    when a failed disk is removed and replaced with a new disk or a
    failed disk that has not been replaced has returned and can be
    rebuilt quickly using the rebuild journal. This parameter also
    enables and disables the automatic replacement of failed disks with
    spare disks.

    Default is ON.

AUTORESTART=ON|OFF
    This parameter enables and disables the automatic disk restart when a
    failed disk due to I/O timeout.

    Default is OFF.

CHANGEMAP
    This parameter changes the current tier mapping for the disks in the
    array.  This changes the position of the tiers in the system to
    conform with the layout of different disk modules.  This parameter
    should only be used when the system is first configured.

CONFIG
    Displays the detailed disk configuration information for all of the
    tiers.  See the general TIER command help description for an
    explanation of the 'Owner' and 'Disk Status' fields.  'Total LUNs'
    indicates the number of LUNs which currently reside on the tier.
    Note that the health indication for the spare channel under the
    'Healthy Disks' heading is an indication of the health of the spare
    disk (if any) which is currently being used to replace a disk on the
    listed tier; the health indication for the spare channel that is
    physically on the listed tier is found under the 'Sp H' heading.  'F'
    indicates the failed disk (if any) on the tier.  'R' indicates the
    replaced disk (if any) on the tier.  'Sp H' indicates if the spare
    disk that is physically on the tier is healthy.  'Sp A' indicates if
    the spare disk that is physically on the tier is available for use as
    a replacement.  'Spare Owner' indicates the current owner of the
    physical spare, where ownership is assigned when the spare is used as
    a replacement.  Note that 'RES-#' will appear under this heading
    while a replacement operation is underway to indicate that unit '#'
    currently has the spare reserved.  'Spare Used on' indicates the tier
    (if any) on which this physical spare is being used as a replacement.
    'Repl Spare from' indicates the tier (if any) whose spare disk is
    being used as a replacement on this tier.

    .. note::

       Note that this command will not display the detailed information
       about channel spares.

CONFIG=ALL
    Displays the detailed disk configuration information for all of the
    tiers.  This command is a combination display of both the CONFIG
    command and the CONFIG=SPARE command to provide a detailed picture of
    the entire system configuration.

CONFIG=SPARE
    Displays the detailed disk configuration information for channel
    spares only. 'Sp H' indicates if the spare disk that is physically on
    the tier is healthy.  'Sp A' indicates if the spare disk that is
    physically on the tier is available for use as a replacement.  'Spare
    Owner' indicates the current owner of the physical spare, where
    ownership is assigned when the spare is used as a replacement.  Note
    that 'RES-#' will appear under this heading while a replacement
    operation is underway to indicate that unit '#' currently has the
    spare reserved.  'Spare Replaces' indicates the disk (if any) for
    which this spare is being used as a replacement.

DELAY=x
    This parameter sets the system rebuild delay.  The rebuild delay
    determines how long a rebuild or format operation will pause after it
    reaches the rebuild extent.  This parameter slows down the rebuild
    and format operations so they will not affect the performance of the
    system.
    This system rebuild delay value is given in 100 millisecond
    increments.
    The valid range for 'x' is 0..1000.

    The default is 30.

DELAYIOLIMIT=x
    This parameter indicates how many host IO requests the system will
    allow per second before the system begins automatically slowing down
    the maintenance operations.
    The valid range for 'x' is 0..1000.

    The default is 0.

EXTENT=x
    This parameter sets the system rebuild extent in MiB.  The rebuild
    extent determines how much data can be rebuilt before the rebuild and
    format operations must pause.  This parameter slows down the rebuild
    and format operations so they will not affect the performance of the
    system.  Increasing the EXTENT will allow more data to be rebuilt in
    a single pass.
    The valid range for 'x' is 1..128 MiB.

    Default is 32 MiB.

JOURNAL
    Displays information about the rebuild journal for each tier in the
    system. If a tier is specified then detailed information about the
    tiers journal will be displayed.
    The rebuild journals contain bitmaps which indicate which portions of
    the disks in a tier have been updated with new data while a disk was
    failed or replaced. The system uses the information in the journals
    to reduce the rebuild time of a drives that have not been swapped
    out. This can dramatically lower rebuild time since only portions of
    the tier may have been updated while the drive was failed or
    replaced.
    The granularity of the journal will be 8MiB of data on a single disk
    or 64MiB of host data. Thus a single host write will force the system
    to rebuild a minimum of 8MiB of data on the disk. A new host write
    into a 8MiB section that has already been journaled will not cause a
    new journal entry. The system will automatically update journals when
    disks are failed or replaced regardless of whether journaling is
    enabled.
    To ensure that the journals are correct the system carefully monitors
    the state of the journals and will automatically invalidate or
    disable the journals if it detects a condition where the journal
    cannot be used or journal information could potentially be lost.

    The following summarizes the limitations that apply to journaling:

    Rebuild journaling will automatically be disabled if the failed disk
    is swapped with a new disk. The system will track the serial number
    of the disks when they are failed and will force a rebuild of the
    entire disk if the serial number changes.

    Rebuild journaling will not be used when a failed disk is replaced by
    a spare. The rebuild journal can be used when rebuilding a replaced
    disk that has not been swapped.

    The system will invalidate the journal on tiers that have failed or
    replaced disks on boot up. This is required because the system does
    not save the journal information.

    Rebuild journaling will be managed by the controller that owns the
    tier. If a controller is failed, then the journals on the tiers owned
    by that controller will be invalidated.

    The system tracks the original owner of a tier when a drive is failed
    so changing the ownership of the tier will disable use of the journal
    for rebuilds on that tier.

    Rebuild journaling will be disabled when rebuilding disks that are
    failed due to a change in the parity mode of the tier.

    Use of the rebuild journal will be temporarily disabled if the system
    is rebuilding a LUN that is a backup LUN in a mirror group.

    The status field indicates the current status of the journal.
    Ready  - The journal is waiting for updates.
    Active - A disk is failed and the journal has updates.
    All other statuses indicate why the journal cannot be used.

    The Rebuild OK field indicates if a rebuild can use the journal.

    * Off    - Journaling not enabled.  Use JOURNAL=ON to enable.
    * Yes    - Journaling can be used when rebuilding.
    * No     - Journaling cannot be used.

    The rebuilds will only use the journals if the 'Rebuild OK' field
    indicates 'Yes'. In order to use journaling on rebuilds, the
    operation must be manually started using DISK REBUILD=tc where 't'
    indicates the tier, and 'c' indicates the channel or REBUILD=ALL
    which will start a rebuild on all disks.

JOURNAL=ON|OFF
    This parameter enables and disables use of the journals during
    rebuild operations. The system will automatically update the journals
    when disks are failed or replaced regardless of this setting. This
    parameter only indicates if the journal can be used during the
    rebuild.

    Default is ON.

JOURNAL=t
    Displays information about the rebuild journal for the specified
    tier. This screen will give detailed information about the status of
    the journal and a display of all the journal entries for the tier.
    This screen will also give more detailed information on the status of
    the journal and will indicate why it was disabled or invalidated

MAP
    This parameter shows the current tier mapping mode for the disks in
    the array.

MAXREBUILDS=x
    This parameter sets the maximum number of active rebuilds for each
    controller in the system. Additional rebuilds will be queued up.
    The valid range for 'x' is 1..16.

    Default is 4.

MAXVERIFIES=x
    This parameter sets the maximum number of concurrent tier verifies on
    a system. The range is 1 to 16.  The default value is 2.

PAUSE[=t]
    This parameter will pause any ongoing rebuild operations.
    A single tier can be specified by 't'.
    Note that rebuild operations can be started either automatically (see
    the AUTOREBUILD option), or with the DISK REBUILD command.

QSHOW
    Display the rebuild queue in a debug format and in order of request.

    RESUME[=t]
    This parameter will release any paused rebuild operations.
    A single tier can be specified by 't'.
    Note that rebuild operations can be started either automatically (see
    the AUTOREBUILD option), or with the DISK REBUILD command.

SMARTREPLACE=ON|OFF
    This parameter enables and disables the automatic proactive
    replacement of disks that indicate a SMART event has triggered.  A
    disk will only be replaced by a spare disk if it indicates that SMART
    has tripped, AUTOREBUILD is ON, and SMARTREPLACE is on.

    Default is OFF.

SPARE=t
    This parameter converts a tier into a SPARE Tier to be used for
    Channel Sparing. If any LUN exist on the tier then the system will
    not allow the conversion. The tier will not be converted if the spare
    disk is currently replacing a failed disk on an 8+1 tier. Specify the
    tier to convert with 't'.

    Tiers are 8+2 mode by default.

STANDBY[=t]
    This parameter displays the current STANDBY status for all tiers
    owned by the unit.
    A single tier can be specified by 't'.
    This parameter is only valid for SATA tiers.
    The valid range for 't' is <3..128>.

STANDBY_DISABLE=[t|ALL]
    This parameter disables STANDBY mode for the specified tier(s).
    A single tier can be specified by 't' as long as it is not owned by
    the other unit.  The valid range for 't' is <3..128>.
    If ALL tiers are specified, then all tiers owned by the unit will be
    disabled for STANDBY mode.

    .. note::

       This parameter is only valid for SATA tiers.

STANDBY_ENABLE=[t|ALL]
    This parameter enables STANDBY mode for the specified tier(s).
    A single tier can be specified by 't' as long as it is not owned by
    the other unit.  The valid range for 't' is <3..128>.
    If ALL tiers are specified, then all tiers owned by the unit will be
    enabled for STANDBY mode with the current standby timeout value.

    .. note::

       This parameter is only valid for SATA tiers.

STANDBY_MAX_TIERS[=x]
    This parameter sets the maximum number of tiers that may be taken out
    of STANDBY mode at once, to avoid over-stressing the enclosure power
    supplies.
    This parameter is only valid for SATA tiers.
    The valid range for 'x' is 1..120.

    Default is 8.

STANDBY_TIMEOUT[=x]
    This parameter sets the standby timeout value for all disks (in
    minutes).  It defines the period that a disk must receive no I/O
    commands before entering STANDBY mode (if enabled for the tier in
    which the disk resides).
    This parameter can only be changed if STANDBY mode is disabled for
    all tiers.
    This parameter is only valid for SATA tiers.
    The valid range for 'x' is 30..330.

    Default is 30.

STOP[=t]
    This parameter will abort any active rebuild operations.
    A single tier can be specified by 't'.
    Note that rebuild operations can be started either automatically (see
    the AUTOREBUILD option), or with the DISK REBUILD command.

VERIFY
    Displays the verify information by tier settings for all valid tiers
    in the system.

    VERIFY=ON|OFF
    Prompts the user for a list of TIERs on which background verify by
    tier will be turned either ON or OFF.
    The 'VERIFY=ON' argument will turn on background verify for the
    specified tier(s), optionally running in continuous mode. A
    'VERIFY=OFF' command, however, only turns off the Background Verify
    setting for the specified tier(s).  Therefore, any verifies already
    active on the tier(s) will not terminate until after the completion
    of that verify's current iteration.  To stop all Verify operations
    immediately, use 'TIER STOP'.

VERIFY=x
    Turns ON background verify for TIER 'x', where 'x' is in the range
    0..128.

VERIFYCLEAR[=x|ALL]
    This parameter allows the user to clear the verify count and the time
    of last verify for a specific tier designated by 'x' or all tiers.
