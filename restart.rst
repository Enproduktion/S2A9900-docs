=========
 RESTART
=========

RESTART  Performs a restart of the system.

This command will prepare the system to be restarted.  The system will
halt all I/O requests and save the data to the disks before restarting.
The restart process may take several minutes to complete.

DELAY=x
    Performs a restart of the unit in 'x' minutes.
    'x' may be any number between 0 and 255.

DUAL
    Will restart both this unit and the other unit.

KILL
    Stops a timed restart that is in progress.
