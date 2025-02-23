🔌 **1. BIOS/UEFI Initialization**  
   └─ 🔍 Hardware check (POST)  
   └─ 📍 Finds bootable device  
   └─ 🚀 Loads Bootloader  

🏁 **2. Bootloader (GRUB)**  
   └─ 📥 Loads Kernel into memory  
   └─ 📜 Passes boot parameters  
   └─ 🖥️ Displays boot menu (if needed)  

🧠 **3. Kernel Initialization**  
   └─ ⚙️ Initializes drivers  
   └─ 📂 Mounts root filesystem  
   └─ 🚦 Starts init system (e.g., systemd)  

⚙️ **4. Init System (Systemd/Upstart/SysVinit)**  
   └─ 🔄 Starts services and daemons  
   └─ 🎯 Sets target (multi-user, graphical)  
   └─ 📝 Logs boot process  

🛠️ **5. Runlevel/Target Initialization**  
   └─ 💻 CLI mode (multi-user.target)  
   └─ 🖥️ GUI mode (graphical.target)  

👤 **6. User Authentication**  
   └─ 🔑 Prompts login (GDM, LightDM)  
   └─ 💻 Starts shell or desktop  

📂 **7. User Environment Setup**  
   └─ ⚙️ Loads personal configurations (.bashrc)  
   └─ 📡 Starts background apps/services  
