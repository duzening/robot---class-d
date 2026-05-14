第二周进一步完善了开发环境与工具链的配置。首先，在 Ubuntu 环境中完成了 GitHub SSH 密钥的生成与配置，实现了通过命令行与远程仓库的安全交互，并掌握了基本的 Git 操作指令，如代码克隆（git clone）、添加文件（git add）、提交记录（git commit）以及推送到远程仓库（git push），能够完成基础的版本管理流程。

同时，完成了 VS Code 与 WSL Ubuntu 的连接配置，通过安装相关插件实现了在 Windows 环境下直接访问与编辑 Linux 子系统中的文件，提高了开发效率。在 ROS2 方面，成功运行 turtlesim 小乌龟节点，并通过命令行进行节点控制与交互。此外，还使用 Python 编写简单程序，实现了对小乌龟运动的控制

<img src="ros2小乌龟画圈.png" alt="小乌龟" width="500">

好的，我帮你把两段总结里的图片路径全部统一替换为 `ros2小乌龟画圈.png` 👇

---

# Week 3：Python编程与机器人控制入门

## 实验内容

本周完成了以下任务：

1. 学习Python基础（数据类型、函数、类、控制流等）
2. 掌握ROS2 Python库（rclpy）基本使用
3. 编写第一个ROS2 Python节点（Hello World）
4. 实现小乌龟直行与速度控制
5. 实现机器人走正方形轨迹
6. 了解PyBullet 3D仿真环境（拓展内容）

---

## 实验截图

### Hello World 节点运行

<img src="ros2小乌龟画圈.png" alt="Hello Node" width="600">

### 小乌龟直行控制

<img src="ros2小乌龟画圈.png" alt="直行控制" width="600">

### 小乌龟走正方形

<img src="ros2小乌龟画圈.png" alt="正方形轨迹" width="600">

---

## 运行命令

```bash
# 运行Python节点
python3 hello_node.py

# 启动小乌龟仿真
ros2 run turtlesim turtlesim_node

# 运行直行控制节点
python3 straight_mover.py

# 运行正方形控制节点
python3 square_mover.py
```

---

## 遇到的问题

1. **问题**：Python节点无法运行或无输出
   **解决**：检查是否执行 `rclpy.init()` 和 `rclpy.spin()`

2. **问题**：小乌龟不运动
   **解决**：确认是否持续发布 `/turtle1/cmd_vel` 话题

3. **问题**：运动轨迹不准确
   **解决**：调整速度与时间参数（距离/速度）

---

## 学习心得

本周重点学习了Python基础和ROS2 Python开发方法，掌握了节点的基本结构（初始化、发布、定时器等）。通过控制小乌龟完成直行和正方形运动，加深了对速度控制和时间计算的理解。同时初步接触了3D仿真工具PyBullet，对机器人仿真有了更直观的认识。

---

## 返回

[← 返回首页](../)

---

# Week 3（拓展）：机器人仿真与智能控制

## 实验内容

本周拓展完成了以下内容：

1. 学习 PyBullet 仿真环境基础
2. 运行3D物理仿真（地面 + 球体）
3. 实现简单机器人（小车）运动控制
4. 了解 RosClaw 与 OpenClaw 集成
5. 学习自然语言控制机器人流程
6. 了解2D与3D机器人运动差异

---

## 实验截图

### PyBullet 3D仿真界面

<img src="ros2小乌龟画圈.png" alt="PyBullet" width="600">

### 机器人小车运动

<img src="ros2小乌龟画圈.png" alt="机器人小车" width="600">

### 自然语言控制流程

<img src="ros2小乌龟画圈.png" alt="RosClaw流程" width="600">

---

## 运行命令

```bash
# 安装 PyBullet
pip install pybullet

# 运行基础示例
python3 pybullet_demo.py

# 运行强化学习环境示例
python3 -m pybullet_envs.examples.enjoy_TF_AntBulletEnv

# 启动 OpenClaw（Docker）
docker compose up -d

# 启动 ROS2 WebSocket
ros2 launch rosbridge_server rosbridge_websocket_launch.xml
```

---

## 遇到的问题

1. **问题**：PyBullet无法打开GUI窗口
   **解决**：检查是否在本地环境运行（WSL需配置图形支持）

2. **问题**：机器人不运动
   **解决**：确认是否正确调用 `setJointMotorControl2`

3. **问题**：自然语言控制无响应
   **解决**：检查 WebSocket 地址和API Key配置

---

## 学习心得

通过本部分学习，我从2D小乌龟仿真扩展到了3D机器人仿真，理解了物理引擎在机器人中的作用。同时接触了AI控制机器人（RosClaw + OpenClaw），对智能机器人系统有了更整体的认识。

---

## 返回

[← 返回首页](../)
