
### Troubleshooting Full Disk Storage on Ubuntu VPS

If your Ubuntu VPS disk storage is full and you're not able to identify what's consuming the space, follow these steps to pinpoint large files and directories:

## Step 1: Check Disk Usage
To check the overall disk usage, run the following command:

```bash
df -h
```

This command will display a summary of the file system, showing how much space is used, available, and the percentage of disk usage.

## Step 2: Find Large Directories
To locate which directories are consuming the most space, use:

```bash
du -h --max-depth=1 /
```

This command lists the sizes of directories at the root level (`/`). To further explore a large directory, rerun the command with the path of that directory. For example, if `/var` is taking up a lot of space, you can check its subdirectories with:

```bash
du -h --max-depth=1 /var
```

## Step 3: Identify Large Files
To directly locate files larger than 100MB, use:

```bash
find / -type f -size +100M -exec ls -lh {} \; | awk '{ print $NF ": " $5 }'
```

This will output a list of large files along with their sizes.

## Step 4: Check for Unnecessary Files
Sometimes, old log files or backups can consume a lot of space. You can check log files in `/var/log/` using:

```bash
sudo du -sh /var/log/*
```

This command will display the sizes of all files in the `/var/log/` directory.

## Step 5: Docker Cleanup (If Using Docker)
If you're using Docker, you can check for unused images and containers that may be consuming space:

```bash
docker system df
```

To clean up all unused Docker data, use:

```bash
docker system prune -a
```

By following these steps, you can identify the source of disk usage and take the necessary actions to free up space.
