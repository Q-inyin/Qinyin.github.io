---
title: hexo的安装及博客的部署
date: 2022-08-24 08:22:00
categories: ['Githube','hexo']
tags: ['分享']
cover: https://w.wallhaven.cc/full/28/wallhaven-2879mg.png
---

# hexo的安装及博客的部署

## 安装Node

```
Node官网 https://nodejs.org/en/
```

**下载Windows带有版本号的LTS版**

- 配置安装路径一直到底安装即可

- 检查是否安装成功，返回版本号成功

  ~~~
  ##cmd输入
  
  node -v 
  
  npm -v
  ~~~

  

## 安装hexo

**按win+r弹出的框输入cmd回车弹出命令提示符,输入以下指令回车。**

```bash
npm install -g cnpm --registry=https://registry.npm.taobao.org

cnpm install hexo-cli -g
```

**CMD命令  盘符号:进入想要存放博客文件的盘符，我这里是D盘以D盘为例D: ,cd:文件名**

```
hexo init
```

**等待完成。完成提示**

```
INFO  Start blogging with Hexo!
```

**这样博客就搭好了，文件储存在你创建的文件下**

## 安装Git

#### <font color=red face="黑体">这里转载了CSDN博主的文章</font>

#### [Git 详细安装教程（详解 Git 安装过程的每一个步骤）_mukes的博客-CSDN博客_git安装](https://blog.csdn.net/mukes/article/details/115693833)

***`本文发布于 2021-4-17，发布后访问量噌噌地涨，评论区一片好评，都是一群爱学习的好同学啊（重点表扬发现彩蛋的同学），现距发布时间快一年了，更新一下新版本，毕竟没有人喜欢过时的东西`***

**查看配置**

```
### 查看自己设置的配置

git config --list 
```

**查看用户信息**

```
查看用户名 ：git config user.name

查看密码： git config user.password

查看邮箱：git config user.email
```

**查看设置信息（全局配置**

```
git config --global user.name "xxxx名称"
git config --global user.email "xxxx.com邮箱"
git config --global user.password "xxxxx密码"
```

**SSH密钥（配置服务器的git和本地提交需要用到**

打开Git Bash，生成SSH密钥 

```
  ssh-keygen -t rsa -C "emailAddress"
```

  获取 并配置公钥
    
```
   cat ~/.ssh/id_rsa.pub 
```

将显示的所有文字复制，然后在Github Settings>SSH keys里面进行配置

  **Token管理**

  1. Github Settings > Developer settings里面生成Token

  网页刷新后，token会消失，所以要及时保存

  2. 控制面板>用户账户>凭据管理器>Windows凭据>普通凭据
  
     添加普通凭据 
  
  **可能遇到的问题**
  
  直接进行修改
  
   $ git remote set-url origin [对应SSH/HTTPS仓库地址]
  
  先删除，然后添加
  
   $ git remote rm origin
   $ git remote add origin [对应SSH/HTTPS仓库地址]
  
  修改项目下的.git/config里面 remote里面的url
  
  ## hexo主题配置
  
  1. 在hexo官网下载合适的主题

  2. 从GitHub下载主题并将其添加到网站目录: themes

  3. 本地博客文件夹下找到themes文件夹（这是博客的主题文件   ，解压文件

  4. 编辑博客的配置文件`_config.yml`文件找到**theme**并设置值为`下载主题文件的名称``

  5. ``进入`themes/flex-block`编辑主题文件`_config.yml`以配置你的站点信息
  
  ### <font color=red face="黑体">config.yml分为本地博客配置和主题文件配置*</font>
  
  **hexo基本命令** cmd命令下启动
  
  - hexo clean 清除博客配置信息
  
  - hexo g -d 配置博客信息
  
  - hexo s 启动博客
  
  **cmd命令提示符，且需要保证在你自己建立的文件夹路径下，我在blog文件夹。**
  
  输入
  
  ```
  hexo s
  ```
  
  提示
  
  ```
  INFO  Validating config
  INFO  Start processing
  INFO  Hexo is running at http://localhost:4000/ . Press Ctrl+C to stop.
  
  ##访问链接:  http://localhost:4000 
  ```
  
  #### 打开博客配置文件_config.yml这个文件
  
  找到最下面，修改成
  
  ```
  deploy:
    type: git
    repo: git@你需要的链接地址GitHub或者git,阿里云
    branch: master
  ```
  
  ##### 安装hexo插件hexo-deployer-git
  
  ```
  npm install hexo-deployer-git --save
  ```
  
  hexo clean  ##第一个是生成本地静态文件
  
  hexo g -d ##第二个是发送到托管库（你链接的地址
  
  ## 博客主题的安装及修改
  
  打开[hexo官网](https://hexo.io/zh-cn/)