

# **1. Basic Questions (Fundamentals & Architecture)**  

### **Q1. Rocky Linux kya hai?**  
📌 **Answer:**  
Rocky Linux ek **RHEL (Red Hat Enterprise Linux) based open-source Linux distribution** hai, jo **CentOS** ke alternative ke roop me develop kiya gaya hai. Iska objective **enterprise-grade stability aur long-term support** provide karna hai.  

### **Q2. Rocky Linux aur CentOS me kya difference hai?**  
📌 **Answer:**  
- **CentOS Stream** rolling updates deta hai, jo testing ke liye use hota hai, jabki **Rocky Linux stable version** hai.  
- **Rocky Linux 1:1 binary compatible hai RHEL ke saath**, jabki CentOS Stream nahi hai.  
- **Rocky Linux LTS (Long-Term Support) provide karta hai** jo production ke liye best hai.  

### **Q3. Rocky Linux ka default package manager kaunsa hai?**  
📌 **Answer:**  
**DNF (Dandified Yum)** Rocky Linux ka default package manager hai. Ye **YUM ka improved version** hai, jo **better dependency management aur faster performance** deta hai.  

### **Q4. SELinux kya hai aur iska kya role hai?**  
📌 **Answer:**  
**SELinux (Security-Enhanced Linux)** ek security mechanism hai jo **mandatory access control (MAC)** enforce karta hai. Ye **unauthorized access aur security threats** se system ko protect karta hai.  
👉 **SELinux ke modes:**  
- **Enforcing** (Default, strict security policy)  
- **Permissive** (Warnings generate karta hai but restrict nahi karta)  
- **Disabled** (SELinux off)  

Command to check SELinux status:  
```bash
sestatus
```  

---

# **2. User & Group Management**  

### **Q5. Ek naya user aur group kaise create karte hain?**  
📌 **Answer:**  
Naya user banane ke liye:  
```bash
useradd username
passwd username
```  
Naya group banane ke liye:  
```bash
groupadd groupname
```  

### **Q6. User ko sudo privileges kaise dete hain?**  
📌 **Answer:**  
```bash
usermod -aG wheel username
```  
Phir sudo access verify karein:  
```bash
sudo whoami
```  

---

# **3. Package Management (dnf, rpm)**  

### **Q7. Kaise check karenge ki ek package installed hai ya nahi?**  
📌 **Answer:**  
```bash
dnf list installed | grep package_name
```  

### **Q8. Kaise install/update/remove karenge ek package ko using dnf?**  
📌 **Answer:**  
Install:  
```bash
dnf install package_name
```  
Update:  
```bash
dnf update package_name
```  
Remove:  
```bash
dnf remove package_name
```  

### **Q9. RPM package manually kaise install karein?**  
📌 **Answer:**  
```bash
rpm -ivh package.rpm
```  

---

# **4. Process & Services Management**  

### **Q10. Systemd kya hai?**  
📌 **Answer:**  
**Systemd** ek init system hai jo **system boot process, services aur logging** manage karta hai.  

### **Q11. Systemd services ko start/stop/restart kaise karte hain?**  
📌 **Answer:**  
Start service:  
```bash
systemctl start service_name
```  
Stop service:  
```bash
systemctl stop service_name
```  
Restart service:  
```bash
systemctl restart service_name
```  

---

# **5. Storage & File System Management**  

### **Q12. File system types (ext4, xfs, btrfs) ka kya difference hai?**  
📌 **Answer:**  
- **ext4** – Traditional file system, journaling support  
- **XFS** – High-performance, large file support  
- **Btrfs** – Snapshot aur data integrity features  

### **Q13. Kaise check karein ki ek partition me kitni free space hai?**  
📌 **Answer:**  
```bash
df -h
```  

---

# **6. Networking in Rocky Linux**  

### **Q14. Kaise check karein ki ek network interface active hai ya nahi?**  
📌 **Answer:**  
```bash
ip a
nmcli device status
```  

### **Q15. FirewallD ka use karke ek port kaise open/close karein?**  
📌 **Answer:**  
Port open karein:  
```bash
firewall-cmd --add-port=8080/tcp --permanent
firewall-cmd --reload
```  
Port close karein:  
```bash
firewall-cmd --remove-port=8080/tcp --permanent
firewall-cmd --reload
```  

---

# **7. Logging & Monitoring**  

### **Q16. System logs kaha store hote hain?**  
📌 **Answer:**  
Most logs **/var/log/** directory me hote hain, jaise:  
- **/var/log/messages** – General system logs  
- **/var/log/secure** – Authentication logs  
- **journalctl -xe** – Systemd logs  

### **Q17. journalctl command ka kya use hai?**  
📌 **Answer:**  
Systemd logs dekhne ke liye use hota hai:  
```bash
journalctl -xe
journalctl -u service_name
```  

---

# **8. Security & Hardening**  

### **Q18. SELinux modes ka kya matlab hai?**  
📌 **Answer:**  
- **Enforcing** – Strict security  
- **Permissive** – Logs errors but allows actions  
- **Disabled** – Security policies off  

SELinux mode check karein:  
```bash
getenforce
```  

### **Q19. Fail2Ban ka use karke SSH brute force attack kaise prevent karein?**  
📌 **Answer:**  
```bash
dnf install fail2ban -y
systemctl enable --now fail2ban
fail2ban-client status
```  

---

# **9. Backup & Recovery**  

### **Q20. rsync aur tar ka kya use hai aur kaise backup lein?**  
📌 **Answer:**  
**tar** ka use backup ke liye:  
```bash
tar -czvf backup.tar.gz /important_data/
```  
**rsync** ka use remote backup ke liye:  
```bash
rsync -avz /source_dir/ user@remote:/backup_dir/
```  

---

# **10. Rocky Linux Containerization & Virtualization**  

### **Q21. Rocky Linux me Podman aur Docker me kya difference hai?**  
📌 **Answer:**  
- **Podman** rootless container support karta hai, jabki **Docker** daemon-based hai.  
- **Podman** ka security model better hai kyunki ye root privileges ke bina bhi chal sakta hai.  

### **Q22. Kaise ek simple Podman container run karein?**  
📌 **Answer:**  
```bash
podman run -d --name my_container nginx
podman ps
```  

---

### 🚀 **Final Tips:**  
✅ **Daily 2-3 hours hands-on practice karein**  
✅ **Mock interviews aur self-explanation practice karein**  
✅ **Scenario-based questions solve karein**  

Agar aap **yeh questions confidently answer kar lein**, to **Rocky Linux interview crack** karna **100% possible hai!** 🔥🚀








Aapke **Rocky Linux interview preparation** ke liye aur **in-depth questions** aur **real-world scenario-based** answers diye gaye hain. Yeh **advanced topics** aur **troubleshooting** bhi cover karega. 🚀  

---  

## **11. Boot Process & System Initialization**  

### **Q23. Rocky Linux ka boot process explain karein?**  
📌 **Answer:**  
1. **BIOS/UEFI** – System ko start karta hai aur bootloader locate karta hai.  
2. **GRUB2 (GRand Unified Bootloader)** – Kernel ko load karta hai.  
3. **Kernel Initialization** – Hardware detection karta hai aur system processes start karta hai.  
4. **Systemd Initialization** – Services aur targets load karta hai.  
5. **Login Prompt** – System ready ho jata hai user login ke liye.  

### **Q24. Kaise check karein ki last boot time kya tha?**  
📌 **Answer:**  
```bash
uptime
who -b
```  

### **Q25. Agar Rocky Linux boot nahi ho raha, to troubleshooting steps kya honge?**  
📌 **Answer:**  
1. **Boot logs check karein:**  
   ```bash
   journalctl -xb
   ```  
2. **GRUB2 menu open karein aur edit mode me jaakar single-user mode enable karein.**  
3. **Emergency mode enter karein:**  
   ```bash
   systemctl emergency
   ```  
4. **Filesystem errors check karein:**  
   ```bash
   fsck -y /dev/sdX
   ```  

---

## **12. Advanced User & Permission Management**  

### **Q26. Kaise ek user ko specific sudo permission di jaye bina full access ke?**  
📌 **Answer:**  
```bash
echo 'username ALL=(ALL) NOPASSWD: /bin/systemctl restart nginx' >> /etc/sudoers
```  
🔹 **Ye command sirf Nginx restart karne ki permission dega, full sudo access nahi.**  

### **Q27. SetUID, SetGID, aur Sticky Bit kya hote hain?**  
📌 **Answer:**  
- **SetUID (chmod u+s)** – Ek file jab kisi user dwara run hoti hai, to **file ka owner permission ke saath execute hoti hai**.  
- **SetGID (chmod g+s)** – Directory ke andar jo files create hoti hain, unka group **same** rahega.  
- **Sticky Bit (chmod +t)** – **Shared directories me files sirf owner delete kar sakta hai.**  

### **Q28. ACL (Access Control List) kya hai aur kaise set karein?**  
📌 **Answer:**  
ACL file/folder par **extra permissions** define karta hai.  
```bash
setfacl -m u:username:rwx /path/to/file
getfacl /path/to/file
```  

---

## **13. Storage & Disk Management**  

### **Q29. Kaise ek naya partition create karein aur mount karein?**  
📌 **Answer:**  
1. **Partition banayein:**  
   ```bash
   fdisk /dev/sdb
   ```  
2. **File system format karein:**  
   ```bash
   mkfs.ext4 /dev/sdb1
   ```  
3. **Mount karein:**  
   ```bash
   mount /dev/sdb1 /mnt
   ```  
4. **Permanent mount ke liye /etc/fstab edit karein.**  

### **Q30. LVM (Logical Volume Manager) ka use kaise karein?**  
📌 **Answer:**  
1. **Physical volume create karein:**  
   ```bash
   pvcreate /dev/sdb
   ```  
2. **Volume group create karein:**  
   ```bash
   vgcreate my_vg /dev/sdb
   ```  
3. **Logical volume create karein:**  
   ```bash
   lvcreate -L 10G -n my_lv my_vg
   ```  
4. **File system format karein aur mount karein.**  

---

## **14. Network Management & Troubleshooting**  

### **Q31. Kaise check karein ki ek port open hai ya nahi?**  
📌 **Answer:**  
```bash
ss -tulnp | grep 80
netstat -tulnp | grep 80
```  

### **Q32. Network interface restart kaise karein?**  
📌 **Answer:**  
```bash
nmcli networking off && nmcli networking on
systemctl restart NetworkManager
```  

### **Q33. Kaise ek static IP set karein Rocky Linux me?**  
📌 **Answer:**  
```bash
nmcli con mod eth0 ipv4.addresses 192.168.1.100/24
nmcli con mod eth0 ipv4.gateway 192.168.1.1
nmcli con mod eth0 ipv4.dns 8.8.8.8
nmcli con mod eth0 ipv4.method manual
nmcli con up eth0
```  

---

## **15. Security Hardening & Intrusion Detection**  

### **Q34. Kaise check karein ki last login kaunse user ka tha?**  
📌 **Answer:**  
```bash
last -a | head -10
```  

### **Q35. SSH login sirf ek particular user ke liye kaise allow karein?**  
📌 **Answer:**  
1. **/etc/ssh/sshd_config** file open karein:  
   ```bash
   nano /etc/ssh/sshd_config
   ```  
2. **Ye line add karein:**  
   ```bash
   AllowUsers specific_user
   ```  
3. **Restart SSH service:**  
   ```bash
   systemctl restart sshd
   ```  

### **Q36. Fail2Ban ko enable kaise karein brute force attack se bachne ke liye?**  
📌 **Answer:**  
```bash
dnf install fail2ban -y
systemctl enable --now fail2ban
```  

---

## **16. Virtualization & Containerization**  

### **Q37. Rocky Linux me KVM install aur configure kaise karein?**  
📌 **Answer:**  
```bash
dnf install @virt virt-install
systemctl enable --now libvirtd
virt-manager
```  

### **Q38. Podman aur Docker ka kya difference hai?**  
📌 **Answer:**  
- **Podman rootless mode support karta hai** jo Docker me nahi hai.  
- **Docker ek daemon chalaata hai**, jabki **Podman direct CLI se work karta hai**.  
- **Podman, OCI (Open Container Initiative) standards follow karta hai** jo Docker compatible hai.  

### **Q39. Kaise ek simple Podman container run karein?**  
📌 **Answer:**  
```bash
podman run -d --name my_container nginx
podman ps
```  

---

## **17. Performance Monitoring & Logging**  

### **Q40. CPU aur Memory usage check karne ke best commands kaun-si hain?**  
📌 **Answer:**  
```bash
top
htop
free -m
vmstat 1 5
```  

### **Q41. System logs kaise analyze karein?**  
📌 **Answer:**  
```bash
journalctl -xe
tail -f /var/log/messages
```  

---

### 🎯 **Final Tips for Cracking Rocky Linux Interview:**  
✅ **Real-world scenarios par focus karein**  
✅ **Daily command line practice karein**  
✅ **Mock interviews aur self-explanation practice karein**  
✅ **Security aur troubleshooting ke use-cases padhein**  

Agar aap **yeh questions confidently answer kar sakein**, to **Rocky Linux interview crack** karna **100% possible hai!** 🔥🚀
