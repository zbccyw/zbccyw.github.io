### 查看卷组的状态和配置信息，以及可用的空间和已分配的空间

```auto
sudo vgdisplay ubuntu-vg
```

![1](https://github.com/zbccyw/zbccyw.github.io/assets/175001413/b3907084-2bb8-42b7-8414-3f137fef792f)

### 显示文件系统的磁盘空间使用情况

```auto
sudo df -lh
```

![2](https://github.com/zbccyw/zbccyw.github.io/assets/175001413/c227d1cc-9466-4a94-aeba-38c668109829)

**从你提供的文件系统信息来看，/dev/mapper/ubuntu--vg-ubuntu--lv（即你的逻辑卷）的大小现在是98G，已使用13G，可用空间为81G。**

### 可以使用以下的命令来将剩余的373G空间分配到你的逻辑卷/dev/mapper/ubuntu--vg-ubuntu--lv中：

```auto
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv
```

![3](https://github.com/zbccyw/zbccyw.github.io/assets/175001413/89d66203-fcf5-4d50-807e-7f4c2ad60514)

### 这两个命令的含义是：

- lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv：这个命令会将所有未分配的空间（在你的情况下是373G）添加到你的逻辑卷/dev/mapper/ubuntu--vg-ubuntu--lv中。

- resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv：这个命令会调整文件系统的大小以适应新的逻辑卷大小。

### 执行完这两个命令后，你可以再次使用`sudo df -lh`命令来查看硬盘的情况，应该可以看到硬盘大小已经增加了。