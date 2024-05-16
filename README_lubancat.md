# MCC DAQ HAT库

MCC DAQ HAT库支持LubanCat1/2 rk系列板卡。

## 关于MCC DAQ HAT库

MCC DAQ HAT库详情请参考[README.md](README.md)。

## LubanCat上安装使用MCC DAQ HAT库

### 说明

- 测试使用板卡默认Debian10系统
- **目前只测试了连接一个MCC 134**

### 安装步骤

1. 连接MCC 134（设备地址不为0）和Lubancat 40pin，上电启动；

   MCC DAQ HAT硬件参考：[MCC 134](https://mccdaq.github.io/daqhats/overview.html#mcc-134)
   MCC 134设备地址连接参考：[Installing multiple boards](https://mccdaq.github.io/daqhats/hardware.html#installing-multiple-boards)

2. 启动系统后更新软件包信息，安装相关软件：

   ```bash
   sudo apt update
   sudo apt install git -y
   ```

3. 在用户目录下，拉取仓库源码：

   ```bash
   cd ~
   git clone https://github.com/mmontol/daqhats
   ```

4. 本地编译安装MCC DAQ HAT C库、工具和应用：

   ```bash
   cd ~/daqhats
   sudo ./install.sh
   sudo reboot
   ```

   重启后，更新EEPROM：
   ```bash
   sudo daqhats_read_eeproms
   ```

   查看库版本：
   ```bash
   daqhats_version
   ```

   如果要卸载MCC DAQ HAT库，执行命令：
   ```bash
   cd ~/daqhats
   sudo ./uninstall.sh
   ```

5. 本地编译安装daqhats Python库（可选）：

   更新和安装相关软件：
   ```sh
   python3 -m pip install --upgrade build
   sudo apt-get install python3-venv
   ```

   编译构建daqhats：
   ```sh
   cd ~/daqhats
   python3 -m build
   ```

   安装daqhats(以实际dist目录下whl文件名称修改下面命令)：
   ```sh
   sudo pip3 install dist/daqhats-1.5.0.0-py3-none-any.whl
   ```

   卸载daqhats Python库:

   ```sh
   sudo pip uninstall daqhats
   ```
