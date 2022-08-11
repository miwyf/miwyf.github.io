---
title: debian
date: 2022-08-11 20:46:16
tags:
      - debian
categories:
      - Debian
description: "Debian安装, 镜像源修改, 常用debian指令"
---

# Debian

## Debian apt (apt-get) 镜像源

使用中科大源 [Debian 源使用帮助 — USTC Mirror Help 文档](http://mirrors.ustc.edu.cn/help/debian.html)

```bash
# 备份原来的配置
cp -pv /etc/apt/sources.list /etc/apt/sources.list.bak
# 修改apt源地址为中科大学
sed -i -e 's/deb.debian.org/mirrors.ustc.edu.cn/g' -e 's/security.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
# 刷新缓存
apt update
```

使用163

```bash
# 备份原来的配置
cp -pv /etc/apt/sources.list /etc/apt/sources.list.bak
# 修改apt源地址为163
sed -i -e 's/deb.debian.org/mirrors.163.com/g' -e 's/security.debian.org/mirrors.163.com/g' /etc/apt/sources.list
# 刷新缓存
apt update
```

使用阿里云

```bash
# 备份原来的配置
cp -pv /etc/apt/sources.list /etc/apt/sources.list.bak
# 修改apt源地址为阿里云
sed -i -e 's/deb.debian.org/mirrors.aliyun.com/g' -e 's/security.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list
# 刷新缓存
apt update
```

使用华为云

```bash
# 备份原来的配置
cp -pv /etc/apt/sources.list /etc/apt/sources.list.bak
# 修改apt源地址为华为云
sed -i -e 's/deb.debian.org/mirrors.huaweicloud.com/g' -e 's/security.debian.org/mirrors.huaweicloud.com/g' /etc/apt/sources.list
# 刷新缓存
apt update
```

### 
