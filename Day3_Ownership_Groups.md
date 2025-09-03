Day 3 – Ownership & Groups in Linux Security

1. Users in Linux
 In Linux, every task is performed by a user account, whether it’s an admin or a normal user.
 A user is identified in the system with a unique UID (User ID).
Purpose: To separate access for different people so that one user cannot directly interfere with another user’s files.

Characteristics:
 Each user has a home directory (e.g., /home/username).
 Each user has a default primary group.
 Users can have different privilege levels (normal user vs root).
 Use Case: In a college server, each student has their own user account so that their data stays separate.

Command Examples:
 whoami     # Show current user
 id         # Display UID, GID and groups
 groups     # Show groups of current user

2. Groups in Linux
  A group is a collection of users that share common permissions.
  A file or folder can be owned by a group, so all members of that group share the same access.
purpose: To make permission management easier for multiple users working on the same project.

Characteristics:
 Each user has one primary group.
 A user can belong to multiple secondary groups.
 All groups are recorded in /etc/group.
 Use Case: Create a devteam group and add developers to it so they can all access the same project folder.

Commands:
         cat /etc/group              # See list of groups
         sudo groupadd devteam       # Create new group
         sudo usermod -aG devteam user1   # Add user1 to devteam group
         groups user1                # Verify group membership

3. Ownership in Linux
   Ownership means who controls a file or folder.
   Every file has three ownerships – User, Group, and Others.
   Purpose: To enforce security by giving control only to authorized users or groups.

Characteristics:
  The owner (user) has maximum control.
   The group allows shared access.
   Others (all remaining users) have restricted access.
   Use Case: A report file should be readable only by project team members (group), not by outsiders.

Commands:
         ls -l                       # View file permissions and ownership 
         sudo chown user:group file  # Change both owner and group
         sudo chgrp devteam file     # Change only group ownership

4. Files related to Users & Groups
/etc/passwd → stores information about users (username, UID, home directory, shell).
/etc/group → stores information about groups.

Example:
        cat /etc/passwd | head -5
         cat /etc/group | head -5

5. Working Example (Step-by-step Lab)
Create a new group:
    sudo groupadd devteam

Create two new users:
    sudo adduser user1
    sudo adduser user2

Add both users to the group:
    sudo usermod -aG devteam user1
    sudo usermod -aG devteam user2

Create a secure project folder:
     sudo mkdir /devproject
     sudo chown :devteam /devproject
     sudo chmod 770 /devproject

verification:
   user1 & user2 can access the folder ✅
   Any other user gets “Permission denied” ❌

6. Practice Exercises
 Create a group cyberlab, add 3 users into it.
 Make a folder accessible only to members of cyberlab.
 Create a file that only the owner can read (others denied).

7. 10 Important Questions (with Answers)

Q: What are the three ownership categories of a Linux file?
A: User (owner), Group, Others.

Q: Command to check groups of a user?
A: groups username

Q: Command to create a new group?
A: sudo groupadd groupname

Q: Command to change file owner and group together?
A: sudo chown user:group filename

Q: What is stored in /etc/passwd?
A: User details: username, UID, home directory, shell.

Q: Command to add a user into a secondary group?
A: sudo usermod -aG groupname username

Q: Difference between primary and secondary groups?
A: Primary = default group of user, Secondary = additional groups.

Q: Which file stores group information?
A: /etc/group

Q: Why is ownership important in Linux security?
A: For data isolation, access control, and accountability.

Q: What does permission 770 mean?
A: Owner → rwx, Group → rwx, Others → no access.

8. Reference Websites (for Revision)
Linux User and Group Management – GeeksforGeeks
Linux File Permissions – TutorialsPoint

✅ This covers 1-hour study material with theor
