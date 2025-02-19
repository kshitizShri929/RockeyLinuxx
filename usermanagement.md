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
![image](https://github.com/user-attachments/assets/daac985c-71ca-42ef-842c-1a83d5d7c251)


## **2. Creating a New User**  

### **Basic User Creation**  
```bash
 useradd username
```

![image](https://github.com/user-attachments/assets/ed6c0a5f-2837-4b07-91e8-2a78045ed02a)

- This creates a user but does not set a password.  
- The default home directory is `/home/username`.  
- The default shell is `/bin/bash`.  

### **Create User with Home Directory**  
```bash
 useradd -m username
```
![image](https://github.com/user-attachments/assets/ad4e368b-585d-4f6d-96d7-df82b865ff38)

The `-m` option ensures the home directory is created under `/home/username`.

### **Set Password for User**  
```bash
 passwd username
```
![image](https://github.com/user-attachments/assets/403124af-1173-40e8-ad18-1302a5b04e97)

*shri@123

Users can also change their own password:  
```bash
passwd
```

---

## **3. Modifying User Accounts**  

### **Change User Home Directory**  
```bash
 usermod -d /new/home/directory username
```
![image](https://github.com/user-attachments/assets/87b163bf-94e3-4d77-bcc2-05d2932e67ed)

- **-d:** The -d option in the usermod command stands for "directory" and is used to change the home directory of a user.

### **Change Username**  
```bash
sudo usermod -l newusername oldusername
```
![image](https://github.com/user-attachments/assets/21521b68-84c9-46c6-9467-0386ee75246e)

-l

### **Change User's Default Shell**  
```bash
sudo usermod -s /bin/zsh username
```
![image](https://github.com/user-attachments/assets/66f53963-7127-4093-9f42-10bd3f162e3a)

To list available shells:  
```bash
cat /etc/shells
```
![image](https://github.com/user-attachments/assets/35e8bb75-3b10-41ce-a401-41e8d249f0ea)


### **Expire a User's Password (Force Password Change at Next Login)**  
```bash
sudo passwd -e username
```
![image](https://github.com/user-attachments/assets/845e8075-becd-4d1e-b694-2caec9bdc948)



## **4. Deleting a User**  

### **Delete a User (Without Deleting Home Directory)**  
```bash
sudo userdel username
```
![image](https://github.com/user-attachments/assets/5447aa5a-c66e-4d60-9f1a-48985429602b)


### **Delete a User and Their Home Directory**  
```bash
sudo userdel -r username
```
![image](https://github.com/user-attachments/assets/032bbdac-dce8-4734-89de-54e36f714867)


## **5. Group Management in Rocky Linux**  

### **Check All Groups**  
```bash
cat /etc/group
```
![image](https://github.com/user-attachments/assets/5b9918c8-0fb8-40a1-b74e-b3b85789d225)

### **Create a New Group**  
```bash
sudo groupadd groupname
```
![image](https://github.com/user-attachments/assets/405ded15-2eff-45d5-892b-dbfbef269184)

### **Add a User to a Group**  
```bash
sudo usermod -aG groupname username
```
![image](https://github.com/user-attachments/assets/839bb614-d68f-492a-bfdc-60e0d194d33c)

- `-aG`: Appends the user to a group without removing existing group memberships.

### **Remove a User from a Group**  
```bash
sudo gpasswd -d username groupname
```
![image](https://github.com/user-attachments/assets/7d18b4af-f156-42a6-a760-eb503b002267)

### **Delete a Group**  
```bash
sudo groupdel groupname
```
 ![image](https://github.com/user-attachments/assets/d92a1431-432f-4fbf-9d5b-12027c1d2bba)

### **Check User’s Group Membership**  
```bash
groups username
```
or  
```bash
id username
```

![image](https://github.com/user-attachments/assets/c62a3b8c-2faa-45fd-8cab-159a5dc44479)


## **6. Managing User Privileges with Sudo**  

### **Grant a User Sudo Access**  
By default, Rocky Linux uses the `wheel` group for sudo access. Add a user to this group:  
```bash
sudo usermod -aG wheel username
```
![image](https://github.com/user-attachments/assets/010b5f5e-fe7d-4707-8632-0b4b6f58e127)


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
![image](https://github.com/user-attachments/assets/e28bd9e1-16c5-4886-b870-87af633a8a47)

The user will not be able to log in.

### **Unlock a User Account**  
```bash
sudo usermod -U username
```
![image](https://github.com/user-attachments/assets/0cafe70a-1c03-4d63-a296-041374628c80)

NOTE:

- Before locking: The user had a normal password entry.
- After locking (-L): The ! was added, preventing login.
- After unlocking (-U): The ! was removed, restoring access.


### **Disable Password Login for a User**  
```bash
sudo passwd -l username

```
![image](https://github.com/user-attachments/assets/03ca4c93-01d5-4dbb-a1e9-de718004d107)

This prevents the user from logging in but does not remove the account.

---

## **8. Managing User Expiration**  

### **Set an Expiry Date for a User**  
```bash
sudo chage -E YYYY-MM-DD username

```
 And check User Account Expiration Information 
```bash
sudo chage -l username
```

![image](https://github.com/user-attachments/assets/0b2eb4a1-b6ec-4d90-94af-c7fb385973a4)


## **9. File Permissions & Ownership**  

### **Check File Permissions**  
```bash
ls -l filename
```
![image](https://github.com/user-attachments/assets/3edf724f-a0a7-4942-8f68-dbfde4a4111e)

### **Change File Owner**  
```bash
sudo chown username:groupname filename
```
![image](https://github.com/user-attachments/assets/ffb890d5-d66d-453f-8a4f-2d9c6aa417f8)


### **Change File Permissions**  
```bash
chmod 755 filename
```
![image](https://github.com/user-attachments/assets/0d7c1a91-6d7b-46d8-b98b-92fe903f3748)

- `7` → Owner: Read, Write, Execute  
- `5` → Group: Read, Execute  
- `5` → Others: Read, Execute  

To **change directory permissions recursively**:  
```bash
chmod -R 755 /path/to/directory
```
![image](https://github.com/user-attachments/assets/52a33e9d-acf5-4876-b7a0-fc5038f563d9)

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
