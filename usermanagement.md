### **Rocky Linux User Management **  

Rocky Linux is a **RHEL-based** distribution that provides a stable and enterprise-grade operating system. **User management** in Rocky Linux involves adding, modifying, deleting users, managing groups, and controlling permissions.  

---

## **1. User Accounts in Rocky Linux**  
Each user account has a **username**, **UID (User ID)**, **GID (Group ID)**, **home directory**, and **shell**.  

### **Check Existing Users**  
Users are stored in the `/etc/passwd` file. To see all users:  
```bash
cat /etc/passwd

```
![image](https://github.com/user-attachments/assets/824de2a2-8efa-4056-8ce7-c3421351462b)


**Summary of /etc/passwd Output**

- **System Users:** root, bin, daemon, adm, lp, sync, shutdown, halt, mail, operator, games, and ftp are system/service accounts with /sbin/nologin or restricted shells.
- **Special Users:** nobody (used for unprivileged processes) and tss (for TPM access) have restricted access.
- **Regular User:** shri is a normal user with a home directory (/home/shri) and an interactive shell (/bin/bash).
  
To check a specific user:  
```bash
id username
```
[root@1309553fa3d7 /]# id shri
uid=1000(shri) gid=1000(shri) groups=1000(shri)
[root@1309553fa3d7 /]#

### **Check Logged-in Users**  
```bash
who  
w  
```
To check the last login of a user:  
```bash
last username
```

---

## **2. Creating a New User**  

### **Basic User Creation**  
```bash
sudo useradd username
```
- This creates a user but does not set a password.  
- The default home directory is `/home/username`.  
- The default shell is `/bin/bash`.  

### **Create User with Home Directory**  
```bash
sudo useradd -m username
```
The `-m` option ensures the home directory is created under `/home/username`.

### **Set Password for User**  
```bash
sudo passwd username
```
Users can also change their own password:  
```bash
passwd
```

---

## **3. Modifying User Accounts**  

### **Change User Home Directory**  
```bash
sudo usermod -d /new/home/directory username
```

### **Change Username**  
```bash
sudo usermod -l newusername oldusername
```

### **Change User's Default Shell**  
```bash
sudo usermod -s /bin/zsh username
```
To list available shells:  
```bash
cat /etc/shells
```

### **Expire a User's Password (Force Password Change at Next Login)**  
```bash
sudo passwd -e username
```

---

## **4. Deleting a User**  

### **Delete a User (Without Deleting Home Directory)**  
```bash
sudo userdel username
```

### **Delete a User and Their Home Directory**  
```bash
sudo userdel -r username
```

---

## **5. Group Management in Rocky Linux**  

### **Check All Groups**  
```bash
cat /etc/group
```

### **Create a New Group**  
```bash
sudo groupadd groupname
```

### **Add a User to a Group**  
```bash
sudo usermod -aG groupname username
```
- `-aG`: Appends the user to a group without removing existing group memberships.

### **Remove a User from a Group**  
```bash
sudo gpasswd -d username groupname
```

### **Delete a Group**  
```bash
sudo groupdel groupname
```

### **Check User’s Group Membership**  
```bash
groups username
```
or  
```bash
id username
```

---

## **6. Managing User Privileges with Sudo**  

### **Grant a User Sudo Access**  
By default, Rocky Linux uses the `wheel` group for sudo access. Add a user to this group:  
```bash
sudo usermod -aG wheel username
```

### **Grant Sudo Without Password (Edit Sudoers File)**  
```bash
sudo visudo
```
Add this line at the end:  
```
username ALL=(ALL) NOPASSWD:ALL
```
This allows the user to execute any command without entering a password.

### **Remove Sudo Access**  
```bash
sudo deluser username wheel
```

---

## **7. Locking and Unlocking User Accounts**  

### **Lock a User Account**  
```bash
sudo usermod -L username
```
The user will not be able to log in.

### **Unlock a User Account**  
```bash
sudo usermod -U username
```

### **Disable Password Login for a User**  
```bash
sudo passwd -l username
```
This prevents the user from logging in but does not remove the account.

---

## **8. Managing User Expiration**  

### **Set an Expiry Date for a User**  
```bash
sudo chage -E YYYY-MM-DD username
```
For example, to expire a user on **December 31, 2025**:  
```bash
sudo chage -E 2025-12-31 username
```

### **Check User Account Expiration Information**  
```bash
sudo chage -l username
```

---

## **9. File Permissions & Ownership**  

### **Check File Permissions**  
```bash
ls -l filename
```

### **Change File Owner**  
```bash
sudo chown username:groupname filename
```

### **Change File Permissions**  
```bash
chmod 755 filename
```
- `7` → Owner: Read, Write, Execute  
- `5` → Group: Read, Execute  
- `5` → Others: Read, Execute  

To **change directory permissions recursively**:  
```bash
chmod -R 755 /path/to/directory
```

---

## **10. Useful User Management Commands**  

| **Command** | **Description** |
|------------|----------------|
| `whoami` | Show the current logged-in user |
| `who` | Show all logged-in users |
| `id username` | Show UID, GID, and groups of a user |
| `passwd username` | Change user password |
| `groups username` | Show groups of a user |
| `useradd -m username` | Add a user with a home directory |
| `usermod -aG groupname username` | Add a user to a group |
| `userdel -r username` | Remove a user with their home directory |
| `groupadd groupname` | Create a group |
| `groupdel groupname` | Delete a group |
| `gpasswd -d username groupname` | Remove user from a group |
| `usermod -L username` | Lock a user account |
| `usermod -U username` | Unlock a user account |
| `chage -E YYYY-MM-DD username` | Set an account expiration date |
| `sudo visudo` | Edit sudoers file for privilege management |

---

## **Conclusion**  
User management in Rocky Linux is a fundamental system administration task. By using the above commands, you can create, modify, and delete users, manage permissions, control sudo privileges, and ensure secure access management.

Let me know if you need any clarifications! 🚀
