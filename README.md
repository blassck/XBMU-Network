西北民族大学校园网认证工具  
改编自https://github.com/HollowMan6/Srun-LZU-Network-Auth  
食用方法请参考前面链接  


# XBMU-Network

**XBMU-Network** 是一个专为西北民族大学（XBMU）校园网设计的自动化认证脚本/工具。它旨在解决校园网频繁掉线、手动登录繁琐的问题，支持在 Linux 路由器、服务器或个人电脑上自动完成身份认证。

---

## 🚀 功能特性

* **自动登录**：一键完成深澜（Srun）网关认证。
* **状态监测**：自动检测掉线并重新拨号。
* **跨平台支持**：支持 Python/Go（根据你的实现而定），可在 OpenWrt 路由器、Windows、macOS 及 Linux 上运行。
* **轻量化**：极低的资源占用，适合嵌入式设备。

---

## 🛠️ 安装与使用

### 1. 克隆仓库

```bash
git clone https://github.com/blassck/XBMU-Network.git
cd XBMU-Network

```

### 2. 配置参数

编辑配置文件 `config.yaml` 或在脚本中修改以下字段：

* **Username**: 学号
* **Password**: 校园网密码
* **Operator**: 运营商类型（如 `cmcc` 移动, `telecom` 电信, `unicom` 联通, 或 `local` 校园网）

### 3. 运行脚本

```bash
# 以 Python 为例
python main.py

```

---

## 📈 原理图解

该工具通过模拟浏览器向校园网网关发送 POST 请求，包含经过加密处理的凭据信息。其核心认证公式通常涉及 MD5 摘要算法，结构如下：

---

## 📅 计划任务 (Keep Alive)

为了保持长久在线，建议配合 `crontab` 使用：

```bash
# 每5分钟检查一次网络状态
*/5 * * * * /usr/bin/python3 /path/to/XBMU-Network/main.py >> /var/log/xbmu_net.log

```

---

## 🤝 贡献与致谢

* 感谢 [HollowMan6/Srun-LZU-Network-Auth](https://github.com/HollowMan6/Srun-LZU-Network-Auth) 提供的思路与参考。
* 欢迎通过 Pull Request 或 Issues 提交改进建议。

---

## 📄 开源协议

本项目基于 **MIT License** 开源。请仅在符合学校校园网使用条例的情况下使用。

---

### 💡 提示

如果你需要我针对你的代码逻辑（比如是用 Python 还是 Go 写的）调整具体的安装指令，或者需要写一份更详细的 **OpenWrt 部署指南**，请告诉我！
