
### **Linux Backup & Restore Commands: `tar`, `cpio`, and `rsync`**  

Linux me backup aur restore ke liye kai tarike hain. **`tar`**, **`cpio`**, aur **`rsync`** sabse jyada use hone wale commands hain. Yeh commands **file aur directory backup, compression, aur remote synchronization** ke liye kaam aati hain.  

---

## **1. `tar` (Tape Archive)**
`tar` ek traditional archive tool hai jo **multiple files aur directories ko ek single archive file** me store karta hai. Yeh **compression bhi support** karta hai.

###  **Syntax:**
```bash
tar [options] -f archive_name.tar /path/to/files
```
### **Common Options:**
- `c` → **Create** (naya archive banaye)  
- `x` → **Extract** (archive ko restore kare)  
- `v` → **Verbose** (progress show kare)  
- `f` → **File name specify kare**  
- `z` → **Gzip compression enable kare**  
- `j` → **bzip2 compression enable kare**  
- `C` → **Extract kisi specific directory me kare**  

### **🔹 `tar` Examples**
####  **Backup (Create Archive)**
```bash
tar -cvf backup.tar /home/user
```
![image](https://github.com/user-attachments/assets/907a40a4-c32d-4133-83d2-1bbce31848c8)

_(Yeh `/home/user` ka archive `backup.tar` me store karega)_

####  **Compressed Backup (Gzip)**
```bash
tar -cvzf backup.tar.gz /home/user

```
![image](https://github.com/user-attachments/assets/a30d1137-8c15-452e-a4fc-dd5f17b2955c)

_(Yeh archive ko gzip se compress karega)_

####  **Extract (Restore) Archive**
```bash
tar -xvf backup.tar
```
![image](https://github.com/user-attachments/assets/fbb5055d-3c87-4d81-b112-5eaade40fcf1)

####  **Extract to a Specific Directory**
```bash
tar -xvf backup.tar -C /restore/location
```
![image](https://github.com/user-attachments/assets/dbe31983-c8b8-473b-9d09-a2bb5f0aa489)
![image](https://github.com/user-attachments/assets/d64a5581-db20-437d-bca1-a8c2915cb23c)




