# 文档说明 20200915

## 准备工作
```
1、安装node.js
https://nodejs.org/en/download/
查看版本号 node –v、npm –v 出现版本号即安装成功。（如未出现，请重启电脑后再试）node8.9或以上版本

2、管理nodejs版本（非必装）
执行命令安装：npm install -g n
n latest  (升级node.js到最新版)
n stable（升级node.js到最新稳定版）
n 后面也可以跟随版本号，例如：$ n v0.10.26 或者 $ n 0.10.26

3、全局安装vue-cli3.0脚手架
卸载：如果已经全局安装了旧版本的vue-cli(1.x 或 2.x)，需要先卸载：npm uninstall vue-cli -g
安装：npm install -g @vue/cli
查看版本号：vue -V，出现版本号即安装成功。
3.0对2.0版本的桥接：npm install –g @vue/cli-init

4、安装淘宝镜像 cnpm (非必装，网络慢的情况可安装)
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

## git使用
```
GIT基础命令（粘贴 shift + insert）
--------------------------------
拷备项目：git clone <仓库地址>
创建分支：git branch <name>
创建并进入分支：git checkout –b <nam>
查看状态：git status
添加所有文件：git add .
提交：git commit –m ‘这里是当前提交的描述’
拉取：git pull
推送：git push
查看分支：git branch --list
查看分支（包含远程分支）：git branch -a
```

## 构建项目
```
vue create vue-admin
--------------------
1.Merge
2.Manually(Babel,Router,Vuex,CSS,Linter)
3.N(use history mode)
4.Sass/SCSS(with node-sass)
5.ESLint+Prettier
6.Lint to Save
7.In dedicated config files
8.N(save this as a preset)

```
## 构建项目出错
```
AppData\Roaming\npm\vue.ps 因为在此系统禁止运行脚本
-------------------------------------------------
管理员--》运行POWERSHELL--》et-ExecutionPolicy RemoteSigned--》Y/A就好了
```

## 运行项目
```
npm run serve
```