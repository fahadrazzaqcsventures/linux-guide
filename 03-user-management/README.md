# Linux User Management Guide

## Overview

Linux is a **multi-user operating system**, meaning multiple people can use it at the same time.  
User management is essential for **security**, **access control**, and **system stability**.

Linux user management controls who can log in, what they can do, and what files they can access.
Mastering these commands is essential for any system administrator or DevOps engineer.

This guide explains the most commonly used commands to **create, modify, and delete users** and **manage groups and permissions** in Linux.

## Important Files

| File | Description |
|------|--------------|
| `/etc/passwd` | Stores user account details (username, UID, shell, etc.). |
| `/etc/shadow` | Stores **encrypted passwords** and password aging info. |
| `/etc/group` | Stores **group membership** details. |
| `/etc/gshadow` | Secure version of group file. |

## Creating Users

### Using `useradd` (standard command)

```bash
useradd username           # Create user (no home dir)
useradd -m username        # Create user with home directory
useradd -s /bin/bash user  # Create user with a specific shell
```

Note: Use `passwd` username to set a password after creating a user.

Using `adduser` (Debian/Ubuntu)

```bash
adduser username
```

Interactive command — automatically creates home, sets password, and prompts for details.

## Managing Passwords

### Set or Change Password

```bash
passwd username
```

### Enforce Password Policies

```bash
chage -M 90 username   # Force password change after 90 days
passwd -l username     # Lock user account
passwd -u username     # Unlock user account
```

## Modifying Users

```bash
usermod -l new_username old_username   # Change username
usermod -d /new/home -m username       # Move home directory
usermod -s /bin/zsh username           # Change shell
```

Tip: Use ```id username``` to see user and group IDs.

## Deleting Users

```bash
userdel username       # Delete user only
userdel -r username    # Delete user and their home directory
```

Warning: The `-r` option permanently deletes the user’s files.

## Working with Groups

```bash
groupadd groupname                     # Create group
usermod -aG groupname username         # Add user to group
usermod -g newgroup username           # Change primary group
groups username                        # View group memberships
```

Tip: Always use `-aG` (append).

Without `-a` existing groups are removed!

## Sudo & Privileges

### Add User to Sudo Group

For Debian/Ubuntu:

```bash
usermod -aG sudo username
```

For RHEL/CentOS:

```bash
usermod -aG wheel username
```

### Grant Specific Sudo Permissions

Edit sudoers file safely:

```bash
visudo
```

Add line:

```bash
username ALL=(ALL) NOPASSWD: /path/to/command
```

Always use `visudo` it checks syntax and prevents lockouts.

## Quick Reference Table

| **Task** | **Command** | **Description** |
|-----------|--------------|-----------------|
| Create user | `useradd username` | Create a new user (no home directory). |
| Create user with home directory | `useradd -m username` | Creates a home folder `/home/username`. |
| Create user with specific shell | `useradd -s /bin/bash username` | Sets default shell for the new user. |
| Interactive user creation | `adduser username` | Friendly interactive user creation (Debian/Ubuntu). |
| Set or change password | `passwd username` | Sets or updates user password. |
| Force password change after 90 days | `chage -M 90 username` | Enforces password expiry policy. |
| Lock account | `passwd -l username` | Disables login for the user. |
| Unlock account | `passwd -u username` | Re-enables locked user account. |
| Rename user | `usermod -l new_username old_username` | Changes username. |
| Change home directory | `usermod -d /new/home -m username` | Moves user to a new home directory. |
| Change login shell | `usermod -s /bin/zsh username` | Updates user’s default shell. |
| Delete user (keep home) | `userdel username` | Removes user but keeps files. |
| Delete user + home directory | `userdel -r username` | Removes user and their home directory. |
| Create group | `groupadd groupname` | Creates a new group. |
| Add user to group | `usermod -aG groupname username` | Adds user to a supplementary group. |
| Change primary group | `usermod -g newgroup username` | Sets new primary group for user. |
| Show user’s groups | `groups username` | Lists all groups the user belongs to. |
| Add user to sudo (Debian/Ubuntu) | `usermod -aG sudo username` | Grants sudo privileges. |
| Add user to wheel (RHEL/CentOS) | `usermod -aG wheel username` | Grants admin privileges. |
| Edit sudoers file | `visudo` | Safely modify sudo permissions. |
| Show account info | `getent passwd username` | Displays user’s info from system database. |
| Show password aging | `chage -l username` | Shows password expiry details. |
| Show group info | `getent group groupname` | Displays group entry details. |
