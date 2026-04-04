# Windows CMD – Directories & Files Commands

## Navigation & Listing

### cd
Display or change the current directory.

### chdir
Same as `cd`, used to change the working directory.

### dir
List files and directories in the current path.

### tree
Display directory structure.

### tree /F
Display directory structure including files.

---

## Creating Directories

### md
Create a new directory.

### mkdir
Create a new directory (same as `md`).

---

## Deleting Directories

### rd
Remove an empty directory.

### rmdir
Remove an empty directory (same as `rd`).

### rd /S
Remove a directory and all its contents.

---

## Moving Directories

### move
Move a file or directory from one location to another.

---

## Copying Files & Directories

### xcopy
Copy files and directories.

### xcopy source destination /E
Copy all files and subdirectories, including empty ones.

### xcopy /K
Preserve file attributes (e.g., read-only, hidden).

---

## Advanced Copying

### robocopy
Advanced file copy tool that preserves metadata (timestamps, ownership, ACLs, attributes).

### robocopy source destination
Copy files/directories with full metadata support.

### robocopy /MIR
Mirror source to destination (can delete extra files in destination).

### robocopy /L
Preview command without executing (dry run).

### robocopy /A-:SH
Remove system and hidden attributes from copied files.

---

## Viewing File Contents

### more
Display output one page at a time.

### more filename
View file contents page by page.

### more /S
Remove extra blank lines when displaying output.

### command | more
Pipe output to display it one screen at a time.

---

### type
Display contents of a file.

### type file1 file2
Display multiple files.

### type file1 >> file2
Append contents of one file to another.

---

### openfiles
Display open files and the users accessing them (requires admin privileges).

---

## Creating & Modifying Files

### echo text > file
Create a file with content.

### echo text >> file
Append text to an existing file.

---

### fsutil file createNew filename size
Create a new file with a specified size.

---

### ren
Rename a file.

### rename
Rename a file (same as `ren`).
