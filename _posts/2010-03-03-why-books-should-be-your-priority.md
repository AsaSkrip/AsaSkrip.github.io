---
date: 2020-11-22 12:26:40
layout: post
title: 关于git命令推送
subtitle: 学而不思则罔，思而不学则殆
description: 只是学习却不思考就会感到迷茫而无所适从,只是空想不学习就会心中充满疑惑而无定见。 
image: https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559822138/theme9_v273a9.jpg
optimized_image: https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559822138/theme9_v273a9.jpg
category: git命令推送送
tags:
  - books
  - read
author: mranderson
paginate: true
---


● 创建一个文件夹<br>
● 进入文件夹，鼠标右键，打开 Git Bash Here<br>
● 执行命令：git init<br>
● 随便创建个文件，写点代码<br>
● 让Git记住此时代码是什么样：<br>
  ○ git add .<br>
  ○ git commit -m '说明文字'<br>
● 随便修改一点代码<br>
  ○ git add .<br>
  ○ git commit -m '说明文字'<br>
● 随便修改一点代码，或新增一些文件，或删除一些文件<br>
  ○ git add .<br>
  ○ git commit -m '说明文字'<br>
● 执行 git log --oneline 查看你记录了几个版本了，方便看到版本号<br>
● 尝试执行 git reset --hard 版本号，将代码切换到历史版本4<br>



添加远程地址：<br>
● git remote add 别名 仓库地址<br>
移除远程地址：<br>
● git remote remove 别名<br>
查看远程地址：<br>
● git remote -v<br>


## 查看分支<br>
git branch<br>

## 创建新分支<br>
git branch 分支名<br>

## 切换分支<br>
git checkout 分支名<br>

## 合并分支<br>
git merge 分支名<br>

## 删除分支<br>
git branch -d 分支名<br>
git branch -D 分支名<br>





  ○ 执行 git pull  命令，以便在本地能够查看到所有的远程分支。<br>
  ○ git branch -a 查看的所有分支（-a 是 all 的意思，以便查看到所有的分支名）<br>
  ○ 依次 执行 git checkout 远程分支名  将所有分支检出（下载）到本地<br>
  ○ 切换到主分支或开发分支 git checkout master <br>
  ○ 依次合并 其他分支 git merge 其他分支名 <br>
  ○ 合并后，将master分支推送<br>
  ○ 其他成员 git pull origin master 拉取更新<br>



● 创建本地仓库并至少提交一次（把项目的初始模板、初始代码提交上去）<br>
  ○ 初始化一个项目，git init<br>
  ○ 添加初始的代码到暂存区 git add .<br>
  ○ 提交初始的代码到本地仓库 git commit -m "提交了初始的代码"<br>
● 推送到远程仓库<br>
  ○ git remote add origin 仓库地址<br>
  ○ git push -u origin master<br>
● 邀请成员<br>
  ○ 码云 -> 进入远程仓库 -> 管理 -> 仓库成员管理 -> 邀请成员<br>
  ○ 可以使用链接邀请，可以使用具体的用户名邀请<br>



## 安装命令<br>
npm install 包名<br>
npm i 包名                 ---  安装命令的简写<br>
npm i 包名 包名 包名        --- 一次性安装多个包<br>
npm i 包名@版本号           --- 安装指定的版本<br>
npm i 包名 -D              --- 安装开发依赖（开发阶段才能用得上，项目做完就用不上了）<br>

## 卸载命令<br>
npm uninstall 包名<br>
npm un 包名                --- 卸载命令的简写<br>
npm un 包名 包名 包名       --- 一次性卸载多个包<br>

windows系统：<br>
npm i -g nrm<br>

Mac系统：<br>
sudo npm i -g nrm<br>

nrm ls         ---- 查看有哪些镜像源可用<br>

nrm use taobao ---- 切换镜像源为淘宝<br>
nrm use npm    ---- 切换镜像源为npm主站<br>

nrm test       ---- 测试镜像源的速度<br>


npm run serve<br>


npm run build 打包结果<br>


## 使用less，需要安装下面的包<br>
npm i less-loader less -D           #（@vue/cli 5.0.1，直接安装）<br>

## 使用scss，需要安装下面的包<br>
npm i sass sass-loader -D <br>









