## 🟢 SECTION 1 — Orient Yourself (10 marks)

> ** Task 1 **: Print your current directory, your username, and full OS and kernel details — three separate commands. What does each command tell you? Why does a DevSecOps engineer run these three things first when SSHing into an unknown server — especially regarding kernel CVEs?

** Used Command : **

  1. `pwd `                   :  to print the current directory
  2. `whoami `                :  to rpint the username
  3. `cat /etc/os-release`    :  to print full os and kernel details 

![screenshot reference](/images/q1.png)

- Each of these commands should we run by a devsecops engineer into an unknown server because:
    1. pwd to see from where we are beginning so as to be sure that we are looking for a file or directory at the right place
    2. whoami to see the different rights we can have
    3. cat /etc/os-release to see all the details about 


> * Task 2 * : List the contents of the root directory — the very top of the Linux filesystem. Pick five directories from the output and explain each one's purpose. What is the Filesystem Hierarchy Standard (FHS) and why does it exist? What breaks on a shared production server without it?

** Used Command : `ls / ` **

![screenshot reference](/images/Q2.png)


> * Task 3 *: List your home directory twice — once the default way, then again revealing hidden files with full details (permissions, ownership, size). What is different between the two outputs? What makes a file hidden in Linux — is it a special type? Name two real hidden files found in a home directory and explain what they do.


## 🟡 SECTION 2 — Build the Environment (15 marks)

> ** Task 4 ** : Create the entire structure above in a single command — including all nested subdirectories. Then display the full tree to verify. 📸 Screenshot the tree. Which flag did you use and what does it do? What is brace expansion and how did it help here? Could you have done this without it — and would you want to?

> ** Task 5 **: Create these five empty files in a single command: configs/app.conf, configs/db.conf, logs/access/access.log, logs/errors/error.log, reports/weekly_report.txt. What does this command actually do beyond creating files? What happens if you run it on an existing file? Check ls -l before and after — what changes? Why does this behaviour matter in automation scripts?

> ** Task 6 **: List ~/projects/cyphercore/configs/ in long format with human-readable file sizes.  What do the file sizes tell you about the files you just created? Break down the permission string on one file — explain every character group. What does the -h flag add?

> ** Task 7 **: Display the full tree of ~/projects/cyphercore again. 📸 Screenshot it.  How is tree different from ls -R? When would a DevSecOps engineer run tree on a live server — what would they be looking for?


## 🟡 SECTION 3 — Write and Read Files

> ** Task 8 ** : Write each of the three log lines into logs/access/access.log using echo, appending each one. Read the file back to confirm all three lines exist. 📸 Screenshot. What is the difference between > and >>? Prove it — re-run the first echo with > instead of >>, then read the file. What happened? Restore the file. Why is confusing these two operators dangerous in a production log rotation script?

> ** Task 9 ** : Display the access log using two different reading commands — one from top to bottom, one from bottom to top.  What is the difference between the two? In a real incident, a log has 80,000 lines and the most recent events are at the bottom — which do you reach for first? What third command shows only the last 10 lines? (Research if needed.)

> ** Task 10 ** : Use heredoc notation to append all four lines into logs/errors/error.log in one operation. Read it back and 📸 screenshot. What is a heredoc and what does it solve over multiple echo commands? What is the difference between 'EOF' (quoted) and EOF (unquoted)? Set a variable DBNAME=cyphercore and test both — screenshot the outputs and explain what you observe. Why might someone on a compromised server prefer heredoc over opening nano or vim? What forensic traces does each method leave?

> ** Task 11 ** : Open the error log using two different pager commands. Navigate and quit each one. Key differences between the two? Which loads the entire file into memory first? On a server with 512MB RAM and a 3GB log — which do you use? List three keyboard shortcuts for less: how to search, jump to the end, and quit.

## 🟡 SECTION 4 — Move and Clean Up (10 marks)

> ** Task 12 ** : Copy the error log to the archive folder as error_2025-06-02.log; Rename the access log to access_2025-06-02.log. Fundamental difference between the two commands used? After renaming — does the original filename still exist? Verify with ls and 📸 screenshot. Does copying a large file duplicate all data on disk immediately?

> ** Task 13 ** : Create an empty directory reports/temp_drafts
Remove it using the command designed for empty directories
Attempt to remove the entire logs/ directory using that same command
answers.md: What happened when you tried to remove logs/? Why? Difference between rmdir and rm -r? What makes rm -rf dangerous and what rule should every engineer follow before running it?

> ** Task 14 ** : Display the full tree of ~/projects/cyphercore. 📸 Screenshot. Does the structure match Abena's original sticky note? Why does a clean, predictable directory structure matter for automation scripts, log agents, and security monitoring tools?


## 🔴 SECTION 5 — Links and Inodes

> ** Task 15 ** : Write three lines into configs/db.conf: DB_HOST=10.0.0.10, DB_PORT=5432, DB_NAME=cyphercore_prod
Create a hard link to it in the same directory named db_hardlink.conf
List the configs directory showing inode numbers alongside full file details
📸 Screenshot the output.

💡 Hint: The flag that shows inode numbers with ls -l is -i.

answers.md: What do you notice about the inode numbers of both files? What does the link count (third column) represent? What is an inode in your own words?


> ** Task 16 ** : Delete the original db.conf. Then read the hard link file. Is the data still there? Explain why using inodes and link counts. What would need to happen for the data to be permanently deleted? Check ls -li again — what changed in the link count? How could an attacker use hard links to hide data on a compromised system? 

> ** Task 17 ** : Write some content into configs/app.conf
Create a symbolic link to it inside ~/projects/cyphercore/ named app_config_link
List ~/projects/cyphercore/ showing full details including link targets
Delete the original app.conf and try to read the symlink
📸 Screenshot both the listing and the failed read.
 What character in the listing identifies a symbolic link? What happened when you read the broken link — what is this called? Why does a dangling symlink in a deployment pipeline cause failures that are hard to debug at 2 AM?



> ** Task 18 ** : 


## 🔴 SECTION 6 — Data Streams and Redirection (15 marks)

> ** Task 19 ** : Task:

Run a single ls targeting two paths: one that exists (logs/) and one that does not
Redirect normal output to reports/stdout_output.txt
Redirect error output to reports/stderr_output.txt
Read both files back
📸 Screenshot the outputs.

💡 Hint: > is shorthand for 1>. Think of 2>&1 as "send stream 2 to wherever stream 1 is going."

answers.md:

Which content landed where and why?
Name all three streams, their numbers, and what each carries.
What does 2> mean specifically?
Run the same command with 2>&1 | cat instead. Explain what 2>&1 does and where you'd use it in a real deployment script.




> ** Task 20 ** : 

> ** Task 21 ** : Display the final tree of ~/projects/cyphercore. 📸 Screenshot it. Look at everything you built today — the structure, logs, archives, links, report. How does each connect to what a real DevSecOps engineer does daily? Pick two commands from today that changed how you think about Linux and explain why they matter beyond this bootcamp.

