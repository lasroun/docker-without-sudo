# docker-without-sudo

This project explains how to configure your system to use Docker without requiring `sudo` for every command.  
By default, Docker requires root privileges because the Docker daemon runs as `root`.  
Granting your user access to the `docker` group allows running Docker commands directly.

---

## Prerequisites

- A Linux-based system with Docker installed
- User account with `sudo` privileges

---

## Steps

```bash
getent group docker
```

If it does not exist, create it:

```bash
sudo groupadd docker
```

Add your user to the docker group

```bash
sudo usermod -aG docker $USER
```

Apply the changes

```bash
newgrp docker
```

Verify

```bash
docker ps
```

You should now see the list of containers without using sudo.
