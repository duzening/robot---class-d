# 第12周课程总结：手机摄像头、ArUco识别与距离测量

## 本周完成的任务

1. 配置 Tailscale 网络环境
2. 完成手机与 WSL Ubuntu 的网络连接
3. 使用手机浏览器调用 HTML5 摄像头
4. 在 WSL 中运行 OpenCV 视频接收程序
5. 完成 ArUco Marker 的识别与检测
6. 学习相机标定与基础距离测量原理

---

## 实验内容

### 手机摄像头接入 WSL

本周首先完成了手机与 WSL Ubuntu 之间的网络连接。通过安装并配置 Tailscale，将手机与电脑放入同一个虚拟网络中，从而解决了校园网与 WSL2 网络隔离的问题。随后，在 Ubuntu 环境中启动 Python 相机桥接程序，并通过手机浏览器访问 WSL 提供的网页服务，实现了手机摄像头画面的实时传输。

---

### OpenCV 接收视频流

在成功连接后，利用 Flask 与 SocketIO 构建简单的视频传输服务，通过 HTML5 摄像头获取手机实时画面，并持续向 WSL 发送 JPEG 图像帧。OpenCV 在 Ubuntu 中成功接收并显示手机视频流，完成了“手机摄像头 → 网络传输 → OpenCV 显示”的基础链路。

---

### ArUco 标记识别

本周重点学习了 ArUco Marker 的检测与识别。课堂统一使用：

* 字典：DICT_4X4_50
* Marker ID：6

通过 OpenCV 的 aruco 模块，对视频画面中的 Marker 进行检测，读取其 ID 与角点位置，并在图像中绘制检测结果。实验过程中理解了：

* Marker 字典必须一致
* 图像方向会影响识别
* JPEG 压缩与分辨率会影响检测精度

成功实现了 ArUco Marker 的实时识别。

---

## 运行命令

```bash
启动 Tailscale
sudo service tailscaled start

查看网络状态
tailscale status
tailscale ip -4

启动相机桥接程序
python3 camera_bridge.py
```

手机浏览器访问：

```bash
https://<WSL的Tailscale_IP>:5000
```

---

## 遇到的问题

问题 1：手机无法访问 WSL 页面
解决：检查 Tailscale 是否正常启动，并确认手机与 WSL 登录的是同一个账号。

问题 2：运行程序提示缺少 flask 模块
解决：使用 pip3 install -r requirements.txt 安装依赖。

问题 3：ArUco 无法识别
解决：检查 Marker 字典是否一致，并调整图像方向与摄像头分辨率。

---
完成截图
5.28.2.jpg
5.28.1.jpg

## 学习心得

通过本周学习，我了解了机器人视觉系统中的基本工作流程，并成功完成了手机摄像头与 WSL Ubuntu 的实时视频通信。课程中不仅学习了 OpenCV 与 ArUco 的基本使用方法，还理解了网络通信、视频流传输以及相机标定等内容。相比之前只运行简单程序，本周更加接近真实机器人系统开发流程，也让我对后续的目标定位、导航与视觉测距产生了更深入的理解。
