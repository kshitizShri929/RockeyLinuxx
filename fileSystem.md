  # Rocky Linux File System

## 1. **Introduction to Rocky Linux File System**  
Rocky Linux follows the standard Linux file system hierarchy defined by the **Filesystem Hierarchy Standard (FHS)**. It uses the **XFS** file system by default but also supports **ext4, Btrfs, and ZFS**.  

---

## 2. **File System Types in Rocky Linux**  
Rocky Linux supports various file systems:  

| File System | Description |
|-------------|-------------|
| **XFS** | Default file system in Rocky Linux, supports large files and journaling. |
| **ext4** | Common Linux file system, supports journaling and large file sizes. |
| **Btrfs** | Advanced file system with features like snapshots and compression. |
| **ZFS** | High-performance file system with data integrity features. |
| **VFAT** | Used for compatibility with Windows partitions (FAT32). |
| **NTFS** | Used for reading Windows file systems. |

---

## 3. **Rocky Linux File System Hierarchy**  
The file system is structured into directories with specific purposes:  

| Directory | Purpose |
|------------|-------------|
| **/** (Root) | Top-level directory containing all system files. |
| **/bin** | Essential user binaries (e.g., `ls`, `cp`, `mv`). |
| **/boot** | Kernel and boot loader files (e.g., `vmlinuz`, `grub`). |
| **/dev** | Device files representing hardware (e.g., `/dev/sda`). |
| **/etc** | System-wide configuration files. |
| **/home** | User directories (e.g., `/home/user`). |
| **/lib** | Shared libraries for system programs. |
| **/mnt** | Temporary mount point for external devices. |
| **/media** | Auto-mounted media (USB, CD-ROM). |
| **/opt** | Optional software packages. |
| **/proc** | Virtual directory for system information. |
| **/root** | Home directory for root user. |
| **/run** | System runtime data. |
| **/sbin** | System binaries for root user (e.g., `fdisk`, `mount`). |
| **/srv** | Data served by system services. |
| **/sys** | Kernel information about devices. |
| **/tmp** | Temporary files (cleared at boot). |
| **/usr** | User applications and utilities. |
| **/var** | Variable files (logs, caches, spool). |

---

## 4. **Managing File Systems in Rocky Linux**  

### 4.1 **Checking Available File Systems**  
```bash
cat /proc/filesystems
lsblk -f
```

### 4.2 **Creating and Formatting a File System**  
- **XFS (default in Rocky Linux):**  
  ```bash
  mkfs.xfs /dev/sdb1
  ```

- **ext4:**  
  ```bash
  mkfs.ext4 /dev/sdb1
  ```

- **Btrfs:**  
  ```bash
  mkfs.btrfs /dev/sdb1
  ```

### 4.3 **Mounting and Unmounting a File System**  
- **Mount a file system:**  
  ```bash
  mount /dev/sdb1 /mnt
  ```
- **Unmount a file system:**  
  ```bash
  umount /mnt
  ```

### 4.4 **Persistent Mounting (via /etc/fstab)**  
To mount a partition permanently, edit `/etc/fstab`:  
```bash
/dev/sdb1  /mnt  xfs  defaults  0 0
```
Then run:  
```bash
mount -a
```

### 4.5 **Checking Disk Usage**  
- **Check disk space:**  
  ```bash
  df -h
  ```
- **Check inodes:**  
  ```bash
  df -i
  ```
- **Check storage devices:**  
  ```bash
  lsblk
  ```

---

## 5. **Logical Volume Management (LVM) in Rocky Linux**  
LVM allows for flexible disk management.

### 5.1 **Creating an LVM Partition**  
1. **Create a physical volume (PV):**  
   ```bash
   pvcreate /dev/sdb
   ```
2. **Create a volume group (VG):**  
   ```bash
   vgcreate my_vg /dev/sdb
   ```
3. **Create a logical volume (LV):**  
   ```bash
   lvcreate -L 10G -n my_lv my_vg
   ```
4. **Format the logical volume:**  
   ```bash
   mkfs.xfs /dev/my_vg/my_lv
   ```
5. **Mount the logical volume:**  
   ```bash
   mount /dev/my_vg/my_lv /mnt
   ```

### 5.2 **Extending an LVM Volume**  
1. Extend the logical volume:  
   ```bash
   lvextend -L +5G /dev/my_vg/my_lv
   ```
2. Resize the file system:  
   ```bash
   xfs_growfs /mnt
   ```

---

## 6. **RAID in Rocky Linux**  
RAID (Redundant Array of Independent Disks) provides redundancy.

### 6.1 **Creating a RAID 1 Array (Mirroring)**  
1. Install RAID utilities:  
   ```bash
   dnf install mdadm
   ```
2. Create RAID 1:  
   ```bash
   mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
   ```
3. Format and mount:  
   ```bash
   mkfs.xfs /dev/md0
   mount /dev/md0 /mnt
   ```

---

## 7. **File System Troubleshooting Commands**  
| Command | Purpose |
|---------|---------|
| `fsck` | Check and repair file system errors. |
| `xfs_repair` | Repair XFS file systems. |
| `tune2fs` | Modify ext4 file system parameters. |
| `mount -o remount,rw /` | Remount root file system as read-write. |

---

## 8. **Backing Up and Restoring File Systems**  

### 8.1 **Backup using tar**  
```bash
tar -czvf backup.tar.gz /home/user
```

### 8.2 **Backup using rsync**  
```bash
rsync -avz /home/user/ /mnt/backup/
```

### 8.3 **Restoring a Backup**  
```bash
tar -xzvf backup.tar.gz -C /
```

---

## 9. **Conclusion**  
Rocky Linux provides robust file system management, with **XFS as the default**, support for LVM, RAID, and various file system utilities. Proper use of tools like `fsck`, `mount`, `df`, and LVM ensures smooth file system administration.
