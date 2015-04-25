
asMake7zBak
===========

A full-disk backup experiment.
Uses 7zr to compress dd's output.

### Requirements

- bash
- dd
- 7zr

### Usage

    asMake7zBak <disk> <file> [RUN]

- The extension '7z' is automatically added to the file name.
- Until "RUN" is added to the end of the command line, nothing will happen.


E.g.
 
    asMake7zBak /dev/sda /mnt/BACKUP/Bak_2015_04
    asMake7zBak /dev/sda /mnt/BACKUP/Bak_2015_04.7z

Might show:

    #####
    # DO NOT BACKUP LIVE SYSTEMS, BOOT WITH STICK/CD/DVD
    #
    # asMake7zBak <device_to_backup> <7z_file_to_save>
    # asMake7zBak /dev/sda /mnt/BACKUP/Bak_2015_04_01
    #
    # Safety First:
    # Nothing will actually happen until you add a 'RUN'
    # to the end of the command line...
    #####
    
    NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
    sda      8:0    0 953,9G  0 disk 
    ├─sda1   8:1    0 923,6G  0 part /
    ├─sda2   8:2    0     1K  0 part 
    └─sda5   8:5    0     8G  0 part [SWAP]
    sdb      8:16   0 931,5G  0 disk 
    └─sdb1   8:17   0 931,5G  0 part /mnt/BACKUP
    sr0     11:0    1  1024M  0 rom  
    
    +-----
    | IS THIS WHAT YOU WANT?
    | sudo dd if=/dev/sda bs=1024k | 7zr a -mx2 -si /mnt/BACKUP/MyBackup.7z
    +-----

Check the output and (if happy) append a RUN to the end of the command line
to start the backup process.

During the task is running, a subshell command show the current size
of the backup file via 'ls':

    0%-rw-rw-r-- 1 askr askr 6,7M Apr 25 22:00 /mnt/BACKUP/MyBackup.7z
    0%-rw-rw-r-- 1 askr askr 12M Apr 25 22:00 /mnt/BACKUP/MyBackup.7z
    0%-rw-rw-r-- 1 askr askr 19M Apr 25 22:00 /mnt/BACKUP/MyBackup.7z
    0%-rw-rw-r-- 1 askr askr 26M Apr 25 22:00 /mnt/BACKUP/MyBackup.7z
    0%-rw-rw-r-- 1 askr askr 33M Apr 25 22:00 /mnt/BACKUP/MyBackup.7z
    0%-rw-rw-r-- 1 askr askr 38M Apr 25 22:00 /mnt/BACKUP/MyBackup.7z
                        

### Notes

 - Do not backup mounted systems.  
   Boot from an USB stick/drive or a CD/DVD.
 - ...

### TODO

 - check permissions
 - check drive mounted
 - ...


---
Good luck  
FMMT666(ASkr)
