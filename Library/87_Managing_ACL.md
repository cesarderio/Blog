# Managing Extended ACL Linux File System Permissions

Extended Access Control Lists (ACLs) in Linux enhance the standard permission model, allowing for more nuanced control over file and directory access. This guide explains how to manage these extended permissions effectively.

## Preparing for ACL Management

Before delving into ACLs, it's essential to ensure that your Linux system supports and includes ACL tools.

1. **Check for ACL Support**: Verify whether your Linux distribution supports ACLs, as they may not be included by default.
2. **Install ACL Package**: On Ubuntu Server, for example, install the ACL package using `sudo apt install acl`.

## Using the `getfacl` Command

`getfacl` is used to display the ACLs of a file or directory, providing insights into both standard and extended permissions.

- **Usage Example**: To view the ACLs for `budget1.txt`, use `getfacl budget1.txt`. This command will display permissions for the owner, group, and any other specified entities.

## Using the `setfacl` Command

`setfacl` allows you to modify or set the ACLs of a file or directory, extending permissions beyond the owner, group, and others.

- **Modifying User Permissions**: For instance, `sudo setfacl -m u:mbishop:rw budget1.txt` grants user `mbishop` read and write permissions on `budget1.txt`.
- **Modifying Group Permissions**: Similarly, `sudo setfacl -m g:westadmins:r budget1.txt` grants the group `westadmins` read permission on the same file.

## Practical Example

Let's walk through a common scenario of applying ACLs to a file:

1. **Navigate to the Directory**: For example, `cd budgets` to access the relevant folder.
2. **View Current Permissions**: Use `ll` to list the existing permissions for `budget1.txt`.
3. **Applying ACLs**: Use `setfacl` to assign specific permissions to users or groups. A `+` sign in the permissions output indicates extended ACLs are in place.

## Summary

Extended ACLs in Linux are a powerful tool for detailed permission management. They are particularly useful in complex scenarios where the standard Linux permissions model falls short. By utilizing `getfacl` and `setfacl`, administrators can ensure precise access control, tailoring permissions to specific requirements and enhancing system security.
