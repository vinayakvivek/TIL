- To erase a disk (even unreadable) in Mac OS Extended Journaled (JHFS+) format
  ```bash
  diskutil eraseDisk JHFS+ <name> <disk_location(/dev/*)>
  ```
- To format a disk to FAT32 
  ```bash
  diskutil eraseDisk FAT32 NAME MBRFormat /dev/disk1
  ```
