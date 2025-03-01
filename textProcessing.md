**`sed`**, **`awk`**, and **`grep`** commands for text processing. 

---

##  **1. `sed` (Stream Editor) Commands**
`sed` is used for modifying text in a file or input stream.

### **Replace text in a file**
```sh
sed 's/oldtext/newtext/' file.txt
```
_Replaces first occurrence of "oldtext" with "newtext" per line._
![image](https://github.com/user-attachments/assets/6b277390-ea13-43f8-ab8c-ffb37be9623b)


```sh
sed 's/oldtext/newtext/g' file.txt
```
![image](https://github.com/user-attachments/assets/1d65b8b8-ee9b-4924-880d-92259fb51bbf)

_Replaces all occurrences in a line._

### **Delete a specific line**
```sh
sed '3d' file.txt
```

_Deletes the 3rd line from the file._
![image](https://github.com/user-attachments/assets/c303d323-d8f8-41f1-a797-882c6c8cf53a)


### **Print only specific lines**
```sh
sed -n '2,4p' file.txt
```
_Prints lines 2 to 4._

![image](https://github.com/user-attachments/assets/4f091d9e-a1fe-465c-a16a-b61c7cc86703)

---

##  **2. `awk` (Pattern Scanning & Processing) Commands**
`awk` is great for extracting and processing text.

### **Print a specific column**
```sh
awk '{print $1}' file.txt
```
_Prints the first column of each line._
![image](https://github.com/user-attachments/assets/4d336b16-52c7-4f57-a3bf-2698e30f2a78)


```sh
awk '{print $1, $3}' file.txt
```
_Prints the 1st and 3rd column._
![image](https://github.com/user-attachments/assets/71991ac9-16b6-4ac2-8170-c0d3b24a4899)


### **Print lines matching a pattern**
```sh
awk '/pattern/ {print $0}' file.txt
```
_Prints all lines containing "pattern"._
![image](https://github.com/user-attachments/assets/cc6ad210-bbc7-40e1-acba-485e591283e0)




## 📌 **3. `grep` (Pattern Searching) Commands**
`grep` searches for patterns in files.

### **Search for a word in a file**
```sh
grep "word" file.txt
```

_Searches for "word" in `file.txt`._
![image](https://github.com/user-attachments/assets/b1ae44a3-1bab-4d71-8379-4a4f876da901)


### **Case-insensitive search**
```sh
grep -i "word" file.txt
```
![image](https://github.com/user-attachments/assets/b7a901ca-6df4-4dd0-95d4-170240572007)

### **Find whole word matches**
```sh
grep -w "word" file.txt
```
![image](https://github.com/user-attachments/assets/f5bec461-0ff7-46da-855e-f73f80371f12)

### **Search recursively in a directory**
```sh
grep -r "word" /path/to/directory
```

### **Find lines that do NOT match a pattern**
```sh
grep -v "word" file.txt
```
_Excludes lines containing "word"._

![image](https://github.com/user-attachments/assets/cfcd6f8b-5abf-4500-9f0a-22f48906d74e)


---


