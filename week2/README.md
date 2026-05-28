# Week 2：WSL、Ubuntu 与 ROS2 环境配置

## 实验内容

本周完成了以下任务：

1. 安装 WSL Ubuntu 22.04
2. 配置 ROS2 Humble 环境
3. 运行 turtlesim 小乌龟节点

## 实验截图

### Ubuntu 安装成功

<img src="ros2 小乌龟.jpg" alt="Ubuntu 安装" width="600">

### 小乌龟仿真运行

<img src="ros2 小乌龟.jpg" alt="小乌龟" width="600">

## 运行命令

\`\`\`bash
# 启动小乌龟节点
ros2 run turtlesim turtlesim_node

# 启动键盘控制
ros2 run turtlesim turtle_teleop_key
\`\`\`

## 遇到的问题

1. **问题**：运行 `ros2` 命令提示 command not found
   **解决**：运行 `source /opt/ros/humble/setup.bash`

## 学习心得

通过本周学习，我掌握了 WSL 的基本使用和 ROS2 的安装配置...

## 返回

[← 返回首页](../)


1.win 商店下载ubuntu系统
2.排除wsl配置错误
3.设置账户名密码进入系统
安装ros2,运行脚本,跑验证的小乌龟ros程序
第二周主要完成了基于 Windows 环境的 ROS2 开发平台搭建工作。首先，通过 Windows 商店成功下载安装了 Ubuntu 子系统，并对 WSL 运行过程中出现的配置问题进行了排查与修复，确保系统能够稳定运行。随后，在 Ubuntu 环境中完成了用户账户与密码的初始化设置，顺利进入 Linux 系统。在此基础上，按照官方流程安装了 ROS2（Humble 版本），并通过运行相关安装与配置脚本完成环境搭建。最后，通过运行经典的 turtlesim 小乌龟示例程序，对 ROS2 的安装结果进行了验证，实现了节点启动与键盘控制小乌龟运动，表明整体环境配置成功

<img src="ros2 小乌龟.jpg" alt="小乌龟" width="500">
