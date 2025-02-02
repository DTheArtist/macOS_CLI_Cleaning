Before deleting files, let's check disk usage:

bash
```
du -sh ~/*
```

Or for more details:

bash
```
sudo du -hxd 1 / | sort -hr | head -n 20
```
This will show the top 20 biggest directories on your system.
