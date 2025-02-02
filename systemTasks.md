Step 3: Set Up a Scheduled Task (Cron Job)
To automate these cleanup scripts, add them to a cron job:

Open Terminal and type:
bash
```
crontab -e
```

Add this line to run the cleanup every Sunday at midnight:
bash
```
0 0 * * 0 ~/cleanup.sh
```

🔹 Step 4: Use Built-in macOS Tools
Optimize Storage

Go to Apple Menu > About This Mac > Storage > Manage
Use "Optimize Storage" and "Reduce Clutter" to remove large files.
Clear Mail Attachments

bash
```
rm -rf ~/Library/Containers/com.apple.mail/Data/Library/Mail\ Downloads/*
```
Remove Old iOS Backups

bash
```
rm -rf ~/Library/Application\ Support/MobileSync/Backup/*
```

🔹 Step 5: Install & Automate Cleanup Tools
🔹 Homebrew Cleanup
Install Homebrew and clean old packages:

bash
```
brew cleanup
```

🔹 Step 6: Automate Deletion of Specific File Types
Delete old .dmg, .zip, and .log files:

bash
```
find ~/Downloads -type f \( -name "*.dmg" -o -name "*.zip" -o -name "*.log" \) -mtime +30 -exec rm -v {} \;
```
