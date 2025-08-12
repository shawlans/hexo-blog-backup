---
title: 如何使用Hexo创建博客
date: 2025-08-11
author: Shawlans
categories:
  - 博客
tags:
  - 技术
  - 教程
  - Hexo
  - GitHub 
draft: false
---

欢迎来到我的博客！这是一个非常详细的、从零开始在windows系统使用 Hexo + GitHub Pages 搭建个人博客的保姆级教程。
即使你是新手，按照这个步骤也能成功搭建。

整个过程分为以下几个主要步骤：
1.	准备工作：安装必要的软件环境 (Node.js, Git)。
2.	安装 Hexo：安装 Hexo 博客框架。
3.	本地运行：在你的电脑上创建并预览博客。
4.	创建 GitHub 仓库：为你的博客网站和源码创建托管空间。
5.	配置部署：将 Hexo 与 GitHub 仓库关联起来。
6.	发布博客：将你的博客部署到互联网上。
7.	日常使用：如何写新文章和更换主题。

## 第一步：准备工作 (环境安装)

在开始之前，你的电脑需要安装 Node.js 和 Git。

### 1. 安装 Git

Git 是一个版本控制系统，Hexo 部署博客时需要用到它。
	官方网站：https://git-scm.com/downloads
	根据你的操作系统（Windows/Mac/Linux）下载并安装。安装过程基本上一路“下一步”即可。
	验证安装：打开你的终端（Windows 用户可以使用 Git Bash、CMD 或 PowerShell），输入以下命令：

      git --version

如果显示出版本号（如 git version 2.38.1.windows.1），说明安装成功。

### 2. 安装 Node.js

Hexo 是基于 Node.js 的，所以必须安装它。
	官方网站：https://nodejs.org/
	建议下载 LTS (长期支持版)，它更稳定。
	安装过程同样是一路“下一步”。Node.js 安装包会自带 npm (Node.js 包管理器)。
	验证安装：在终端中输入以下命令：

      node -v
      npm -v
    
如果分别显示出 Node.js 和 npm 的版本号，说明安装成功。

## 第二步：安装 Hexo

环境准备好后，就可以通过 npm 全局安装 Hexo 的命令行工具了。
在终端中输入以下命令：

      npm install -g hexo-cli
    
	#npm install 是安装命令。
	-g 表示全局安装，这样你就可以在任何目录下使用 hexo 命令。

## 第三步：本地创建并运行博客

现在，你可以在本地电脑上创建一个博客项目了。

### 1.	初始化博客

选择一个你喜欢的位置（比如 D:\Blog），在该目录下打开终端，执行以下命令：
  
      hexo init my-blog
      # "my-blog" 是你的博客文件夹名，可以自定义
    
### 2	      进入博客目录

      cd my-blog
    
### 3.	安装依赖

进入文件夹后，你会看到很多文件。现在需要安装项目所需的依赖包。

      npm install
    
### 4.	本地预览

激动人心的时刻！启动 Hexo 的本地服务，看看你的博客长什么样。

      hexo server
      或者简写
      hexo s
    
终端会显示：
INFO Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
现在，打开浏览器，访问 http://localhost:4000，你就能看到 Hexo 的默认博客页面了！
提示：在终端按 Ctrl+C 可以停止本地服务。

## 第四步：创建 GitHub 仓库

要将博客发布到网上，你需要一个地方来托管它。GitHub Pages 是最完美的免费选择。

### 1.	注册 GitHub 账号

如果你还没有，先去 https://github.com/ 注册一个账号。

### 2.	创建博客网站仓库

这是用来存放你 最终生成的静态网站文件 (HTML/CSS/JS) 的地方。
o	点击 GitHub 页面右上角的 + 号，选择 New repository。
o	仓库名称 (Repository name) 必须是特定的格式：你的用户名.github.io。
	例如，如果你的 GitHub 用户名是XXX，那么仓库名必须是XXX.github.io。这一点至关重要！
o	选择 Public (公开)。
o	点击 Create repository。

## 第五步：配置部署

现在，需要让你的本地 Hexo 项目知道应该把网站文件推送到哪里。
### 1.	安装 Git 部署插件

Hexo 需要一个插件来帮助它通过 Git 进行部署。在你的博客根目录 (my-blog) 下的终端中执行：

      npm install hexo-deployer-git --save
    
### 2.	配置 _config.yml 文件

这是 Hexo 的核心配置文件，位于你的博客根目录 (my-blog) 下。用代码编辑器（如 VS Code）打开它。
找到文件末尾的 deploy 部分，修改成如下格式：

      # Deployment
    ## Docs: https://hexo.io/docs/one-command-deployment
      deploy:
      type: git
      repo: https://github.com/你的用户名/你的用户名.github.io.git
      branch: main # 或者 master，取决于你的GitHub仓库默认分支名
    
	
      # type: 必须是 git。
	# repo: 换成你上一步创建的 你的用户名.github.io 仓库的 URL。你可以在仓库主页的 Code 按钮下找到这个 URL (推荐使用 HTTPS 格式)。
	# branch: GitHub 现在默认新建的分支是 main，如果你的仓库是 master，请修改为 master。
注意：YAML 格式对缩进非常敏感，type:, repo:, branch: 前面必须有两个空格。

## 第六步：发布你的博客

万事俱备，只欠东风。现在可以将你的博客部署到 GitHub Pages 了。
在你的博客根目录 (my-blog) 下的终端中，依次执行以下命令：

### 1.	清除缓存 (可选，但推荐,不清楚缓存可能会导致网页内容不更新)

      hexo clean
    
### 2.	生成静态文件

这个命令会把你的 Markdown 文章转换成网站所需的 HTML、CSS 等文件，存放在 public 文件夹中。

      hexo generate
    # 或者简写
      hexo g
    
### 3.	部署到 GitHub

这个命令会将 public 文件夹里的所有内容推送到你配置好的 GitHub 仓库中。

      hexo deploy
    # 或者简写
      hexo d
    
执行 hexo deploy 时，它会要求你输入 GitHub 的用户名和密码（或 Personal Access Token），按提示操作即可。
现在，见证奇迹！
等待一两分钟，然后访问你的 GitHub Pages 网址：https://你的用户名.github.io。
恭喜！你的个人博客已经成功上线了！

## 第七步：日常使用

### 1. 如何写新文章？

非常简单，使用 hexo new 命令。

      hexo new "我的第一篇文章"
    
Hexo 会在 source/_posts 文件夹下创建一个名为 我的第一篇文章.md 的 Markdown 文件。你只需要用任何支持 Markdown 的编辑器（如 VS Code, Typora）打开它，开始写作即可。
写完后，按照 第六步 的流程重新部署一遍：

      hexo clean && hexo g -d

      # 简写组合命令
    
这个命令会先清除、再生成、最后部署。稍等片刻，你的新文章就出现在网站上了。

### 2. 如何更换主题？

Hexo 有海量漂亮的主题。以广受欢迎的 Next 主题为例：

#### 1.	下载主题

在你的博客根目录 (my-blog) 下，执行 Git 命令下载主题到 themes 文件夹：

      git clone https://github.com/next-theme/hexo-theme-next themes/next
    
#### 2.	修改配置

打开根目录的 _config.yml 文件，找到 theme 字段，修改为：

      # Extensions
      ## Plugins: https://hexo.io/plugins/
      ## Themes: https://hexo.io/themes/
      theme: next
    
#### 3.	重新生成和部署

      hexo clean && hexo g -d
    
刷新你的网站，就能看到全新的主题了！每个主题都有自己详细的配置文档，你可以根据文档进行个性化设置。

## 总结

至此，你已经掌握了使用 Hexo 和 GitHub Pages 搭建和维护个人博客的全套流程。
•	本地写作：hexo new "文章名"
•	本地预览：hexo s
•	发布上线：hexo g -d
•     清楚缓存，生成静态文件并部署：hexo clean && hexo generate && hexo deploy（或者使用简写 hexo clean && hexo g -d）
祝你写作愉快！







