# Introduction
The **[Bandit wargame](https://overthewire.org/wargames/bandit/)** is a CTF-style game to learn Linux basics while having fun. It currently has 34 levels (with more possibly added).   
Start at **[Level 0](https://overthewire.org/wargames/bandit/bandit0.html)** and solve each level to find the password/flag that unlocks the next one.  

# Writeups for all Levels 
<details>
  <summary> Level 0 </summary>  

  SSH into the game using the credentials given.
  ```
  ssh bandit0@bandit.labs.overthewire.org -p 2220
  ```
</details>  

<details>
  <summary> Level 1 </summary>  

  The password for the next level is stored in a file called `readme` located in the home directory.  
  ```
  cat readme
  ```  
  <img width="765" height="247" alt="image" src="https://github.com/user-attachments/assets/ba210c00-0eb2-4aed-970a-1cdf4d61db71" />  
  
  Now, we can SSH into **bandit1** for the next level.  
  ```
  ssh bandit1@bandit.labs.overthewire.org -p 2220
  ```
</details>  

<details>
  <summary> Level 2 </summary>  

  The password for the next level is stored in a file called `-` located in the home directory.   
  ```
  cat ./-
  ```   
  <img width="302" height="43" alt="image" src="https://github.com/user-attachments/assets/17c9d81f-3484-4a21-a82b-24c89c961f86" />
  
  **Explaination:** Using the Relative/Absolute path ensures that files starting with `-` are properly referenced and avoids misinterpretation as an option or argument."
</details>  

<details>
  <summary> Level 3 </summary>  

  The password for the next level is stored in a file called `--spaces in this filename--` located in the home directory.  
  ```
  cat ./'--spaces in this filename--'
  ```   
  <img width="490" height="43" alt="image" src="https://github.com/user-attachments/assets/384374c8-e638-4278-a975-90bb28322fad" />
  
  **Explaination:** To avoid the command treating each word as a separate file, enclose the filename with spaces in single quotes.
</details>  

<details>
  <summary> Level 4 </summary>  

  The password for the next level is stored in a **hidden file** in the `inhere` directory.  
  ```
  ls -la
  ```   
  <img width="615" height="157" alt="image" src="https://github.com/user-attachments/assets/92f86090-b51c-460d-b090-9a4d812f545a" />
  
  **Explaination:** Use the `-a` switch with the `ls` command to list all files, including hidden ones.
</details> 

<details>
  <summary> Level 5 </summary>  

  The password for the next level is stored in the **only human-readable file** in the `inhere` directory. Tip: if your terminal is messed up, try the “reset” command.
  ```
  file ./-*
  ```   
  <img width="764" height="215" alt="image" src="https://github.com/user-attachments/assets/82664100-77a6-45f1-a337-8694e8c7ad37" />
  
  **Explaination:** Use the `file` command to determine the file type. The `*` wildcard can be used to refer to all files.
</details> 

<details>
  <summary> Level 6 </summary>  

  The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
  - human-readable
  - 1033 bytes in size
  - not executable
  ```
  find . -size 1033c ! -executable | xargs file | grep ASCII
  ```   
  <img width="758" height="48" alt="image" src="https://github.com/user-attachments/assets/42d86d2c-defb-4ac3-a852-c5b5119daa6b" />
  
  **Explaination:** Use the `find` command with the `-size` and `-executable` flags, then run `file` on them and filters results for ASCII text files.
</details> 
