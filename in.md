Yeh **Rocky Linux interview questions with answers** ka **detailed guide** hai. Ye **basic se advanced** level tak sab cover karega, jo aapke **deep understanding** aur **confidence** ke liye perfect hoga.  

---  

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
