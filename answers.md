## 🟢 SECTION 1 — Orient Yourself (10 marks)

### ** Task 1 **: Print your current directory, your username, and full OS and kernel details — three separate commands. What does each command tell you? Why does a DevSecOps engineer run these three things first when SSHing into an unknown server — especially regarding kernel CVEs?

** Used Command : **

  1. `pwd `                   :  to print the current directory
  2. `whoami `                :  to rpint the username
  3. `cat /etc/os-release`    :  to print full os and kernel details 

![screenshot reference](/images/q1.png)

- Each of these commands should we run by a devsecops engineer into an unknown server because:
    1. pwd to see from where we are beginning so as to be sure that we are looking for a file or directory at the right place
    2. whoami to see the different rights we can have
    3. cat /etc/os-release to see all the details about 


## Task: List the contents of the root directory — the very top of the Linux filesystem.answers.md: Pick five directories from the output and explain each one's purpose. What is the Filesystem Hierarchy Standard (FHS) and why does it exist? What breaks on a shared production server without it?


