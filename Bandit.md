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
