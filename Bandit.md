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
  
  **Explanation:** Using the Relative/Absolute path ensures that files starting with `-` are properly referenced and avoids misinterpretation as an option or argument."
</details>  

<details>
  <summary> Level 3 </summary>  

  The password for the next level is stored in a file called `--spaces in this filename--` located in the home directory.  
  ```
  cat ./'--spaces in this filename--'
  ```   
  <img width="490" height="43" alt="image" src="https://github.com/user-attachments/assets/384374c8-e638-4278-a975-90bb28322fad" />
  
  **Explanation:** To avoid the command treating each word as a separate file, enclose the filename with spaces in single quotes.
</details>  

<details>
  <summary> Level 4 </summary>  

  The password for the next level is stored in a **hidden file** in the `inhere` directory.  
  ```
  ls -la
  ```   
  <img width="615" height="157" alt="image" src="https://github.com/user-attachments/assets/92f86090-b51c-460d-b090-9a4d812f545a" />
  
  **Explanation:** Use the `-a` switch with the `ls` command to list all files, including hidden ones.
</details> 

<details>
  <summary> Level 5 </summary>  

  The password for the next level is stored in the **only human-readable file** in the `inhere` directory. Tip: if your terminal is messed up, try the “reset” command.
  ```
  file ./-*
  ```   
  <img width="764" height="215" alt="image" src="https://github.com/user-attachments/assets/82664100-77a6-45f1-a337-8694e8c7ad37" />
  
  **Explanation:** Use the `file` command to determine the file type. The `*` wildcard can be used to refer to all files.
</details> 

<details>
  <summary> Level 6 </summary>  

  The password for the next level is stored in a file somewhere under the `inhere` directory and has all of the following properties:
  - human-readable
  - 1033 bytes in size
  - not executable
  ```
  find . -size 1033c ! -executable | xargs file | grep ASCII
  ```   
  <img width="758" height="48" alt="image" src="https://github.com/user-attachments/assets/42d86d2c-defb-4ac3-a852-c5b5119daa6b" />
  
  **Explanation:** Use the `find` command with the `-size` and `-executable` flags, then run `file` on them and filters results for ASCII text files.
</details> 

<details>
  <summary> Level 7 </summary>  

  The password for the next level is stored somewhere on the server and has all of the following properties:
  - owned by user bandit7
  - owned by group bandit6
  - 33 bytes in size
  ```
  find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
  ```   
  <img width="684" height="43" alt="image" src="https://github.com/user-attachments/assets/53c08633-7107-4ad6-a9e0-cfac0a1b9b6e" />
  
  **Explanation:** Use the `find` command with the `-user`, `-group`, and `-size` flags and redirect errors to `/dev/null`.
</details> 

<details>
  <summary> Level 8 </summary>  

  The password for the next level is stored in the file `data.txt` next to the word **millionth**
  ```
  cat data.txt | grep millionth
  ```   
 <img width="446" height="41" alt="image" src="https://github.com/user-attachments/assets/4cf2b2ab-8393-4f12-8d3b-ce4cb2ef2079" />

  **Explanation:** Print the contents of `data.txt` and filter out only the line containing the word **millionth** with `grep`
</details> 

<details>
  <summary> Level 9 </summary>  

  The password for the next level is stored in the file `data.txt` and is the only line of text that occurs only once.
  ```
  sort data.txt | uniq -u
  ```   
 <img width="385" height="45" alt="image" src="https://github.com/user-attachments/assets/288bbb46-8c2d-4876-b422-28d2c0272977" />

  **Explanation:** Use `uniq` with the `-u` flag to print all unique lines. Uniq only checks adjacent lines, so sort the file first. 
</details> 

<details>
  <summary> Level 10 </summary>  

  The password for the next level is stored in the file `data.txt` in one of the few human-readable strings, preceded by **several ‘=’ characters.**
  ```
  strings data.txt | grep ==
  ```   
 <img width="416" height="99" alt="image" src="https://github.com/user-attachments/assets/634df51b-40c2-455e-be4e-e900473fe1f4" />

  **Explanation:** Use `strings` to print out all the human-readable text. With `grep` filter out the text containing `==` (I used 2 since we don't know how many is several).
</details> 

<details>
  <summary> Level 11 </summary>  

  The password for the next level is stored in the file `data.txt`, which contains base64 encoded data.
  ```
  cat data.txt | base64 -d
  ```   
 <img width="450" height="42" alt="image" src="https://github.com/user-attachments/assets/c2cd9e37-2dfc-4b00-8971-d5f02a614f89" />

  **Explanation:** Use `base64` with the `-d` flag to decode the base64 encoded data.
</details>

<details>
  <summary> Level 12 </summary>  

  The password for the next level is stored in the file `data.txt`, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.
  ```
  cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
  ```   
 <img width="542" height="42" alt="image" src="https://github.com/user-attachments/assets/0031ae47-bf0a-4139-94e4-67cbdf7fccc3" />

  **Explanation:** Use `tr` to translate (rotate) the letters. So, "A-Z" maps to "N-ZA-M" and "a-z" to "n-za-m"
</details>

<details>
  <summary> Level 13 </summary>  

  The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or   better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)
  ```
  file {File_Name}
  mv {Old_Name} {New_Name}
  gzip -d {File_name}.gz
  bzip2 -d {File_name}.bz2
  tar -xf {File_name}.tar
  ```   
 <img width="443" height="79" alt="image" src="https://github.com/user-attachments/assets/ced6e78a-2523-45a4-ad92-f704e21a987d" />

  **Explanation:** Use the `file` command to check what type of file it is. Us the `mv` command to rename the files to match the required format and decompress the file using the related commands, until you get a human readable file.
</details>

<details>
  <summary> Level 14 </summary>  

  The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname       that refers to the machine you are working on
  ```
  ssh bandit14@bandit.labs.overthewire.org -p 2220 -i sshkey.private
  ```   
 <img width="933" height="136" alt="image" src="https://github.com/user-attachments/assets/1f0e270b-1de0-41d8-97a2-51134b78b6c5" />

  **Explanation:** Use the `ssh` command with the `-i` flag to login using the private key of **bandit14.** The passwords can be found in `/etc/bandit_pass/`.
</details>


