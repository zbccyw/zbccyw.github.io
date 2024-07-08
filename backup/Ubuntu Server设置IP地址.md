1. 使用以下命令列出所有网络接口，确定 Ubuntu 上可用的网络接口名称：
```auto
ip link show
```

2. 找到 Netplan 的配置文件：
```auto
cd /etc/netplan
ls -l
```

3. 打开并编辑 Netplan 配置文件，例如50-cloud-init.yaml：
```auto
sudo vi 50-cloud-init.yaml
```

4. 保存文件后，执行以下命令应用更改：
```auto
sudo netplan apply
```

5. 检查 IP 地址和网络连接：
```auto
ip addr show
ip route show
ping www.sysgeek.cn
```