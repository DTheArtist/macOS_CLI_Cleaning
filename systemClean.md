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

# 3 Delete Large Files (Over 500MB)
bash
#!/bin/bash
```
echo "Finding large files over 500MB..."
find ~ -type f -size +500M -exec ls -lh {} \;
echo "Manually review and delete if necessary."
```
* Optional: sort -rh -k5: Sorts by file size in descending order. *
```
find ~ -type f -size +500M -exec ls -lh {} + | sort -rh -k5
```

After running the command, carefully review the files.
If you recognize files you no longer need, take note of their paths.

* To delete them Maunally:
* Delete Specific Files One by One
To remove a specific file, use:

bash
```
rm -i /path/to/file
```


* To delete them automatically:

bash
```
find ~ -type f -size +500M -delete
```

# 4️ Clean Log Files
bash
#!/bin/bash
```
echo "Cleaning log files..."
sudo rm -rf /var/log/*
echo "✅ Logs cleaned"
```


