## **Linux Systems Administration**

Make a copy of this document to work in, and then for each step, add the solution commands below the prompt. Save and submit this completed file as your Challenge deliverable.


### **Step 1: Ensure/Double Check Permissions on Sensitive Files**



1. Permissions on `/etc/shadow` should allow only `root` read and write access.
    1. Command to inspect permissions:

        `ls -l /etc/shadow`



    2. Command to set permissions (if needed):

        `sudo chmod 600 /etc/shadow`


2. Permissions on `/etc/gshadow` should allow only `root` read and write access.
    3. Command to inspect permissions:

        `ls -l /etc/gshadow`


    4. Command to set permissions (if needed):

        sudo chmod u=rw,g=,o= /etc/gshadow`


3. Permissions on `/etc/group` should allow `root` read and write access, and allow everyone else read access only.
    5. Command to inspect permissions:

        `ls -l /etc/group`


    6. Command to set permissions (if needed):

        `sudo chmod u=rw,g=r,o=r /etc/group`


4. Permissions on `/etc/passwd` should allow `root` read and write access, and allow everyone else read access only.
    7. Command to inspect permissions:

        `ls -l /etc/passwd`


    8. Command to set permissions (if needed):

        `sudo chmod u=rw,g=r,o=r /etc/passwd`




### **Step 2: Create User Accounts**



1. Add user accounts for `sam`, `joe`, `amy`, `sara`, and `admin` with the `useradd` command.
    1. Command to add each user account (include all five users):

        `sudo adduser sam`
        `sudo adduser joe`
        `sudo adduser amy`
        `sudo adduser sara`
        `sudo adduser admin`


2. Ensure that only the `admin` has general sudo access.
    2. Command to add `admin` to the sudo group:

        `sudo usermod -g sudo admin`


### **Step 3: Create User Group and Collaborative Folder**



1. Add an `engineers` group to the system.
    1. Command to add group:

        `addgroup engineers`


2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.
    2. Command to add users to `engineers` group (include all four users):

        `sudo usermod -g engineers sam`
        `sudo usermod -g engineers joe`
        `sudo usermod -g engineers amy`
        `sudo usermod -g engineers sara`


3. Create a shared folder for this group at `/home/engineers`.
    3. Command to create the shared folder:

        `sudo mkdir /home/engineers`


4. Change ownership on the new engineers’ shared folder to the `engineers` group.
    4. Command to change ownership of engineers’ shared folder to `engineers` group:

        `sudo chgrp -R engineers /home/engineers`



### Step 4: Lynis Auditing



1. Command to install Lynis:

    `sudo git clone https://github.com/CISOfy/lynis`


2. Command to view documentation and instructions:

    `lynis --help`


3. Command to run an audit:

    `lynis audit system`


4. Provide a report from the Lynis output with recommendations for hardening the system.
    1. Screenshot of report output: 



### Bonus


1. Command to install chkrootkit:

    `sudo apt install -y chkrootkit`


2. Command to view documentation and instructions:

    `chkrootkit --help`


3. Command to run expert mode:

    `sudo chkrootkit -x`


4. Provide a report from the chrootkit output with recommendations for hardening the system.
    1. Screenshot of end of sample output: 
