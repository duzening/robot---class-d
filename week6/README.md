Week6

    第六周在复习基础操作的同时，引入机器人传感器相关知识，包括激光雷达、相机、IMU、GPS 等及其数据融合方法。结合 ROS2 实验，完成数据发布、编译与可视化（RViz、rqt）操作，理解传感器数据在机器人系统中的应用，并进行相关实验与作业提交。

<img src="传感器ros2 实验.png" alt="ros仿真传感器" width="500">

# Week 5：传感器与感知基础

## 实验内容

本周完成了以下任务：

1. 学习机器人常用传感器分类（外部传感器、内部传感器）
2. 掌握激光雷达（LiDAR）测距原理与数据结构
3. 了解相机与图像传感器基本概念
4. 学习ROS2中传感器数据话题（/scan、/image等）
5. 掌握 RViz 可视化工具基本使用
6. 实现传感器数据的可视化（激光雷达、图像、位姿）
7. 完成Turtlesim与仿真环境的数据展示实验

---

## 实验截图

### 传感器数据示意

<img src="传感器ros2 实验.png" alt="ros仿真传感器" width="500">


---

## 运行命令

```bash id="3a0k2m"
# 启动小乌龟
ros2 run turtlesim turtlesim_node

# 启动RViz
rviz2

# 查看激光雷达话题
ros2 topic list | grep scan

# 监听激光雷达数据
ros2 topic echo /scan

# 启动仿真环境（带雷达）
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py

# 相机数据
ros2 run image_transport republish raw
```

---

## 遇到的问题

1. **问题**：RViz无法显示数据
   **解决**：检查Fixed Frame是否正确（如 world / map）

2. **问题**：看不到激光雷达数据
   **解决**：确认 /scan 话题是否存在并正确订阅

3. **问题**：图像无法显示
   **解决**：检查话题名称和Image类型是否匹配

---

## 学习心得

本周学习了机器人感知系统的基础知识，了解了不同传感器的作用及应用场景。通过RViz工具实现数据可视化，使抽象的传感器数据变得直观易懂。同时掌握了ROS2中常见传感器话题的使用方法，为后续实现环境感知与自主导航打下基础。

---

## 返回
