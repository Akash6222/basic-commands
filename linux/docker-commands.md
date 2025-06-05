# Docker Commands Overview

> A quick reference guide for common Docker commands and their usage.

---

### 1. Run as Root
```bash
docker exec -u 0 -it <container> /bin/bash
```
- **What it does**: Opens a root shell inside a running container.
- **Key options**:
  - `-u 0`: Runs as root user.
  - `-it`: Starts an interactive terminal.

---

### 2. Check Resource Usage
```bash
docker stats <container> --no-stream
```
- **What it does**: Shows memory, CPU, and other resource usage for a container.
- **Key option**:
  - `--no-stream`: Displays a single snapshot instead of continuous updates.

---

### 3. Container Management
#### Stop All Containers
```bash
docker stop $(docker ps -aq)
```
- **What it does**: Stops all running containers.
- **How it works**: Uses `docker ps -aq` to list all container IDs and stops them.

#### Remove All Containers
```bash
docker rm $(docker ps -aq)
```
- **What it does**: Deletes all containers (running or stopped).
- **How it works**: Lists all container IDs with `docker ps -aq` and removes them.

#### Remove All Volumes
```bash
docker volume rm $(docker volume ls -q)
```
- **What it does**: Deletes all Docker volumes.
- **How it works**: Lists all volume names with `docker volume ls -q` and removes them.

---

### 4. Check Last 100 Logs
```bash
docker logs <container> --tail 100
```
- **What it does**: Displays the last 100 log lines from a container.
- **Key option**:
  - `--tail 100`: Limits the output to the most recent 100 lines.

---

### 5. Mount a Volume
```bash
-v /host/path:/container/path
```
- **What it does**: Maps a directory on your host machine to a directory inside the container.
- **Why use it**: Allows persistent storage or sharing of files between the host and container.

---

### 6. Limit CPU and Memory Usage
```bash
--cpus="1" --memory="1g" --memory-swap="2g"
```
- **What it does**:
  - `--cpus="1"`: Limits the container to use **1 CPU core**.
  - `--memory="1g"`: Restricts the container to use **1 GB of RAM**.
  - `--memory-swap="2g"`: Allows the container to use up to **2 GB of total memory** (RAM + swap).

---

### 7. Run a Container with Restart Policy
```bash
docker run --restart always -d -t <image>
```
- **What it does**:
  - `--restart always`: Ensures the container restarts automatically if it stops, crashes, or the system reboots.
  - `-d`: Runs the container in **detached mode** (in the background).
  - `-t`: Allocates a pseudo-TTY for interactive processes.

---

### 8. Example Command
```bash
docker run --name <container_name> --restart always -v /host/path:/container/path -d -t --cpus="1" --memory="1g" --memory-swap="2g" <image>
```
- **Purpose**:
  - Starts a container with resource limits, a mounted volume, and automatic restarts.

---

### Important Considerations
- **Mounting (`-v`)**: Useful for sharing configuration files or data between the host and container.
- **Resource Limits**: Prevent containers from consuming excessive CPU or memory, ensuring system stability.
- **Restart Policy**: Keeps critical services running without manual intervention.
- **Be cautious**: Commands like `docker rm`, `docker stop`, and `docker volume rm` are **destructive** and cannot be undone.
- **Use sparingly**: Ensure you don’t need the containers or volumes before removing them.

---
```
