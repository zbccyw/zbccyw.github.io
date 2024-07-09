HEU KMS Activator，简洁高效的KMS/OEM智能激活工具，适用所有Windows, Office版本，无需联网即可一键激活，支持UEFI的KMS激活工具。KMS服务是微软对Windows, Office等产品的批量许可服务，利用KMS可以激活局域网内的产品。该工具利用KMS机制在系统搭建KMS服务器，从而实现在线或离线激活。

![HEU_KMS_Activator](https://github.com/zbccyw/zbccyw.github.io/assets/175001413/f4a015a3-70ad-43f7-a3b5-938243690e4c)

### 功能介绍：

1. 智能激活：智能识别最佳的激活方式
- 优先顺序依次为数字许可证/KMS38/OEM/KMS
- 自动识别并跳过已经永久激活的Windows/Office
2. KMS激活
- 安装/卸载自动续期功能，两种模式可供选择[1]自动续订模式(默认 [2]任务计划模式
- 清除KMS客户端信息：清除KMS服务器地址、端口、激活时间间隔、续订时间间隔等
- 搭建KMS服务器[手动激活]：KMS服务器地址/端口
3. 数字激活（数字许可证激活、KMS38激活）
- 添加/解除KMS38保护，免受180天激活影响，除非解除保护，否则不能使用KMS38激活
- 查看当前系统信息：网络状态/激活状态，描述便于快速查看是否支持数字许可证/KMS38
4. OEM激活（提供6种模式）
- 卸载OEM激活信息：清除动态加载的SLIC等信息，OEM激活将失效
- 生产$OEM$文件夹：可将该文件夹置于ISO镜像source文件夹下，以集成OEM激活功能
- 更改Windows 10版本、激活信息备份还原、Microsoft Office 零售版转换批量授权版
- Windows/Office密钥管理功能：安装密钥、卸载密钥、查看密钥、清除Office许可证
- 智能激活、激活成功率高、支持静默参数、几乎支持所有 Windows/Office 所有版本
- Windows 7上无需依赖.NET Framework、能够离线激活，也能连接网络服务器激活

```atuo
静默参数
/? 查看静默参数
/kwi 激活Windows
/kof 激活Office
/ren 安装自动续期功能
/unr 卸载自动续期功能
/dig 数字许可证激活Win10
/k38 激活Win10有效期至2038年
/oem OEM激活Win Vista/7/Server
/lok 为KMS38激活添加保护
/reb 重启计算机
/nologo 使用静默参数时不显示logo
```

静默使用数字许可永久激活Windows示例：
HEU_KMS_Activator.exe /kwi /dig /nologo
注意：此激活工具微软Defender会误报威胁，记得提前加排除！

### 更新日志：

[2024.05.06] v42.0.3 更新说明：
1.修复Ohook导致原有MAK永久激活失败的bug。
2.更换logo。

```auto
文件：HEU_KMS_Activator_v42.0.3.exe
SHA1：B3D7A5944CFF70F67D987371630D3A62DE29C32F
```

### 下载地址：
蓝奏云盘：https://www.lanzoui.com/iY9np1xy0j2f

### 转发自[宋永志的博客](http://www.songyongzhi.com/)