=======
 ALARM
=======

ALARM  Functions pertaining to the AVR System Alarm.

This command controls the audible AVR system alarm.

DISABLE
    Disable the AVR system alarm.
    This command disables the AVR System Alarm for any alarms that are
    currently sounding and all future alarms.  This command only disables
    the alarm for the current power cycle.

ENABLE
    Enables the AVR system alarm.
    This command enables the AVR System Alarm for any alarms that are in
    progress and all future alarms.  By default alarms are always enabled
    unless they are disabled via the ALARM DISABLE command or the
    hardware alarm button.

STATUS
    Displays whether the AVR system alarm is enabled or disabled.
    NOTE: Even though the system alarm can be enabled or disabled by both
    hardware and software methods, the status does not identify the
    method used. Additionally, neither method takes precedence over the
    other. Therefore, a hardware command to disable the alarm can
    override a software command to enable it and vice versa.

TEST
    Tests the AVR system alarm.
