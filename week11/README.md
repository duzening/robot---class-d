week11/屏幕截图 2026-05-14 100033.png
<img src="屏幕截图 2026-05-14 100033.png" alt="opencv" width="500">
````markdown
# Week 11：Docker 进阶与 GitHub Pages 网页部署

## 实验内容
本周完成了以下任务：
1. 掌握 Docker 进阶操作（查看、停止容器）
2. 学习 Docker 镜像保存与更新（commit）
3. 在容器中安装 pybullet 与 OpenCV 并生成新镜像
4. 将 GitHub 作业仓库部署为网页（GitHub Pages）
5. 优化 README 结构与网页展示效果

---

## 实验截图

### GitHub Pages 网页访问效果
<img src="屏幕截图 2026-05-14 100033.png" alt="GitHub Pages" width="600">

### Docker 容器运行与保存镜像
<img src="屏幕截图 2026-05-14 100033.png" alt="Docker进阶" width="600">

---

## 运行命令
```bash
# 查看运行中的容器
docker ps

# 查看所有容器
docker ps -a

# 停止容器
docker stop <容器ID>

# 保存容器为新镜像
docker commit -m "install pybullet and opencv" -a "your-name" <容器ID> my-ros2-full:v1.0

# 查看镜像
docker images

# 运行并挂载目录
docker run -p 6080:80 --security-opt seccomp=unconfined --shm-size=512m \
  -v "$(pwd)/:/home/ws" \
  ghcr.io/tiryoh/ros2-desktop-vnc:humble

# 提交 GitHub Pages
git add .
git commit -m "配置 GitHub Pages"
git push
````

---

## 遇到的问题

1. **问题**：Docker 容器修改后环境丢失
   **解决**：使用 `docker commit` 保存为新镜像

2. **问题**：GitHub Pages 访问 404
   **解决**：确认仓库为 Public，并正确设置 Pages 分支

3. **问题**：图片无法显示
   **解决**：使用相对路径（如 img/xxx.png），并确保已提交

---

## 学习心得

通过本周学习，我掌握了 Docker 容器的管理与镜像保存方法，能够构建属于自己的开发环境。同时学会了使用 GitHub Pages 将作业仓库部署为网页，实现内容的可视化展示。这不仅提升了项目整理能力，也为后续作品展示打下基础。

---

## 返回

[← 返回首页](../)

```
```
