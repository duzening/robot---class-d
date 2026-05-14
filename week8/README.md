docker win
docker mac
docker 运行ros2
显示隐藏文件，找到ProgramData目录
删除DockerDesktop文件夹
浏览器打开 http://127.0.0.1:6080/
运行小乌龟的ros2节点（注意在docker镜像中ros2 已经安装好了）

<img src="image.png" alt="docker ros2" width="500">


# Week 8：Docker 与 ROS2 桌面环境

## 实验内容
本周完成了以下任务：
1. 安装 Docker（Windows / Mac）
2. 使用 Docker 运行 ROS2 桌面环境
3. 通过浏览器访问 ROS2 图形界面
4. 在容器中运行 turtlesim 小乌龟节点

---

## 实验截图

### ROS2 桌面环境（浏览器访问）
<img src="image.png" alt="ROS2桌面" width="600">

### 小乌龟仿真运行
<img src="image.png" alt="小乌龟" width="600">

---

## 运行命令
```bash
# 运行 ROS2 桌面容器（参考项目）
docker run ...

# 浏览器访问
http://127.0.0.1:6080/

# 启动小乌龟
ros2 run turtlesim turtlesim_node

# 键盘控制
ros2 run turtlesim turtle_teleop_key
遇到的问题
问题：Docker Desktop 无法启动
解决：确认 WSL2 已安装并正常运行
问题：首次运行镜像下载过慢
解决：更换网络或使用镜像加速
问题：浏览器无法访问界面
解决：确认容器运行成功，并访问 127.0.0.1:6080
学习心得

通过本周学习，我掌握了 Docker 的基本使用，并成功在容器中运行 ROS2 桌面环境。理解了 Docker 可以统一运行环境，减少系统差异，方便 ROS2 项目的部署与复现。

返回

← 返回首页
