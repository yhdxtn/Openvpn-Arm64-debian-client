## 安装步骤


1. 下载所需的 `.deb` 文件：
   ```
   wget https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/iproute2_5.10.0-4_arm64.deb
   wget https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/libbpf0_0.3-2_arm64.deb
   wget https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/libpkcs11-helper1_1.25.1-1_arm64.deb
   wget https://github.com/yhdxtn/Openvpn-Arm64-debian-client/raw/main/openvpn_2.4.7-1+deb10u1_arm64.deb
   ```

2. 安装 `.deb` 文件：
   ```
   sudo dpkg -i iproute2_5.10.0-4_arm64.deb
   sudo dpkg -i libbpf0_0.3-2_arm64.deb
   sudo dpkg -i libpkcs11-helper1_1.25.1-1_arm64.deb
   sudo dpkg -i openvpn_2.4.7-1+deb10u1_arm64.deb
   ```

3. 将 OpenVPN 服务器配置文件放置到 `/etc/openvpn/` 目录中。

4. 启动 OpenVPN 客户端：
   ```
   sudo openvpn --config /etc/openvpn/<your_config_file>.ovpn
   ```

---
