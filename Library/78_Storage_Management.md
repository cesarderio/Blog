# Linux Storage Command Line Management Tools

Managing storage is a fundamental aspect of Linux system administration. This blog post provides a detailed overview of command-line tools for storage management in Linux. Most of these tools require root access, so ensure you use `sudo` for administrative privileges.

## Common Linux Storage Management Tools

### Tool Descriptions and Usage

- **lsblk**
  - **Description**: Lists block storage devices.
  - **Usage**: `lsblk --scsi` to display SCSI devices.

- **fdisk**
  - **Description**: Manages disk partitions.
  - **Usage**: `fdisk -l` lists partitions; commonly used with MBR disks.

- **mkfs**
  - **Description**: Formats a partition with a specified filesystem.
  - **Usage**: `mkfs -t [type] [device]`, for example, `mkfs -t ext4 /dev/sda1`.

- **parted**
  - **Description**: Manages disk partitions, including resizing.
  - **Usage**: Supports MBR and GPT; can resize partitions without data loss.

- **partprobe**
  - **Description**: Refreshes the kernel's partition table.
  - **Usage**: Useful after partition table changes, avoiding a reboot.

### Additional Important Tools

- **mount**
  - **Description**: Mounts a filesystem to a directory.
  - **Usage**: Access filesystem contents.

- **umount**
  - **Description**: Unmounts a filesystem.
  - **Usage**: Prevents data corruption by ensuring safe unmounting.

- **df**
  - **Description**: Shows disk space usage.
  - **Usage**: Monitors free space on filesystems.

- **du**
  - **Description**: Estimates file and directory space usage.
  - **Usage**: Identifies space consumption by files and directories.

## Creating Linux File Systems

### Tools and Commands for File System Management

1. **Disks Tool (GUI)**
   - **Description**: Manages disks and partitions graphically.
   - **Usage**: Format, resize, check, and mount filesystems.

2. **fdisk -l**
   - **Usage**: Lists filesystems on all disks.
   - **Example**: `sudo fdisk -l /dev/sdb` for specific disk details.

3. **mkfs**
   - **Command**: `sudo mkfs -t [type] [device]`.
   - **Example**: `sudo mkfs -t ext4 /dev/sdb1` for formatting with ext4.

4. **Creating and Mounting File Systems**
   - **Mount Point Creation**: `sudo mkdir /path/to/mount-point`.
   - **Mounting**: `sudo mount [device] [mount-point]`.

5. **Verifying Mounts**
   - **Command**: `mount | grep [device]`.
   - **Example**: `sudo mount | grep sdb1`.

### Additional Considerations

- **File System Check (fsck)**
  - **Usage**: Check and repair filesystem inconsistencies.
  - **Command**: `sudo fsck /dev/sdb1`.

- **Unmounting File Systems**
  - **Command**: `sudo umount [mount-point]`.

- **Automounting File Systems**
  - **Method**: Edit `/etc/fstab` for boot-time mounting.

- **Choosing File System Type**
  - **Consideration**: Match the file system type (ext4, XFS, Btrfs) with your performance and compatibility needs.

## Conclusion

Linux offers a robust set of command-line tools for comprehensive storage management. Whether you're partitioning drives, formatting filesystems, or simply checking disk space, these tools provide the control and flexibility needed for effective system administration.

Do you have any favorite storage management commands or tips? Share your experiences and best practices in the comments!
