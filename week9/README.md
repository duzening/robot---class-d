# 机器人智能基础中的数学与算法

## 1. 线性代数——智能机器人的数学基石

### 为什么机器人需要线性代数？

机器人需要在三维物理世界中完成感知、决策与控制任务，而这些过程本质上都依赖数学描述。

* 位置（Position）
* 姿态（Pose）
* 速度（Velocity）
* 力（Force）

这些物理量都可以表示为向量或矩阵。

### 核心数学工具

* 向量（Vector）
* 矩阵（Matrix）
* 坐标变换（Coordinate Transformation）
* SO(3) 旋转群
* SE(3) 刚体运动群
* 四元数（Quaternion）

### 在线性代数中的应用

#### 感知（Perception）

相机、激光雷达将真实世界转换为：

* 图像矩阵（Image Matrix）
* 点云数据（Point Cloud）

涉及：

* 卷积（Convolution）
* 梯度（Gradient）
* 投影变换（Projection）

#### 决策（Planning）

机器人需要解决：

> 如何从 A 点移动到 B 点？

核心问题：

* 图搜索（Graph Search）
* 采样算法（Sampling）
* 优化算法（Optimization）

#### 控制（Control）

控制系统需要保证：

* 动作合法
* 满足动力学约束
* 可微分
* 可优化

---

# 2. 向量与坐标系

## 向量（Vector）

向量是同时具有：

* 大小（Magnitude）
* 方向（Direction）

的数学对象。

### 机器人中的向量

例如：

* 位置向量
* 速度向量
* 力向量
* 角速度向量

---

## 坐标系（Coordinate System）

坐标系是描述空间位置的参考框架。

常见坐标系：

### 世界坐标系（World Frame）

整个环境的统一参考系

### 机器人坐标系（Body Frame）

机器人自身参考系

### 相机坐标系（Camera Frame）

视觉系统参考系

### 关节坐标系（Joint Frame）

机械臂关节参考系

---

### 坐标变换的本质

同一个空间点：

在不同坐标系下，

数值表示不同。

因此：

> 坐标变换 = 更换参考系

---

## 常用向量运算

### 点积（Dot Product）

用途：

* 求夹角
* 求投影

公式：

[
a\cdot b = |a||b|\cos\theta
]

---

### 叉积（Cross Product）

用途：

* 求法向量
* 求旋转方向

公式：

[
a\times b
]

---

### 模长（Norm）

表示向量长度：

[
||a||=\sqrt{x^2+y^2+z^2}
]

---

### 线性组合

[
v=a_1v_1+a_2v_2+\cdots+a_nv_n
]

是矩阵运算和机器学习的基础。

---

# 3. 机器人运动学数学

## 正运动学（Forward Kinematics）

已知：

* 关节角度

求：

* 末端执行器位置

即：

[
(\theta_1,\theta_2)
\rightarrow
(x,y)
]

---

## 逆运动学（Inverse Kinematics）

已知：

* 末端位置

求：

* 各关节角度

即：

[
(x,y)
\rightarrow
(\theta_1,\theta_2)
]

---

### 逆运动学特点

#### 多解

例如：

* 肘部向上
* 肘部向下

两种姿态都能到达目标点。

（插入机械臂效果图）

---

#### 无解

目标超出机械臂工作空间。

（插入工作空间示意图）

---

#### 无穷多解

冗余机械臂：

[
DOF > Task\ Dimension
]

例如：

7自由度机械臂执行6维任务。

---

## 雅可比矩阵（Jacobian Matrix）

描述：

关节速度与末端速度之间的关系

[
\dot{x}=J(q)\dot{q}
]

作用：

* 运动控制
* 力控制
* 逆运动学求解

---

# 4. 计算机视觉中的数学

## 图像表示

数字图像本质上是矩阵。

例如：

[
Image=
\begin{bmatrix}
255 & 120 & 34\
210 & 85 & 40\
...
\end{bmatrix}
]

---

## 卷积（Convolution）

计算机视觉与深度学习的核心运算。

### 原理

卷积核在图像上滑动：

1. 对应元素相乘
2. 求和
3. 输出新像素值

即：

[
Output
======

Image * Kernel
]

---

### 卷积过程

（插入卷积动画或示意图）

卷积核：

[
\begin{bmatrix}
0 & -1 & 0\
-1 & 5 & -1\
0 & -1 & 0
\end{bmatrix}
]

不断移动：

得到特征图（Feature Map）。

---

### CNN中的作用

卷积层能够自动提取：

* 边缘
* 纹理
* 形状
* 高级语义特征

不同卷积核对应不同特征。

（插入CNN效果图）

---

# 5. 路径规划算法

## BFS（广度优先搜索）

所有图搜索算法的基础。

### 核心思想

像水波纹一样：

从起点向外逐层扩散。

（插入波纹扩散效果图）

---

### 数据结构

使用队列（Queue）

特点：

先进先出（FIFO）

过程：

1. 取出队头节点
2. 访问邻居节点
3. 加入队尾

---

### 优点

* 实现简单
* 保证最少步数路径

---

### 缺点

* 默认边权重相同
* 无法处理不同地形代价
* 大规模地图搜索效率低

---

## Dijkstra 算法

适用于：

* 非负权重图

特点：

* 计算真正的最短路径
* 考虑路径代价

---

## A* 算法

机器人导航最常用算法之一。

公式：

[
f(n)=g(n)+h(n)
]

其中：

* g(n)：已走代价
* h(n)：启发式估计

优点：

* 搜索速度快
* 路径质量高

---

## RRT（Rapidly-exploring Random Tree）

随机采样路径规划算法。

特点：

* 适用于高维空间
* 常用于机械臂规划

（插入RRT树状扩展图）

---

## DWA（Dynamic Window Approach）

移动机器人局部规划经典算法。

特点：

* 考虑机器人动力学约束
* 实时避障
* 广泛用于自动导航机器人

（插入DWA轨迹评估图）

---

# 总结

机器人智能的核心可以概括为：

**数学建模 → 感知 → 规划 → 控制**

其中：

* 线性代数负责描述世界
* 运动学负责描述机器人运动
* 计算机视觉负责环境感知
* 路径规划负责决策导航
* 控制理论负责执行动作

这些共同构成了现代机器人与人工智能系统的基础。


<img src="week9 picture1.png" alt="picture1" width="500">
<img src="week9 picture2.png" alt="picture2" width="500">
<img src="week9 picture3.png" alt="picture3" width="500">
<img src="week9 picture4.png" alt="picture4" width="500">
<img src="week9 picture5.png" alt="picture5" width="500">