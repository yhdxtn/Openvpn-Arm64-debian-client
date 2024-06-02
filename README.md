## 安装步骤

1. **下载所需的 `.deb` 文件：**
   ```bash
   wget https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/iproute2_5.10.0-4_arm64.deb
   wget https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/libbpf0_0.3-2_arm64.deb
   wget https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/libpkcs11-helper1_1.25.1-1_arm64.deb
   wget https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/openvpn_2.4.7-1+deb10u1_arm64.deb
   ```
或者
   bash'''
   curl -O -L https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/iproute2_5.10.0-4_arm64.deb
   curl -O -L https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/libbpf0_0.3-2_arm64.deb
   curl -O -L https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/libpkcs11-helper1_1.25.1-1_arm64.deb
   curl -O -L https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/openvpn_2.4.7-1+deb10u1_arm64.deb
   '''
2. **安装 `.deb` 文件：**
   ```bash

sudo dpkg -i libbpf0_0.3-2_arm64.deb
sudo dpkg -i libpkcs11-helper1_1.25.1-1_arm64.deb
sudo dpkg -i iproute2_5.10.0-4_arm64.deb
sudo dpkg -i openvpn_2.4.7-1+deb10u1_arm64.deb

   ```

3. **将 OpenVPN 服务器配置文件放置到 `/etc/openvpn/` 目录中。**

4. **启动 OpenVPN 客户端：**
   ```bash
   sudo openvpn --config /etc/openvpn/<your_config_file>.ovpn
   ```

### 如何设置 OpenVPN 别名以简化启动流程

在命令行中，你可以使用别名（alias）来简化常用命令的输入。这对于启动 OpenVPN 等长命令特别有用。下面是设置 OpenVPN 别名的步骤：

#### 步骤 1：编辑 `.bashrc` 文件

1. 打开终端，并输入以下命令以编辑 `~/.bashrc` 文件：
   ```bash
   nano ~/.bashrc
   ```

2. 在文件末尾添加以下行，用于设置 OpenVPN 别名：
   ```bash
   alias myvpn='/usr/sbin/openvpn --config /etc/openvpn/<your_config_file>.ovpn'
   ```

3. 保存并关闭文件。

#### 步骤 2：重新加载 `.bashrc` 文件

输入以下命令以使修改生效：
```bash
source ~/.bashrc
```

#### 步骤 3：使用别名启动 OpenVPN

现在你可以使用你设置的别名来启动 OpenVPN 了。在终端中输入以下命令即可：
```bash
myvpn
```

这会启动 OpenVPN 并使用指定的配置文件 `/etc/openvpn/<your_config_file>.ovpn`。
#后台运行
要在后台静默运行 OpenVPN，你可以使用 `nohup` 命令，它允许你在后台运行一个命令，并且即使退出终端，该命令也会继续运行。




```bash
nohup openvpn /etc/openvpn/xg2.ovpn > /dev/null &
```

这个命令使用了 `nohup` 来确保即使终端关闭，也能继续运行 OpenVPN，同时将输出重定向到 `/dev/null` 中，这样连接日志就不会打印到终端上。
#关闭openvpn
要关闭在后台运行的 OpenVPN，可以使用 `kill` 命令来发送信号给 OpenVPN 进程，让它终止。你可以按照以下步骤操作：

1. 首先，使用 `ps` 命令查找正在运行的 OpenVPN 进程的 PID（进程 ID）。在终端中输入以下命令：

```bash
ps aux | grep openvpn
```

这会列出所有包含 "openvpn" 字符串的进程，并显示它们的 PID。

2. 找到属于 OpenVPN 的进程，记下它的 PID。

3. 然后，使用 `kill` 命令发送信号给该进程，终止它。假设 PID 是 923，那么命令将是：

```bash
sudo kill 923
```

这会向 PID 为 923 的进程发送终止信号，关闭 OpenVPN。
