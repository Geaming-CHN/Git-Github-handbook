# Git-Github-handbook
# Git&Github使用手册
在学习Git&Github中的学习笔记
1. 版本控制
2. Git简介
3. Git命令行操作
4. Github服务器环境搭建
5. Git图形化界面操作

[TOC]

## 版本控制

### 版本控制介绍

#### 版本控制工具应该具备的功能

- 协同修改：多人并行不悖的修改服务器端的同一个文件。
- 数据备份：不仅保存目录和文件的当前状态，还能够保存每一个提交过的历史状态。
- 版本管理：在保存每一个版本的文件信息的时候要做到不保存重复数据，以节约存储空间。提高运行效率。==这方面SVN采用的是增量式管理的方式，而Git采取了文件系统快照的方式。==
- 权限管理：
  - 对团队中参与开发的人员进行权限控制。
  - 对团队外开发者贡献的代码进行审核——Git独有
- 历史记录：
  - 查看修改人、修改时间、修改内容、日志信息
  - 将本地文件恢复到某一个历史状态
- 分支管理：
  - 允许开发团队在工作过程中多条生产线同时推进 任务，进一步提高效率

#### 版本控制简介

工程设计领域中使用版本控制管理工程蓝图的设计过程。在IT开发过程中也可以使用版本控制思想管理代码的版本迭代。

1. 集中式版本控制工具（单点故障SPOF）：CVS、==SVN==、VSS……
2. 分布式版本控制工具：==Git==……

## Git简史
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Git-logo.svg/1024px-Git-logo.svg.png" alt="Git-logo-2012.svg" style="zoom: 25%;" />

https://en.wikipedia.org/wiki/Git

### Git的优势

1. 大部分操作在本地完成，不需要联网
2. 完整性保证
3. 尽可能添加数据而不是删除或修改数据
4. 分支操作非常快捷流畅
5. 与Linux命令全面兼容

### Git结构

![image-20210717164835252](https://cdn.jsdelivr.net/gh/GEAMING-CHN/images/blogimg/%E6%9D%82%E9%A1%B9/image-20210717164835252.png)

### Git和代码托管中心

代码托管中心任务：维护远程库

- 局域网环境下：GitLab服务器
- 外网环境下：Github、码云

### 本地库和远程库

- 团队内部协作
- 跨团队协作

![1](https://cdn.jsdelivr.net/gh/GEAMING-CHN/images/blogimg/%E6%9D%82%E9%A1%B9/1.png)

## Git命令行操作

### 本地库操作

#### 本地库初始化

![image-20210717175859096](https://cdn.jsdelivr.net/gh/GEAMING-CHN/images/blogimg/%E6%9D%82%E9%A1%B9/image-20210717175859096.png)

==注意==：==.git目录==中存放的是本地库相关的子目录和文件，不要删除，也不要胡乱修改

#### 设置签名:

形式：（区分不同开发人员身份）

- 用户名：Geaming-CHN

- Email地址：XXXXX@163.com

- 辨析：设置的签名和登录远程库（代码托管中心）的账号、密码无任何关系

- 命令：

  - 项目级别/仓库级别：仅在当前本地库范围内有效

    ```
    git config user.name Geaming-CHN_pro
    git config user.email XXXXXXXXX
    ```

    信息保存位置：`./.git/config`

    ![image-20210717181120679](https://cdn.jsdelivr.net/gh/GEAMING-CHN/images/blogimg/%E6%9D%82%E9%A1%B9/image-20210717181120679.png)

  - 系统用户级别：登录当前操作系统的用户范围

    ```
    git config --global user.name Geaming-CHN_glb
    git config --global user.email XXXXXXXXX
    ```

    信息保存位置：`~/.gitconfig`

    ![image-20210717181722273](https://cdn.jsdelivr.net/gh/GEAMING-CHN/images/blogimg/%E6%9D%82%E9%A1%B9/image-20210717181722273.png)

  - 优先级：就近原则（项目级别优先于用户级别）

  - 二者都没有->不允许

#### 命令操作

`git status`

![image-20210717182038459](https://cdn.jsdelivr.net/gh/GEAMING-CHN/images/blogimg/%E6%9D%82%E9%A1%B9/image-20210717182038459.png)

创建测试：`vim good.txt`

![image-20210717182816435](https://cdn.jsdelivr.net/gh/GEAMING-CHN/images/blogimg/%E6%9D%82%E9%A1%B9/image-20210717182816435.png)

### 远程库操作

