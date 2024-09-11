README: Running the Disk Extension and Volume Setup Script Overview 
 
This script performs the following tasks:

Creates a physical volume on a new disk.
Sets up a volume group.
Creates a logical volume.
Formats the logical volume with a specified file system.
Creates a mount point and mounts the logical volume.
Updates /etc/fstab to ensure the volume mounts automatically at startup.
Important: Ensure you review and customize the script before running it to match your environment and requirements.

Prerequisites
Linux Distribution: The script is designed for use on Linux systems with LVM (Logical Volume Manager) support.
Privileges: You need sudo privileges to run this script.
Dependencies: Ensure lvm2 and e2fsprogs (for ext4) or relevant packages for other file systems are installed.
Customization
Disk Identifier (DISK): Replace /dev/sdX with the actual identifier of your new disk (e.g., /dev/sdb).

Volume Group (VOLUME_GROUP): Choose a name for your volume group. This is where your logical volumes will reside.

Logical Volume (LOGICAL_VOLUME): Name the logical volume you will create.

Mount Point (MOUNT_POINT): Specify the directory where you want to mount the logical volume.

File System (FILE_SYSTEM): Set the desired file system type (e.g., ext4, xfs). Make sure to have the relevant tools installed.

How to Use the Script
Save the Script:

Save the provided script content to a file named extend_disk.sh.

Make the Script Executable:

bash
Copy code
chmod +x extend_disk.sh
Run the Script:

Execute the script with sudo:

bash
Copy code
sudo ./extend_disk.sh
Verify the Setup:

Physical Volume: Check with pvdisplay.
Volume Group: Check with vgdisplay.
Logical Volume: Check with lvdisplay.
Mount Point: Verify with df -h or lsblk.
Troubleshooting
Disk Not Found: Ensure the disk identifier is correct and the disk is properly connected.
Formatting Issues: Verify the file system type and ensure necessary utilities are installed.
Mounting Issues: Check /etc/fstab for errors and ensure the mount point directory exists.
For further assistance, consult your system administrator or refer to the LVM documentation for your Linux distribution.