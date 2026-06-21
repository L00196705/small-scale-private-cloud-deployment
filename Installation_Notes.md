# Installation Notes

All virtual machines were created using VMware.

The following distributions were installed:

- Lubuntu 26.04 LTS
- Xubuntu 26.04 LTS
- Linux Lite 7.8

The "Erase disk and install" option was selected for all installations to ensure consistency.

During the first installation attempt, Xubuntu failed to boot correctly due to a different partitioning option being selected. The VM was recreated and reinstalled using "Erase disk and install", after which the system operated normally.

Linux Lite requested removal of the installation medium after installation before rebooting.

Docker installation was completed successfully on all three distributions without dependency issues.

The nginx container deployed successfully and the default "Welcome to nginx" page was accessible through the browser.


## Docker Installation

### Install Required Packages

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
```

### Add Docker Repository Key

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### Add Docker Repository

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu noble stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Install Docker

```bash
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io -y
```

### Verify Docker Installation

```bash
docker --version
```

### Deploy nginx Container

```bash
sudo docker run --name test-nginx -p 8080:80 -d nginx
```

### View Running Containers

```bash
sudo docker ps
```
