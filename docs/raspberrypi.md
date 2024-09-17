# Raspberrypi

## 地址

<https://mirrors.ustc.edu.cn/archive.raspberrypi.org/> 或
<https://mirrors.ustc.edu.cn/raspberrypi/>

## 说明

树莓派的 archive.raspberrypi.org 软件源，是由树莓派基金会提供的软件源，包括 ui 相关程序（如 Raspbian 的桌面环境 PIXEL DE）及部分由树莓派基金会为树莓派编写的软件，通常与 raspbian.raspberrypi.org（参考 [raspbian](raspbian.md)，旧版为 archive.raspbian.org）一起使用。

## 收录架构

- armhf
- arm64
- x86
- x86_64

## 收录版本

- wheezy
- jessie
- stretch
- buster
- bullseye
- bookworm

## 使用说明

!!! warning

    操作前请做好相应备份

一般情况下，将 `/etc/apt/sources.list.d/raspi.list`
 文件中默认的源地址
`http://archive.raspberrypi.org/`（bullseye 及之前版本）或者
`http://archive.raspberrypi.com/`（bookworm 及之后版本）替换为
`http://mirrors.ustc.edu.cn/raspberrypi/` 即可。

可以使用如下命令：

```shell
sudo sed \
  -e 's|http://archive.raspberrypi.org|http://mirrors.ustc.edu.cn/raspberrypi|g' \
  -e 's|http://archive.raspberrypi.com|http://mirrors.ustc.edu.cn/raspberrypi|g' \
  -i.bak \
  /etc/apt/sources.list.d/raspi.list
```

当然也可以直接编辑 `raspi.list` 文件（需要使用 sudo）。以下是 bookworm 的参考配置内容：

{% for release in debian_releases %}
=== "Raspbian {{ release.codename }}"

    ```debsources title="/etc/apt/sources.list.d/raspi.list"
    deb http://mirrors.ustc.edu.cn/raspberrypi/debian/ {{ release.codename }} main
    #deb-src http://mirrors.ustc.edu.cn/raspberrypi/debian/ {{ release.codename }} main
    ```
{% endfor %}

更改完 `raspi.list` 文件后请运行 `sudo apt-get update` 更新索引以生效。

!!! tip

    使用 HTTPS 可以有效避免国内运营商的缓存劫持，但 stretch 及老版本系统需要事先安装 `apt-transport-https`。

## 相关链接

- 树莓派链接

    官方主页

    :   <https://www.raspberrypi.org/>

    文档

    :   <https://www.raspberrypi.org/documentation/>

- 其他镜像帮助

    - [Raspberry Pi OS 镜像使用帮助](raspberry-pi-os-images.md)
    - [Raspbian 镜像使用帮助](raspbian.md)
