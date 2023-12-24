# Mounting File Systems in Linux: Local and Cloud-based Storage

In Linux, mounting file systems is a key operation for managing both local and remote storage. This guide covers the steps for mounting local Linux file systems and connecting to remote cloud-based storage, specifically Microsoft Azure.

## Mounting Local Linux File Systems

### Initial Steps and Disk Partitioning

1. **Viewing System Partitions**
   - `sudo fdisk -l` displays partition layout.

2. **Creating a New Partition**
   - Use `sudo fdisk /dev/sdc` to create a new partition on `/dev/sdc`.

3. **Verifying the New Partition**
   - `sudo fdisk -l /dev/sdc` to confirm creation.

### Formatting and Mounting the Partition

1. **Formatting**
   - `sudo mkfs -t ext4 /dev/sdc1` formats the partition with ext4.

2. **Creating a Mount Point**
   - `sudo mkdir /data2` for a new directory.

3. **Mounting the File System**
   - `sudo mount /dev/sdc1 /data2` attaches the partition.

4. **Verifying the Mount**
   - `sudo mount | grep sdc` to check the mount.

### Setting Up Persistence

1. **Editing fstab**
   - Add `/dev/sdc1 /data2 ext4 rw 0 2` to `/etc/fstab`.

2. **Rebooting**
   - `sudo init 6` to apply changes.

3. **Verifying Automatic Mounting**
   - Post-reboot, confirm auto-mount with `sudo mount | grep sdc`.

4. **Unmounting and Manual Mounting**
   - `sudo umount /data2` to unmount.
   - `sudo mount /dev/sdc1 /data2` for manual mounting.

### Additional Notes

- Handle `/etc/fstab` with care to avoid boot issues.
- Back up data before partitioning or formatting drives.

## Mounting Remote Cloud-based File Systems

### Managing Azure Cloud File Systems

#### Setting Up a Shared Folder in Microsoft Azure

1. **Creating a Storage Account**
   - Create a new storage account in Azure, specifying details like resource group and region.

2. **Creating a File Share**
   - In the storage account, add a file share (e.g., `projects`).

3. **Uploading Files**
   - Add directories and files within the file share.

#### Connecting to the Shared Folder from Linux

1. **Generating Mount Script in Azure**
   - Generate a Linux mount script in Azure for the `projects` file share.

2. **Executing the Script on Linux**
   - Run the script on your Linux host to establish the SMB/CIFS connection.

3. **Verifying and Persisting the Mount**
   - Confirm mount details in `/etc/fstab` and verify with `ls /mnt/projects`.

#### Summary

- This process enables Linux users to access Azure cloud storage directly.
- The Azure portal simplifies script generation for SMB/CIFS connections.
- Ensure persistent mounts with correct fstab entries.

## Conclusion

Understanding how to mount local and remote file systems in Linux is crucial for effective data management. Whether dealing with local storage or integrating cloud solutions like Azure, these steps provide a roadmap for secure and efficient storage access.

Do you have tips or experiences to share about mounting file systems in Linux? Let's discuss in the comments below!
