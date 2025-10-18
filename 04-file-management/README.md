# Linux File Management Commands

Linux provides powerful commands to **create**, **view**, **edit**, **move**, and **delete** files and directories directly from the terminal.  
Below is a simple guide with examples and short explanations.

## File & Directory Management

| **Command** | **Description / Function** | **Example** |
|--------------|-----------------------------|--------------|
| `touch`| Creates a new file | `touch file.html`|
| `ls` | Lists files and directories in the current folder. | `ls -l` → list in long format with permissions, owner, and size |
| `cd /path/to/dir` | Changes the current working directory. | `cd /home/fahad/Documents` |
| `pwd` | Prints the current working directory. | `pwd` |
| `mkdir new_folder` | Creates a new directory. | `mkdir projects` |
| `rmdir empty_folder` | Removes an **empty** directory. | `rmdir old_dir` |
| `rm file.txt` | Deletes a file. | `rm notes.txt` |
| `rm -r folder` | Deletes a directory **and all its contents**. | `rm -r temp_files` |
| `cp file1.txt file2.txt` | Copies one file to another. | `cp index.html backup.html` |
| `cp -r dir1 dir2` | Copies directories **recursively** (with all files inside). | `cp -r project backup_project` |
| `mv old_name new_name` | Moves or renames a file/directory. | `mv old.txt new.txt` or `mv file.txt /home/user/Desktop/` |

**Tip:** Use the `-i` flag (interactive) with `rm` or `cp` to ask before overwriting or deleting files.  
Example: `rm -i file.txt`

## File Viewing & Editing

| **Command** | **Description / Function** | **Example** |
|--------------|-----------------------------|--------------|
| `cat file.txt` | Displays file content. | `cat notes.txt` |
| `tac file.txt` | Displays file content **in reverse order** (last line first). | `tac log.txt` |
| `less file.txt` | View large files **one screen at a time** (scroll up/down with arrows). | `less /var/log/syslog` |
| `more file.txt` | Similar to `less`, but scrolls **forward only**. | `more output.txt` |
| `head -n 10 file.txt` | Shows the **first 10 lines** of a file. | `head -n 10 data.txt` |
| `tail -n 10 file.txt` | Shows the **last 10 lines** of a file. | `tail -n 10 log.txt` |
| `nano file.txt` | Opens a simple terminal-based text editor. | `nano notes.txt` |
| `vi file.txt` | Opens the **Vi/Vim** editor (powerful and advanced). | `vi script.sh` |
| `echo 'Hello' > file.txt` | Writes text to a file (**overwrites** existing content). | `echo 'Welcome to Linux!' > info.txt` |
| `echo 'Hello' >> file.txt` | **Appends** text to the end of a file. | `echo 'New line added' >> info.txt` |

**Tip:**  
Use `tail -f logfile.log` to **monitor logs in real-time** — useful for debugging.

## Quick Summary

| **Purpose** | **Useful Commands** |
|--------------|---------------------|
| Navigate directories | `cd`, `pwd`, `ls` |
| Create or remove | `mkdir`, `rmdir`, `rm` |
| Copy or move | `cp`, `mv` |
| View content | `cat`, `less`, `head`, `tail` |
| Edit text files | `nano`, `vi`, `echo` |

## In Short

> Linux file management is done through simple yet powerful terminal commands.  
> Mastering these lets you quickly navigate, organize, and modify files — without needing a GUI!
