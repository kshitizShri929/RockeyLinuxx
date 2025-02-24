### 📝 **Detailed Linux Command Notes**

---

#### 🔍 **System Information & User Commands**

- **`man [command]`**  
  Displays the manual page for a command. Use `/` to search within the manual and `q` to quit.  
  _Example:_ `man ls` (Shows details about the `ls` command)  
![image](https://github.com/user-attachments/assets/1117ef88-a936-43be-b7f0-024d362ed362)

- **`history`**  
  Lists previously executed commands with line numbers.  
  _Shortcut:_ Use `!n` to repeat command number `n` (from history).  
  _Example:_ `!45` (Executes command number 45 from the history)
  ![image](https://github.com/user-attachments/assets/55255ffa-c5a4-4bfc-9092-8cf34ad3cacf)


- **`clear`**  
  Clears the terminal screen but doesn’t remove command history.  
  _Shortcut:_ `Ctrl + L` does the same thing.

- **`echo [text/variable]`**  
  Displays text or variable value on the terminal.  
  _Example:_  
  - `echo "Hello, World!"` (Displays text)  
  - `echo $HOME` (Displays the value of the HOME environment variable)
  ![image](https://github.com/user-attachments/assets/424634ae-2a71-415c-ad83-90e72cdad110)



- **`id`**  
  Displays user ID (UID), group ID (GID), and the groups the user belongs to.  
  _Example:_ `id chandan`

  ![image](https://github.com/user-attachments/assets/9b1fe238-3f9a-41c3-af77-cf7c1dbe51d5)


- **`who`**  
  Shows who is currently logged in.  
  _Example:_ `who` (Displays all logged-in users)  

- **`whoami`**  
  Displays the current username. Useful in scripts to confirm execution privileges.

![image](https://github.com/user-attachments/assets/527e11e4-6bf0-4fb7-a32d-24ce731cd5e6)


#### 📂 **File & Directory Management Commands**

- **`pwd`** *(Print Working Directory)*  
  Shows the current directory’s absolute path.  
  _Example:_ `/home/chandan/projects`  
  ![image](https://github.com/user-attachments/assets/4e068716-8edc-4f07-81e2-98286caba281)

- **`cd [directory]`** *(Change Directory)*  
  Moves between directories.  
  _Examples:_  
  - `cd /home/chandan` (Go to an absolute path)  
  - `cd ..` (Move up one level)  
  - `cd -` (Go back to the previous directory)  
  - `cd ~` (Go to the home directory)  
![image](https://github.com/user-attachments/assets/e8f26a45-b940-4904-afc8-6d010c79e67b)

- **`ls [options]`** *(List Directory Contents)*  
  Lists files and directories.  
  _Common options:_  
  - `ls -l` (Detailed list view with permissions)  
  - `ls -a` (Lists hidden files)  
  - `ls -lh` (Human-readable file sizes)
 
    ![image](https://github.com/user-attachments/assets/ebf03a61-4143-4b48-862e-d8aff3cbcb9b)


- **`mkdir [directory]`** *(Make Directory)*  
  Creates a new directory. Use `-p` to create nested directories.  
  _Example:_ `mkdir -p /home/chandan/projects/java`  
  ![image](https://github.com/user-attachments/assets/fd8f59b0-0d15-49ca-bb2a-d00954a8f2f0)

- **`touch [file]`** *(Create Empty File)*  
  Creates an empty file or updates the timestamp of an existing file.  
  _Example:_ `touch notes.txt`
  
  ![image](https://github.com/user-attachments/assets/7345dba7-4c1f-4da6-b950-3df5fea82e5e)


- **`rmdir [directory]`** *(Remove Empty Directory)*  
  Deletes an empty directory. Use `rm -r` for non-empty directories.  
  _Example:_ `rmdir old_logs`

  ![image](https://github.com/user-attachments/assets/78216039-5b8a-4f85-8e78-d682526d5d0c)


- **`mv [source] [destination]`** *(Move or Rename Files/Directories)*  
  Moves files or renames them if the destination path is in the same directory.  
  _Examples:_  
  - `mv file.txt /home/chandan/docs/` (Move)  
  - `mv file.txt file_renamed.txt` (Rename)  

![image](https://github.com/user-attachments/assets/a49ae47e-9253-4a6c-b854-085175603f39)


#### 📑 **File Viewing & Manipulation Commands**

- **`more [file]`** / **`less [file]`**  
  Displays the content of large files page by page.  
  _Differences:_  
  - `more`: Forward-only navigation.  
  - `less`: Allows forward and backward navigation (`q` to quit).
 
    ![image](https://github.com/user-attachments/assets/18d61265-44b7-4a3a-bc15-d5ae404a7f6e)

    ![image](https://github.com/user-attachments/assets/5f6ad988-4b7f-49c2-a35d-e697dc8dc7de)



- **`head [file]`**  
  Displays the first 10 lines of a file by default.  
  _Example:_ `head -n 20 log.txt` (Shows the first 20 lines)  

![image](https://github.com/user-attachments/assets/c62f93cd-cf28-448c-ba4d-3b2d6f85ae04)

- **`tail [file]`**  
  Displays the last 10 lines of a file by default.  
  _Options:_  
  - `tail -f [file]`: Continuously monitors a file (useful for logs).  
  - `tail -n 50 logs.txt`: Show the last 50 lines.

    ![image](https://github.com/user-attachments/assets/b862b545-a3f5-4542-a668-d28892893aba)


- **`cat [file]`** *(Concatenate and Display Files)*  
  Displays the full content of a file or merges multiple files.  
  _Example:_ `cat file1.txt file2.txt > merged.txt`

  ![image](https://github.com/user-attachments/assets/6988af5e-392b-4fd0-9351-3edf2a8c1f88)


---

#### 🔠 **Text Processing & Word Count Commands**

- **`sort [file]`**  
  Sorts the contents of a text file line by line.  
  _Options:_  
  - `sort -r [file]`: Sort in reverse order.  
  - `sort -n [file]`: Sort numerically.
    ![image](https://github.com/user-attachments/assets/06a84398-865e-48a5-9873-c0a8583226e4)
    ![image](https://github.com/user-attachments/assets/f699c26c-0f20-426b-93bb-9fef913b2c85)
    ![image](https://github.com/user-attachments/assets/d9a1fc58-a340-4580-a944-4b6df9821522)




- **`wc [file]`** *(Word Count)*  
  Counts the number of lines, words, and characters.  
  _Options:_  
  - `wc -l [file]`: Count lines.  
  - `wc -w [file]`: Count words.  
  - `wc -c [file]`: Count characters.  

![image](https://github.com/user-attachments/assets/3528883b-c6d1-480c-9de8-c3c035137f8c)


#### 🔎 **Searching & Finding Commands**

- **`find [directory] -name [filename]`**  
  Searches for files and directories recursively from the given directory.  
  _Examples:_  
  - `find /home/chandan -name "*.txt"` (Find all `.txt` files)  
  - `find . -type d` (Find all directories in the current folder
  
    ![image](https://github.com/user-attachments/assets/f1ddafee-2a16-46b3-a127-3bca85e5e017)


- **`grep [pattern] [file]`** *(Search Inside Files)*  
  Searches for patterns in a file.  
  _Examples:_  
  - `grep "error" logfile.txt` (Find lines containing "error")  
  - `grep -r "TODO" .` (Recursively search for "TODO" in the current directory)
    ![image](https://github.com/user-attachments/assets/5e895adc-0c44-4034-814a-e841410bb5fa)


https://www.geeksforgeeks.org/linux-commands-cheat-sheet/
