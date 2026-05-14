image 镜像
只读的模板，包含了运行应用程序所需的所有文件、依赖项、配置、库和运行环境。可以将其理解为轻量级的、可执行的“安装包”，用于在 Docker 容器中运行代码，确保应用程序在不同环境中保持一致性。
核心特性：
只读模板： 镜像在运行后不会被改变。
分层结构： 基于联合文件系统（UnionFS），通过分层叠加生成最终的文件系统。
可移植性： “一次构建，随处运行”，可在任意安装了 Docker 的服务器上启动。 [1, 2, 3, 4, 5]
形象类比：
镜像 (Image) 就像是面向对象编程中的 类（Class） 或软件安装光盘（ISO 文件）。
容器 (Container) 则是类的 实例（Instance） 或运行中的安装程序。
container 容器
软件运行环境，一个基于沙盒隔离的可执行进程，运行在宿主机上，但不依赖独立操作系统。
与镜像关系： 容器是镜像的运行实例。镜像是只读的，容器是在镜像基础上增加了一个可读可写层。





<img src="屏幕截图 2026-05-07 104619.png" alt="opencv" width="500">


# Week 10：Docker 概念与 OpenCV 实验

## 实验内容
本周完成了以下任务：
1. 学习 Docker 核心概念（镜像、容器）
2. 掌握 Docker 基础命令（pull、run、ps 等）
3. 理解容器与本地文件挂载（-v 参数）
4. 安装 OpenCV 并进行基础图像处理实验
5. 使用 Python 读取、显示和处理图像

---

## 实验截图

### OpenCV 图像处理效果
<img src="屏幕截图 2026-05-07 104619.png" alt="OpenCV处理" width="600">

### Docker 容器运行示意
<img src="屏幕截图 2026-05-07 104619.png" alt="Docker容器" width="600">

---

## 运行命令
```bash
# 拉取镜像
docker pull <镜像名>

# 运行容器
docker run <镜像名>

# 查看容器
docker ps
docker ps -a

# 停止容器
docker stop <容器ID>

# 删除容器
docker rm <容器ID>

# 挂载本地目录运行 ROS2 容器
docker run -p 6080:80 --security-opt seccomp=unconfined --shm-size=512m \
  -v "$(pwd)/:/home/ws" \
  ghcr.io/tiryoh/ros2-desktop-vnc:humble

# 安装 OpenCV
pip install opencv-python opencv-contrib-python

# 解决 numpy 版本问题
pip install "numpy<2"
遇到的问题
问题：Docker 容器无法启动
解决：检查 Docker Desktop 是否运行，确认端口 6080 未被占用
问题：OpenCV 导入失败
解决：重新安装 OpenCV 或检查 pip 环境
问题：图像颜色显示异常
解决：使用 cv2.cvtColor(img, cv2.COLOR_BGR2RGB) 转换颜色空间
学习心得

通过本周学习，我理解了 Docker 镜像与容器的关系，以及容器化技术“环境隔离”的优势。同时掌握了基本 Docker 操作和目录挂载方法。
在 OpenCV 实验中，我学会了图像读取、颜色空间转换和简单处理流程，为后续视觉感知学习打下基础。

返回

← 返回首页
