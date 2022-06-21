# File System
Everything in Linux is a file. Things like configurations, network settings, devices all are files.

*   /bin - contains command binaries (soft link to /usr/bin)
*   /sbin - (super bin) contains root command binaries (soft linked to /usr/sbin)
*   /usr
    *   ./bin 
    *   ./sbin
    *   ./local - stores local (user defined) binaries. same structure as /usr
*   /boot - files used during boot 
*   /var - log files 
*   /tmp - temporary files 
*   /lib - shared libraries 
*   /root - same contents as /home/<root\_user>
*   /dev - lists all devices
*   /etc - contains config files and other misc application files
*   /mnt - has drives that are manually mounted 
*   /mount - has drives that are mounted automatically like USB