Automate Cleaning with Scripts
Here are some scripts to remove unneeded files automatically.

# 1 Clean System Caches
You can delete macOS system caches safely:

bash
#!/bin/bash
```
echo "Cleaning System Caches..."
sudo rm -rf ~/Library/Caches/*
sudo rm -rf /Library/Caches/*
sudo rm -rf ~/Library/Application\ Support/Slack/Cache/*
sudo rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Cache/*
echo "✅ Caches Cleared"
```

# 2️ Remove Large & Old Files
This script deletes files over 365 days old from Downloads, Trash, and Temp folders:

bash
#!/bin/bash
```
echo "Deleting old files..."
find ~/Downloads -type f -mtime +365 -exec rm -v {} \;
find ~/.Trash -type f -mtime +365 -exec rm -v {} \;
find /private/tmp -type f -mtime +365 -exec rm -v {} \;
echo "✅ Old files deleted"
```

3️⃣ Delete Large Files (Over 500MB)
bash
Copy
Edit
#!/bin/bash
echo "Finding large files over 500MB..."
find ~ -type f -size +500M -exec ls -lh {} \;
echo "Manually review and delete if necessary."
To delete them automatically:

bash
Copy
Edit
find ~ -type f -size +500M -delete
4️⃣ Clean Log Files
bash
Copy
Edit
#!/bin/bash
echo "Cleaning log files..."
sudo rm -rf /var/log/*
echo "✅ Logs cleaned"
