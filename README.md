macOS_CLI_Cleaning
Cleaning Hard Drive &amp; Purging Unneeded Files
---

# **Automating System Management with Bash: A Hands-on Approach**  

## **Harnessing the Power of Bash for Workflow Efficiency**  

As a developer, strategist, and systems thinker, I’m always looking for ways to optimize workflows and automate repetitive tasks. While high-level scripting languages like Python and automation tools like Ansible are excellent for infrastructure management, **Bash remains one of the most efficient and lightweight tools for system administration, automation, and task execution.**  

Over the years, I’ve developed a **practical working knowledge of Bash**, leveraging it for system cleanup, file management, and task automation. In this post, I’ll walk through my recent hands-on work in Bash—demonstrating my ability to tackle real-world system challenges efficiently.  

---

## **Using Bash to Manage System Files & Optimize Storage**  

### **Identifying and Removing Large Files**  
A common issue that many professionals face is **disk bloat**—unused files accumulating over time and consuming valuable storage. I tackled this by using Bash to **identify, review, and remove large files** efficiently:  

```bash
find ~ -type f -size +500M -exec ls -lh {} + | sort -rh -k5 | head -20
```
✅ This script finds and lists **the largest 20 files** in my home directory, making it easy to review before deletion.  

To **delete old files** safely, I used:  

```bash
find ~/Downloads -type f -mtime +30 -exec rm -v {} \;
```
✅ This command finds and removes files older than 30 days in my **Downloads folder**, ensuring my system stays clean.  

---

### **Automating System Cleanup with Bash Scripts**  
Rather than manually running multiple commands, I streamlined my workflow by writing a **Bash script** that clears caches, removes temporary files, and optimizes storage:  

```bash
#!/bin/bash
echo "Cleaning system caches and old files..."

# Remove user caches
rm -rf ~/Library/Caches/*

# Remove files older than 30 days from Downloads & Trash
find ~/Downloads -type f -mtime +30 -exec rm -v {} \;
find ~/.Trash -type f -mtime +30 -exec rm -v {} \;

echo "✅ System cleanup complete!"
```
This script ensures that my system remains optimized **without manual intervention**, saving time and maintaining performance.  

---

## **Leveraging Bash for System Insights & Logs**  

### **Checking Disk Usage Efficiently**  
To keep track of storage usage, I used the following **disk usage (du) and sort combination**:  

```bash
du -ah ~ | sort -rh | head -20
```
✅ This command efficiently identifies the **largest files and directories**, allowing me to pinpoint where storage is being consumed.  

For monitoring **purgeable storage** and system snapshots:  

```bash
diskutil info / | grep "Purgeable"
```
✅ This command helps track macOS **purgeable files**, which can be manually cleared for more space.  

---

## **Automating & Scheduling Tasks with Cron Jobs**  
To ensure system cleanup happens regularly, I used **cron jobs** to schedule automation:  

1️⃣ Open the cron job editor:  
```bash
crontab -e
```
2️⃣ Add the following line to **run my cleanup script every Sunday at midnight**:  
```bash
0 0 * * 0 ~/cleanup.sh
```
✅ This ensures my system stays optimized **without manual intervention** every week.  

---

## **Handling System Restrictions & MacOS Security (SIP)**  
During this process, I encountered **macOS System Integrity Protection (SIP)** preventing access to certain system files. Instead of disabling SIP, I worked around it by:  

- **Granting Full Disk Access to Terminal** (via System Settings).  
- Using `tmutil thinlocalsnapshots / 10000000000 4` to **remove Time Machine local snapshots**.  
- Running `mkfile -n 10g ~/bigfile` and deleting it to force macOS to clear purgeable space.  

These solutions ensured **safe and effective system maintenance without compromising security**.  

---

## **Why Bash? A Startup & Enterprise Perspective**  

For **startups and enterprises**, Bash scripting remains an essential tool for:  

✔ **Automating DevOps workflows**—log rotation, backups, package installations.  
✔ **Managing cloud instances**—automating AWS, GCP, and Azure tasks.  
✔ **Optimizing CI/CD pipelines**—integrating with Jenkins, GitHub Actions, and Kubernetes.  
✔ **Server & user management**—handling provisioning, permissions, and cleanup.  

While I work extensively with cloud automation tools like Terraform and Ansible, **Bash remains a core skill in my technical toolkit** for handling tasks quickly and efficiently.  

---

## **Final Thoughts & Next Steps**  

Through these exercises, I demonstrated my ability to:  

✅ **Use Bash effectively** for system maintenance and storage optimization.  
✅ **Write automation scripts** to eliminate manual work.  
✅ **Solve real-world system challenges** while navigating security restrictions.  
✅ **Leverage Bash within larger automation workflows** to enhance productivity.  

You can check out the full **Bash scripts, logs, and steps I used** in my GitHub repository: **https://github.com/DTheArtist/macOS_CLI_Cleaning/**  

Bash is just one of the many tools in my technical stack, but its impact on automation and efficiency is undeniable. Whether handling infrastructure, DevOps, or startup workflows, **I thrive in designing scalable, automated solutions** to keep systems running smoothly.  

🚀 **Looking for an engineer, product strategist, or automation expert?** Let's talk!  
