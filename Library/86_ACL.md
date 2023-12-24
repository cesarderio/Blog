# Extended ACL File System Permissions in Linux

Access Control Lists (ACLs) in Linux offer a more granular approach to managing file and directory permissions, extending beyond the traditional owner-group-others model. This guide dives into the world of ACLs, showcasing their flexibility and utility in complex permission scenarios.

## Introduction to ACLs

ACLs provide an advanced level of permission control, allowing specific permissions to be set for multiple individual users and groups on the same files and directories.

### Flexibility and Control

With ACLs, Linux administrators can precisely define who can access specific files or directories and what actions they can perform, surpassing the limitations of standard permissions.

## Setting Up ACLs

Before diving into ACLs, ensure that your Linux distribution includes the necessary tools.

1. **Installation**:
   - Install the ACL package if it's not included by default: `sudo apt install acl`.

2. **Key ACL Commands**:
   - `setfacl`: To set or modify ACL permissions.
   - `getfacl`: To view existing ACL permissions.

## Using ACL Commands

1. **Viewing ACLs with `getfacl`**:
   - Retrieve ACLs for a file or directory: `getfacl file1.txt`.

2. **Modifying ACLs with `setfacl`**:
   - Add user permissions: `setfacl -m u:mbishop:rwx file1.txt`.
   - Add group permissions: `setfacl -m g:eastadmins:rw file1.txt`.
   - Apply permissions recursively: `setfacl -R -m o:r /dir1`.

3. **Backup and Restore ACLs**:
   - Backup ACLs: `getfacl -R /dir1 > aclpermissionsbackup.txt`.
   - Restore ACLs: `setfacl --restore=aclpermissionsbackup.txt`.

## Understanding ACL Entries

- **Mask Entry**: Serves as a ceiling for permissions, setting the maximum allowed permissions for users and groups.

## Example Scenario: `budget1.txt`

In this scenario, `budget1.txt` displays a `+` sign, indicating that extended ACLs are in effect. Using `getfacl budget1.txt`, we can see:

- Owner (`lbrenner`) permissions.
- User `mbishop` with specific permissions.
- Group `westadmins` with their permissions.
- A mask entry that determines the effective permissions.

## Summary

ACLs in Linux provide a sophisticated mechanism for managing permissions, essential for complex environments where standard permissions fall short. They offer administrators precise control over who can access what, allowing for a more secure and compliant file system structure.
