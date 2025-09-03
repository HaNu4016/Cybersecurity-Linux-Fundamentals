Day 2 – Linux File Permissions (r, w, x)

1. What are File Permissions?
  File permissions define who can read, write, or execute a file or directory in Linux.
  Every file has permissions for three categories:

User (Owner) → file ka malik
Group → file ke group members
Others → baaki sab users

2. Purpose of Permissions
  Protect files from unauthorized access.
  Allow multi-user collaboration while keeping control.
  Prevent accidental modification or deletion of system files.

   Permission Types
     r (read): View contents of file / list directory.
     w (write): Modify file / add-delete files inside directory.
     x (execute): Run file as program / enter directory.

Example (File vs Directory):
  r on file → can open file.
  r on directory → can list files inside.
  x on directory → can enter that directory.

4. Characteristics of Permissions 
   Applied separately for User, Group, Others.
   Can be changed using chmod command.
   Represented in symbolic (u+r, g-w) or numeric (755) mode.

5. How Permissions Work (ls -l output)

Example:
        ls -l file.txt
        -rwxr-xr--


Breakdown:

- → file type
rwx → User (owner) permissions
r-x → Group permissions
r-- → Others permissions

6. Commands for Permissions
View permissions:
   ls -l filename

Change permissions (numeric mode):
chmod 755 file.txt
7 = rwx
5 = r-x
5 = r-x

Change permissions (symbolic mode):
chmod u+x script.sh   # add execute for user
chmod g-w file.txt    # remove write for group
chmod o+r notes.txt   # add read for others

7. Examples
chmod 644 file.txt → User: rw-, Group: r--, Others: r--
chmod 700 secret.txt → Only owner can read/write/execute
chmod 770 project/ → Owner + Group full access, Others denied

8. Practice Task
Create a file test.txt.
Give read + write access to owner only.
Give read only access to group.
Give no access to others.
Verify with ls -l test.txt.

9. 10 Important Questions with Answers

Q: What are the three types of permissions in Linux?
A: Read, Write, Execute.

Q: Command to see file permissions?
A: ls -l

Q: Difference between symbolic and numeric mode in chmod?
A: Symbolic = u+r, g-w (human-readable), Numeric = 755 (binary values).

Q: What does chmod 777 file mean?
A: User, Group, Others → full read, write, execute.

Q: What does chmod 000 file mean?
A: No one can access the file.

Q: Permission value of rw-r--r--?
A: 644

Q: What does x permission on a directory mean?
A: You can enter the directory.

Q: Command to remove write permission from group?
A: chmod g-w filename

Q: If a file has rw- --- ---, who can access it?
A: Only the owner.

Q: Which command gives execute permission to all?
A: chmod a+x filename

Linux File Permissions (TutorialsPoint)

chmod Command Explained (GeeksforGeeks)
