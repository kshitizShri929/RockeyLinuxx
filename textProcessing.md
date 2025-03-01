Here are some basic and practical **`sed`**, **`awk`**, and **`grep`** commands for text processing. You can try these on a sample text file.

---

## 📌 **1. `sed` (Stream Editor) Commands**
`sed` is used for modifying text in a file or input stream.

### **Replace text in a file**
```sh
sed 's/oldtext/newtext/' file.txt
```
_Replaces first occurrence of "oldtext" with "newtext" per line._

```sh
sed 's/oldtext/newtext/g' file.txt
```
_Replaces all occurrences in a line._

### **Delete a specific line**
```sh
sed '3d' file.txt
```
_Deletes the 3rd line from the file._

### **Print only specific lines**
```sh
sed -n '2,4p' file.txt
```
_Prints lines 2 to 4._

---

## 📌 **2. `awk` (Pattern Scanning & Processing) Commands**
`awk` is great for extracting and processing text.

### **Print a specific column**
```sh
awk '{print $1}' file.txt
```
_Prints the first column of each line._

```sh
awk '{print $1, $3}' file.txt
```
_Prints the 1st and 3rd column._

### **Print lines matching a pattern**
```sh
awk '/pattern/ {print $0}' file.txt
```
_Prints all lines containing "pattern"._

### **Calculate sum of a column (e.g., numbers in column 2)**
```sh
awk '{sum += $2} END {print sum}' file.txt
```
_Sums up all numbers in the second column._

---

## 📌 **3. `grep` (Pattern Searching) Commands**
`grep` searches for patterns in files.

### **Search for a word in a file**
```sh
grep "word" file.txt
```
_Searches for "word" in `file.txt`._

### **Case-insensitive search**
```sh
grep -i "word" file.txt
```

### **Find whole word matches**
```sh
grep -w "word" file.txt
```

### **Search recursively in a directory**
```sh
grep -r "word" /path/to/directory
```

### **Find lines that do NOT match a pattern**
```sh
grep -v "word" file.txt
```
_Excludes lines containing "word"._

---

🔹 Try these commands and let me know if you need more advanced use cases! 🚀
