---
date: 2023-09-30
tags:
  - windows
  - webdev
---
[[Docker]]

Setting up Docker on a Windows machine without using Docker Desktop requires a few more steps, mainly because Docker is natively a Linux technology. Here's a guide to setting up Docker on Windows without Docker Desktop:

### 1. **Install Windows Subsystem for Linux (WSL)**:

The Windows Subsystem for Linux lets you run a Linux distribution alongside your existing Windows installation.

1. Open PowerShell as Administrator and run:
```bash
wsl --install
```

2. Restart your machine if required.

3. Once restarted, open the Microsoft Store, search for a Linux distribution (like Ubuntu), and install it.

4. Launch the installed Linux distribution to set it up for the first time (you'll set a username and password).

### 2. **Install Docker on WSL**:

Now, you'll be installing Docker inside the WSL environment:

1. Open your Linux distribution terminal.

2. Update the package list and install required dependencies:
```bash
sudo apt update && sudo apt upgrade
sudo apt-get install apt-transport-https ca-certificates curl software-properties-common
```

3. Add Docker’s GPG key:
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

4. Add Docker's repository:
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

5. Update the package list again and install Docker:
```bash
sudo apt update
sudo apt install docker-ce
```

6. Start Docker:
```bash
sudo service docker start
```

### 3. **Install Docker Compose (Optional)**:

If you want Docker Compose, you can install it too:

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```

### 4. **Post-Installation Steps**:

1. Add your user to the `docker` group to run Docker commands without `sudo`:
```bash
sudo usermod -aG docker $USER
```
Exit the terminal and start it again to reflect this change.

2. Test Docker:
```bash
docker --version
docker run hello-world
```

### 5. **Accessing Docker from Windows**:

Since Docker is installed in the Linux subsystem, if you want to work with your Windows files, make sure to navigate to the `/mnt/` directory in WSL where your Windows drives are mounted (e.g., `/mnt/c/` for C: drive).

### Note:

While this setup lets you run Docker without Docker Desktop, there are differences in terms of performance, networking, and convenience. Docker Desktop offers tight integration, optimizations, and GUI that can make certain tasks easier. If the licensing is the primary concern, you might want to explore other options or virtualization methods that can fit your needs better.