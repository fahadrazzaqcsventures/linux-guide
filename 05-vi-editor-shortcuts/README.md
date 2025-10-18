# VI Editor Commands and Shortcuts

The **Vi (or Vim)** editor is a powerful text editor built into almost all Linux systems.  
It works in **different modes**, allowing you to **navigate, edit, and manage files** directly from the terminal.

## Modes in VI Editor

| **Mode** | **Purpose** | **How to Enter / Exit** |
|-----------|--------------|--------------------------|
| **Normal Mode** | Default mode for navigation and commands. | Press `Esc` to return here from any mode. |
| **Insert Mode** | Used for typing and editing text. | Press `i`, `a`, `o` to enter → `Esc` to exit. |
| **Command Mode** | Used for saving, quitting, and searching. | Type `:` in Normal mode. |

**Tip:** You always start in **Normal Mode** when you open a file in `vi`.

## Basic Navigation

| **Command** | **Function** |
|--------------|---------------|
| `h` | Move left |
| `l` | Move right |
| `j` | Move down |
| `k` | Move up |
| `0` | Jump to the beginning of the line |
| `^` | Move to first non-blank character |
| `$` | Move to the end of the line |
| `w` | Jump forward one word |
| `b` | Jump backward one word |
| `gg` | Go to the top of the file |
| `G` | Go to the bottom of the file |
| `:n` | Go to line number `n` |

**Example:**  
`:15` → takes you directly to line 15.

## Insert Mode Shortcuts

| **Command** | **Function** |
|--------------|---------------|
| `i` | Insert text **before** the cursor |
| `I` | Insert at **start of line** |
| `a` | Append text **after** the cursor |
| `A` | Append at **end of line** |
| `o` | Open a **new line below** |
| `O` | Open a **new line above** |
| `Esc` | Exit insert mode and return to normal mode |

**Tip:** Use `a` and `A` often when editing — they let you continue writing without repositioning the cursor.

## Editing and Deleting Text

| **Command** | **Function** |
|--------------|---------------|
| `x` | Delete character under cursor |
| `X` | Delete character before cursor |
| `dw` | Delete a word |
| `dd` | Delete current line |
| `d$` or `D` | Delete from cursor to end of line |
| `d0` | Delete from cursor to start of line |
| `u` | Undo last action |
| `Ctrl + r` | Redo last undone action |
| `yy` | Copy (yank) current line |
| `yw` | Copy (yank) a word |
| `p` | Paste **after** cursor |
| `P` | Paste **before** cursor |

**Example:**  
Type `3dd` → deletes 3 lines at once.  
Type `5yy` → copies 5 lines.

## Search and Replace

| **Command** | **Function** |
|--------------|---------------|
| `/pattern` | Search **forward** for a word or pattern |
| `?pattern` | Search **backward** |
| `n` | Repeat search **in same direction** |
| `N` | Repeat search **in opposite direction** |
| `:%s/old/new/g` | Replace all occurrences of "old" with "new" (entire file) |
| `:s/old/new/g` | Replace all occurrences in **current line only** |

**Example:**  
`:%s/error/success/g` → replaces *“error”* with *“success”* everywhere.

## Working with Multiple Files

| **Command** | **Function** |
|--------------|---------------|
| `:e filename` | Open a new file in the same window |
| `:w` | Save (write) file |
| `:wq` | Save and quit |
| `:q!` | Quit **without saving** |
| `:split filename` | Split screen **horizontally** to open another file |
| `:vsplit filename` | Split screen **vertically** |
| `Ctrl + w + w` | Switch between split windows |

**Example:**  
Use `:split main.c` to edit another file without closing the current one.

## Quick Summary

| **Purpose** | **Key Commands** |
|--------------|------------------|
| Navigation | `h`, `j`, `k`, `l`, `gg`, `G`, `:n` |
| Editing | `i`, `a`, `o`, `dd`, `yy`, `p` |
| Search & Replace | `/pattern`, `:%s/old/new/g` |
| Save & Quit | `:w`, `:wq`, `:q!` |
| Split Windows | `:split`, `:vsplit`, `Ctrl + w + w` |

## Pro Tips

- Always press `Esc` first to ensure you’re in **Normal Mode** before running commands.  
- Use `u` to undo mistakes — it’s your safety net.  
- For beginners, start with `i`, `Esc`, `:wq`, and `dd` — they cover most tasks.  
- To open Vi directly with a file:  

  ```bash
  vi filename.txt
  ```
