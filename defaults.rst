==========
 DEFAULTS
==========

DEFAULTS  Restores the system to its default configuration.

This command is used to restore the system to its default configuration.
The system will halt all I/O requests, delete all the LUNs, and restore
all the parameters back to their defaults values.  This is a destructive
operation which will delete all the data stored in the system.  The
system will then ask if it should erase all the configuration
information stored on the disks.  This will prevent the system from
retrieving the backup copies of the configuration settings from the
disks after the system is restarted.  This means that to read the
parameter blocks off the disk, the current controller will have to be
removed and replaced by another system.  After the defaults have been
loaded, the system will ask if it should begin reconfiguring by scanning
for the disks.  New LUNs can be created after the disks have been added
back to the system.

The following table outlines the combinations of answers to the defaults
questions and shows what the outcome will be for each combination:

===================  ========== ===============================
Erase Configuration  Disk Scan  Outcome
===================  ========== ===============================
Y                    Y          IP address saved
                                NVRAM cleared.
                                Disk information is cleared.
                                S2A remains powered up.
                                Disk scan occurs.
                                IP address is restored.

Y                    N          IP address cleared
                                NVRAM cleared.
                                Disk information is cleared.
                                S2A remains powered up.

N                    N/A        IP address cleared,
                                NVRAM cleared.
                                Disk information is preserved.
                                S2A powers down.

Y                    Y          IP address saved,
                                NVRAM cleared.
                                Disk information is cleared.
                                S2A remains powered up.
                                Disk scan occurs.
                                IP address is restored.

Y                    N          IP address cleared,
                                NVRAM cleared.
                                Disk information is cleared.
                                S2A remains powered up.

N                    N/A        IP address cleared,
                                NVRAM cleared.
                                Disk information is preserved.
                                S2A powers down.
===================  ========== ===============================
