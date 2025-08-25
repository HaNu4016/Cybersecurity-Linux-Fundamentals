Day-01 : Linux Security Fundamentals
1. What is Linux?

 Linux is an open-source operating system kernel used widely in servers, cloud, networking, and cybersecurity.
 It is a multiuser, multitasking OS where every user and process can be controlled with permissions.

Use cases:

 90% of cloud servers (AWS, GCP, Azure) run on Linux.

 In cybersecurity, Linux is preferred for penetration testing and server hardening.

 Interview Q: Why is Linux preferred in cybersecurity?
 Answer: Because it is open-source, lightweight, more secure, and provides strong networking + permission controls which are essential for security tools and system hardening.

2. Linux File System Basics

 In Linux, everything is treated as a file (devices, processes, configurations).
 It follows a hierarchical structure starting from the root /.

Important Directories:

/home → user personal files

/etc → configuration files

/var/log → system logs

/bin & /sbin → executable commands

Example:

If your username is hanuman, your home directory will be /home/hanuman.

To view users info: cat /etc/passwd

Interview Q: What does /etc/shadow store?
Answer: It stores encrypted passwords of system users.

3. Linux Users & Groups

 A user is an account that can access the system.
 A group is a collection of users whose permissions can be managed together.

Example Commands:

whoami          # current user
id              # user + group info
adduser test    # add new user
groupadd devs   # add new group
usermod -aG devs test   # add user to group


Use case:

A devops group can be created for the DevOps team → all users can share permissions easily.

Interview Q: Why is the root user dangerous?
Answer: Root has unlimited access (modify, delete, install, configure). If compromised, the whole system is at risk.

4. File Permissions (rwx)
 Each file in Linux has 3 permissions – read (r), write (w), execute (x).
 These permissions are set for owner, group, and others.
Linux file/folder permissions control who can read, write, or execute a file.

Permission types:

r – Read → View file contents or list folder contents → Value 4

w – Write → Modify file or create/delete files in folder → Value 2

x – Execute → Run file/script or enter folder → Value 1

Permission categories:

User (u): File/folder owner

Group (g): Users in same group

Others (o): Everyone else

Numeric Permissions

rwx = 4+2+1 = 7 → Full

rw- = 4+2 = 6 → Read + write

r-x = 4+1 = 5 → Read + execute

r-- = 4 → Read only

--- = 0 → No access

Use-case:

Database config → 600 (only owner)

Web folder → 755 (others can read/execute)

Example:

ls -l file.txt
-rw-r--r--  1 hanuman users  120 Aug 25  file.txt


Owner: rw- → read + write

Group: r-- → read only

Others: r-- → read only

Change Permissions:

chmod 755 script.sh   # rwxr-xr-x
chown hanuman:users file.txt  # change owner & group


Use case:

Sensitive files (/etc/shadow) should only be readable by root.

Interview Q: What does chmod 600 file.txt mean?
Answer: Owner = read + write, Group = no access, Others = no access.

Q: What are Linux file permissions?
A: Permissions control who can read, write, or execute files/folders; categories: user, group, others.

Q: Explain numeric permissions?
A: r=4, w=2, x=1; sum determines access: rwx=7, rw-=6, r-x=5, r--=4

Q: Difference between chmod 700 and 755?
A: 700 → only owner full access, others none; 755 → owner full, group/others read+execute

5. Mini Project – Secure Folder

Task: Create a folder that only you (the owner) can access.

mkdir secret
chmod 700 secret


Now only the owner can read/write/execute inside secret.

Group and Others have no access.


Ownership & chmod
Theory

Ownership defines which user & group can access the file/folder

chown → Change owner/group

chmod → Change permissions

Commands
sudo chown alice:devteam /secure_data  # Set owner and group
chmod 700 /secure_data                  # Owner full, group/others none
chmod 755 /secure_data                  # Owner full, group/others read+execute


Use-case:

Secure private folders for single user

Public folders for group access

Interview Questions – Ownership & chmod

Q: What is chown used for?
A: To change the owner and group of a file/folder.

Q: How do chmod values work?
A: Numeric values: r=4, w=2, x=1; sum defines access for owner/group/others.

5️⃣ Topic 4: SSH Basics
Theory

SSH (Secure Shell) → Secure remote login to Linux machine

Encrypts traffic, safer than Telnet

Command
ssh username@IP


Use-case: Remote server management, DevOps pipelines, admin tasks

Interview Questions – SSH

Q: What is SSH and why use it?
A: Secure remote connection with encryption; prevents password sniffing.

Q: Difference between password-based and key-based SSH?
A: Password → simple login; Key-based → more secure, recommended for servers

6️⃣ Practical Commands – Day 1
mkdir /secure_data                   # Create folder
sudo adduser alice                    # Create user alice
sudo adduser bob                      # Create user bob
sudo groupadd devteam                 # Create group
sudo usermod -aG devteam alice        # Add alice to group
sudo chown alice:devteam /secure_data # Set ownership
chmod 700 /secure_data                # Only owner can access
su - bob                               # Switch to bob
cd /secure_data                        # Test access → should fail


✅ Day-01 Summary

Understood Linux basics

Explored file system structure

Learned user & group management

Learned file permissions (chmod, chown)

Built a secure folder mini project
