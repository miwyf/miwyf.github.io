---
title: docker
date: 2022-08-11 16:56:58
tags:
      - docker
      - docker compose
categories:
      - Docker
description: "Docker安装, docker compose安装, docker镜像源修改, 常用docker指令"
---

# Docker

[Install Docker Desktop on Debian | Docker Documentation](https://docs.docker.com/desktop/install/debian/)

# Install Docker Engine on Debian

[Install Docker Engine on Debian | Docker Documentation](https://docs.docker.com/engine/install/debian/#set-up-the-repository)

#### Set up the repository

1.Update the `apt` package index and install packages to allow `apt` to use a repository over HTTPS:

```shell
 sudo apt-get update
 sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

2.Add Docker’s official GPG key:

```shell
 sudo mkdir -p /etc/apt/keyrings
 curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

3.Use the following command to set up the repository:

```shell
  echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

#### Install Docker Engine

1.Update the `apt` package index, and install the *latest version* of Docker Engine, containerd, and Docker Compose, or go to the next step to install a specific version:

```shell
 sudo apt-get update
 sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
 docker compose version
```

# 修改Docker Hub镜像源

 在配置文件 `/etc/docker/daemon.json` 中加入：

[Docker Hub 源使用帮助 — USTC Mirror Help 文档](http://mirrors.ustc.edu.cn/help/dockerhub.html)

```json
{
  "registry-mirrors": ["https://docker.mirrors.ustc.edu.cn/"]
}
```

```json
{
    "registry-mirrors": [
        "https://docker.mirrors.ustc.edu.cn",
        "http://hub-mirror.c.163.com",
        "https://registry.docker-cn.com"
    ]
}
```

重新启动 dockerd：

```shell
sudo systemctl restart docker
docker info
```



# Install Docker Compose CLI plugin

[Install Docker Compose CLI plugin | Docker Documentation](https://docs.docker.com/compose/install/compose-plugin/#install-using-the-repository)

### 1.Docker Compose V2 Install using the repository

1.Update the `apt` package index, and install the *latest version* of Docker Compose:

```shell
 sudo apt-get update
 sudo apt-get install docker-compose-plugin
```

2.Compose Switch

Compose Switch is a replacement to the Compose V1 `docker-compose` (python) executable. It translates the command line into Compose V2 `docker compose` then run the latter.

[docker/compose-switch (github.com)](https://github.com/docker/compose-switch)

```
curl -fL https://raw.githubusercontent.com/docker/compose-switch/master/install_on_linux.sh | sh
```

### 2.Docker Compose V1

```
curl -L https://github.com/docker/compose/releases/download/1.29.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

## Docker指令

### 复制容器文件

```
docker ps -a
docker cp a1190c88eb92:/app .
```

## 常用镜像

### 1.portainer

```sh
docker run -d --name=prtainer --restart=always \
    -p 9000:9000 \
    -v /var/run/docker.sock:/var/run/docker.sock \
    portainer/portainer
```

