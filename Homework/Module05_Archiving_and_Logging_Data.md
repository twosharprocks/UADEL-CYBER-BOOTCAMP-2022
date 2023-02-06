## Archiving and Logging Data

### Step 1: Create, Extract, Compress, and Manage tar Backup Archives


1. Command to **extract** the `TarDocs.tar` archive to the current directory:

    `tar xvf TarDocs.tar `


2. Command to **create** the Javaless_Docs.tar archive from the TarDocs/ directory, while excluding the `TarDocs/Documents/Java` directory:

    `tar --exclude='TarDocs/Documents/Java' -cvf Javaless_Docs.tar TarDocs/ `


3. Command to ensure `Java` is not in the new `Javaless_Docs.tar` archive:

    `tar tvf Javaless_Docs.tar | grep Java`


#### Bonus




4. Command to create an incremental archive called `logs_backup_tar.gz` with only changed files to `snapshot.file` for the `/var/log` directory:

    `[Enter answer here]`




#### Critical Analysis Question



5. Why wouldn't you use the options `-x` and` -c` at the same time with `tar`?

`‘-x’ is the option used to extract a .tar file while ‘-c’ is the option used to create a tar file`


### Step 2: Create, Manage, and Automate Cron Jobs



1. Cron job for backing up the `/var/log/auth.log` file:

    `0 6 * * 3 tar zcf /auth_backup.tgz /var/log/auth.log`




### Step 3: Write Basic Bash Scripts



1. Brace expansion command to create the four subdirectories:

    `mkdir -p backups/{freemem,diskuse,openlist,freedisk}`


2. Paste your `system.sh` script edits:

    `#!/bin/bash`

#Free memory to free_mem.txt
`free -h > ~/backups/freemem/free_mem.txt`

#Disk usage to disk_usage.txt
`du -h > ~/backups/diskuse/disk_usage.txt`

#List open files to open_list.txt
`lsof -h > ~/backups/openlist/open_list.txt`

#Disc space to free_disk.txt
`df -h > ~/backups/freedisk/free_disk.txt`


3. Command to make the `system.sh` script executable:

    `sudo chmod +x system.sh`




#### Optional



4. Commands to test the script and confirm its execution:

    `sudo ./system.sh`



### Step 4. Manage Log File Sizes



1. Run `sudo nano /etc/logrotate.conf` to edit the `logrotate` configuration file. 

    Configure a log rotation scheme that backs up authentication messages to the `/var/log/auth.log`. 

    1. Add your config file edits:

`
`/var/log/auth.log {`
   ` missingok`
   ` weekly`
   ` rotate 7`
   ` delaycompress`
   ` notifempty`
`}`
