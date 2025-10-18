# Linux File Permissions

## What Are File Permissions?

In Linux, **file permissions** control **who can read, write, or execute** files and directories.  
Each file or folder has three levels of access:

| **Type** | **Description** |
|-----------|----------------|
| **Owner (User)** | The person who created the file. |
| **Group** | A set of users who share permissions. |
| **Others** | Everyone else on the system. |

## Types of Permissions

| **Permission** | **Symbol** | **Value** | **Description** |
|----------------|-------------|------------|------------------|
| **Read** | `r` | `4` | View file contents or list directory. |
| **Write** | `w` | `2` | Modify or delete file contents. |
| **Execute** | `x` | `1` | Run programs or enter directories. |

To **check file permissions**, use:

```bash
ls -l filename
```

Example Output:

```bash
-rwxr--r-- 1 user group 1234 Mar 28 10:00 myfile.sh
```

This means:

* User: `rwx` → read, write, execute
* Group: `r--` → read only
* Others: `r--` → read only

Changing Permissions with chmod

You can change permissions using symbolic mode (letters) or numeric mode (numbers).

### Symbolic Mode

Use u (user), g (group), o (others), or a (all).

| **Command** |	**Action**|
|----------------|-------------|
|`chmod u+x file` |Add execute for user
|`chmod g-w file` |Remove write for group
|`chmod o=r file` |Set read-only for others
|`chmod u=rwx,g=rx,o= file` |Give user full, group read/execute, others no access.|

Tip: Use symbolic mode when you want fine control without remembering numbers.

### Numeric (Octal) Mode

Each permission has a numeric value:

* Read = 4
* Write = 2
* Execute = 1

You add them up for each group (User / Group / Others).

|**Command**|**Meaning**|
|-----------|-----------|
|`chmod 755 file`|User (rwx), Group (r-x), Others (r-x)|
|`chmod 644 file`|User (rw-), Group (r--), Others (r--)|
|`chmod 700 file`|User (rwx), No access for others|

Example:

```bash
chmod 755 script.sh
```

Gives the user full rights, and read/execute for everyone else.

## Changing File Ownership with chown

Used to change the owner and group of a file or directory.

|**Command1**|**Function**|
|------------|------------|
|`chown newuser file`|Change file owner|
|`chown newuser:newgroup file`|Change both owner and group|
|`chown :newgroup file`|Change only group|
|`chown -R user:group directory/`|Change recursively for all files inside|

Tip: You’ll need sudo/root permissions to change ownership.

## Changing Group Ownership with chgrp

|**Command**|**Function**|
|-----------|------------|
|`chgrp newgroup file`|Change group of file|
|`chgrp -R newgroup folder/`|Change group recursively|

## Special Permissions

These advanced permissions give more control over how files are executed or managed.

|**Permission**|**Symbol**|**Function**|**Example Command**|
|--------------|----------|------------|-------------------|
|SetUID|`s` on user execute bit|Runs file as file owner, not the user executing it.|`chmod u+s file`|
|SetGID|`s` on group execute bit|Runs file as file’s group. Files in a SetGID directory inherit group ownership.|`chmod g+s dir/`|
|Sticky Bit|`t` on others execute bit|Used on shared directories — only the file’s owner can delete it.|`chmod +t /tmp`

Example:

* `/usr/bin/passwd` has **SetUID** — lets normal users update passwords.
* `/tmp` directory has a **Sticky Bit** — prevents users from deleting others’ files.

## Default Permissions with umask

umask defines default file permissions for new files and directories.

|**Command**|**Description**|
|-----------|---------------|
|`umask`|Show current umask value|
|`umask 022`|Set default permissions (755 for directories, 644 for files)|

How it works:
umask subtracts values from 777 (for directories) or 666 (for files).

|**umask**|**Directory Permissions**|**File Permissions**|
|---------|-------------------------|--------------------|
|`022`|755|644|
|`077`|700|600|

## Summary Table

|**Command**|**Purpose**|**Example**|
|-----------|-----------|-----------|
|`ls -l`|View permissions|`ls -l myfile.sh`|
|`chmod`|Change permissions|`chmod 755 file`|
|`chown`|Change file owner/group|`chown user:group file`|
|`chgrp`|Change only group|`chgrp devteam file`|
|`umask`|View or set default permissions|`umask 022`|

## In Short

> File permissions are essential for security and access control in Linux.
> Use chmod, chown, and chgrp to manage access, and umask to set smart defaults.
> Mastering these commands helps prevent accidental edits and improves system safety.