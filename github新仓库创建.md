### 一、在 GitHub 上创建新仓库

1. 登录 GitHub 账号，点击右上角「+」→「New repository」。
2. 填写仓库信息：
   - **Repository name**：仓库名称（如`my-project`）。
   - **Description**（可选）：仓库描述（如「我的第一个项目」）。
   - **Public/Private**：选择仓库公开 / 私有。
   - 勾选「Add a README file」（可选，初始化仓库说明文档）。
3. 点击「Create repository」完成创建。

### 二、将本地项目推送到 GitHub 仓库

#### 情况 1：本地已有项目（未关联 Git）

1. **本地初始化 Git 仓库**

   打开终端，进入本地项目文件夹：

   ```bash
   cd /本地项目路径（如D:/my-project）
   git init  # 初始化Git仓库
   ```

   

2. **关联 GitHub 远程仓库**

   复制 GitHub 仓库的 HTTPS/SSH 地址（仓库页面→Code→复制地址），执行：

   ```bash
   git remote add origin https://github.com/你的用户名/仓库名.git
   ```

   

3. **提交本地文件到 Git**

   ```bash
   git add .  # 添加所有文件到暂存区
   git commit -m "初始化项目"  # 提交到本地仓库（-m后为提交说明）
   ```

   

4. **推送到 GitHub 远程仓库**

   - 若 GitHub 仓库默认分支是main

     ```bash
     git branch -M main  # 将本地分支重命名为main（匹配GitHub默认分支）
     git push -u origin main  # 推送并关联远程分支
     ```

   - 若本地分支是master

     ```bash
     git push -u origin master  # 推送master分支
     ```

#### 情况 2：本地项目已关联其他 Git 仓库

先移除旧的远程关联（可选），再关联新的 GitHub 仓库：

```bash
git remote remove origin  # 移除旧远程仓库
git remote add origin https://github.com/你的用户名/仓库名.git  # 关联GitHub仓库
git push -u origin main  # 推送
```

### 三、从 GitHub 克隆仓库到本地

1. **获取 GitHub 仓库地址**

   进入 GitHub 仓库页面→点击「Code」→复制 HTTPS/SSH 地址（如`https://github.com/你的用户名/仓库名.git`）。

2. **克隆到本地指定位置**

   打开终端，执行克隆命令：

   ```bash
   # 克隆到默认文件夹（仓库名）
   git clone https://github.com/你的用户名/仓库名.git
   
   # 克隆到指定文件夹（自定义路径）
   git clone https://github.com/你的用户名/仓库名.git /目标路径（如D:/code/my-project）
   ```

   

3. **进入克隆后的仓库**

   ```bash
   cd 仓库名（或自定义文件夹名）
   ```

### 四、补充说明

- SSH vs HTTPS

  - HTTPS：需输入 GitHub 账号密码（或令牌），适合新手。
  - SSH：需配置 SSH 密钥，无需每次输入密码，更便捷（配置方法参考之前的 SSH 密钥生成步骤）。

- 分支问题

  GitHub 默认分支main，若本地分支是master，推送时需对应分支名（如git push origin master）。

- 常用后续操作

  克隆 / 推送后，本地修改文件可通过

  git add→git commit→git push

  同步到 GitHub；GitHub 更新后，本地可通过git pull拉取最新内容。