## **Vi Text Editor - Important Commands**  

### **Modes in Vi**  
- **Normal Mode**: Commands execute karne ke liye (`Esc`)  
- **Insert Mode**: Text edit karne ke liye (`i`, `a`, `o`)  
- **Command Mode**: File save, exit, search, replace (`:`)  

### **Opening & Exiting Vi**  
- `vi filename` → File open karein  
- `:w` → Save karein  
- `:q` → Exit karein  
- `:wq` / `ZZ` → Save + Exit  
- `:q!` → Force quit bina save kiye  

### **Navigation Commands**  
- `h` → Left, `l` → Right, `j` → Down, `k` → Up  
- `w` → Next word, `b` → Previous word  
- `0` → Line start, `$` → Line end  
- `gg` → File start, `G` → File end  
- `:n` → Line number `n` par jayein  

### **Editing Commands**  
- `i` → Insert at cursor, `a` → Insert after cursor  
- `o` → Neeche nayi line, `O` → Upar nayi line  

### **Deleting & Copy-Pasting**  
- `x` → Character delete, `dd` → Line delete  
- `dw` → Word delete, `d$` → Line end tak delete  
- `yy` → Line copy, `p` → Paste after cursor  

### **Undo & Redo**  
- `u` → Undo, `Ctrl + r` → Redo  

### **Search & Replace**  
- `/text` → Search forward  
- `?text` → Search backward  
- `n` → Next match, `N` → Previous match  
- `:%s/old/new/g` → Replace all  


