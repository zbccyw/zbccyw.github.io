### 网卡设置

**eth → edit IPv4 → Manual**
> Subnet：网段/子网掩码（如：192.168.1.0/24）
> Address：IPv4地址（如：192.168.1.100）
> Gateway：网关地址（如：192.168.1.1）
> Name server：DNS地址（如：114.114.114.114，8.8.8.8）
> Search domains：（可不填）

### 修改源地址

默认地址：`http://cn.archive.ubuntu.com/ubuntu/`
修改为
阿里云地址：`http://mirrors.aliyun.com/ubuntu/`

### 开启root用户登录

- 给root账户设置密码：
```auto
sudo passwd root
```

- 然后按提示两次输入密码即可

- 修改sshd配置：
```auto
sudo vim /etc/ssh/sshd_config
```

- 按i进入编辑模式，找到#PermitRootLogin prohibit-password，默认是注释掉的。直接在下面添加一行：
```auto
PermitRootLogin yes
```

- 然后按esc，输入:wq保存并退出。重启sshd服务：
```auto
sudo systemctl restart sshd
```

### 更换国内源地址

- 备份原有的源文件：
```auto
cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

- 查看是否修改备份成功：
```auto
ls /etc/apt
```

- 创建 sources.list 文件：
```auto
vim /etc/apt/sources.list
```

```auto
# 阿里源
deb http://mirrors.aliyun.com/ubuntu/ jammy main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ jammy-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ jammy-backports main restricted universe multiverse
```

```auto
# 网易163源       
deb http://mirrors.163.com/ubuntu/ jammy main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ jammy-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ jammy-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ jammy-proposed main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ jammy-backports main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ jammy main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ jammy-security main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ jammy-updates main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ jammy-proposed main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ jammy-backports main restricted universe multiverse
```

### 更新

```auto
sudo apt-get update
```
```auto
sudo apt-get upgrade
```

### 安装ifconfig

```auto
apt install net-tools
```

### 安装vim编辑器

```auto
apt-get install vim
```

### 安装casaOS

```auto
curl -fsSL https://get.casaos.io | sudo bash
```

## 把未分配的空间给系统盘

- 查看卷组的状态和配置信息，以及可用的空间和已分配的空间：
```auto
sudo vgdisplay ubuntu-vg
```

- 显示文件系统的磁盘空间使用情况：
```auto
sudo df -lh
```

- 可以使用以下的命令来将剩余的373G空间分配到你的逻辑卷/dev/mapper/ubuntu--vg-ubuntu--lv中：
```auto
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
```
```auto
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

### 这两个命令的含义是：

- lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv：这个命令会将所有未分配的空间（在你的情况下是373G）添加到你的逻辑卷/dev/mapper/ubuntu--vg-ubuntu--lv中。
- resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv：这个命令会调整文件系统的大小以适应新的逻辑卷大小。
- 执行完这两个命令后，你可以再次使用sudo df -lh命令来查看硬盘的情况，应该可以看到硬盘大小已经增加了。