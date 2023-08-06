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

Cas sociis natoque penatibus et magnis <a href="#">dis parturient montes</a>, nascetur ridiculus mus. *Aenean eu leo quam.* Pellentesque ornare sem lacinia quam venenatis vestibulum. Sed posuere consectetur est at lobortis. Cras mattis consectetur purus sit amet fermentum.

> Curabitur blandit tempus porttitor. Nullam quis risus eget urna mollis ornare vel eu leo. Nullam id dolor id nibh ultricies vehicula ut id elit.

Etiam porta **sem malesuada magna** mollis euismod. Cras mattis consectetur purus sit amet fermentum. Aenean lacinia bibendum nulla sed consectetur.

<!--page-->

## Inline HTML elements

HTML defines a long list of available inline tags, a complete list of which can be found on the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTML/Element).

- **To bold text**, use `<strong>`.
- *To italicize text*, use `<em>`.
- Abbreviations, like <abbr title="HyperText Markup Langage">HTML</abbr> should use `<abbr>`, with an optional `title` attribute for the full phrase.
- Citations, like <cite>&mdash; Thiago Rossener</cite>, should use `<cite>`.
- <del>Deleted</del> text should use `<del>` and <ins>inserted</ins> text should use `<ins>`.
- Superscript <sup>text</sup> uses `<sup>` and subscript <sub>text</sub> uses `<sub>`.

Most of these elements are styled by browsers with few modifications on our part.

<!--page-->
● 创建一个文件夹
● 进入文件夹，鼠标右键，打开 Git Bash Here
● 执行命令：git init
● 随便创建个文件，写点代码
● 让Git记住此时代码是什么样：
  ○ git add .
  ○ git commit -m '说明文字'
● 随便修改一点代码
  ○ git add .
  ○ git commit -m '说明文字'
● 随便修改一点代码，或新增一些文件，或删除一些文件
  ○ git add .
  ○ git commit -m '说明文字'
● 执行 git log --oneline 查看你记录了几个版本了，方便看到版本号
● 尝试执行 git reset --hard 版本号，将代码切换到历史版本4



添加远程地址：
● git remote add 别名 仓库地址
移除远程地址：
● git remote remove 别名
查看远程地址：
● git remote -v


# 查看分支
git branch

# 创建新分支
git branch 分支名

# 切换分支
git checkout 分支名

# 合并分支
git merge 分支名

# 删除分支
git branch -d 分支名
git branch -D 分支名





  ○ 执行 git pull  命令，以便在本地能够查看到所有的远程分支。
  ○ git branch -a 查看的所有分支（-a 是 all 的意思，以便查看到所有的分支名）
  ○ 依次 执行 git checkout 远程分支名  将所有分支检出（下载）到本地
  ○ 切换到主分支或开发分支 git checkout master 
  ○ 依次合并 其他分支 git merge 其他分支名 
  ○ 合并后，将master分支推送
  ○ 其他成员 git pull origin master 拉取更新


v

● 创建本地仓库并至少提交一次（把项目的初始模板、初始代码提交上去）
  ○ 初始化一个项目，git init
  ○ 添加初始的代码到暂存区 git add .
  ○ 提交初始的代码到本地仓库 git commit -m "提交了初始的代码"
● 推送到远程仓库
  ○ git remote add origin 仓库地址
  ○ git push -u origin master
● 邀请成员
  ○ 码云 -> 进入远程仓库 -> 管理 -> 仓库成员管理 -> 邀请成员
  ○ 可以使用链接邀请，可以使用具体的用户名邀请



# 安装命令
npm install 包名
npm i 包名                 ---  安装命令的简写
npm i 包名 包名 包名        --- 一次性安装多个包
npm i 包名@版本号           --- 安装指定的版本
npm i 包名 -D              --- 安装开发依赖（开发阶段才能用得上，项目做完就用不上了）

# 卸载命令
npm uninstall 包名
npm un 包名                --- 卸载命令的简写
npm un 包名 包名 包名       --- 一次性卸载多个包

windows系统：
npm i -g nrm

Mac系统：
sudo npm i -g nrm

nrm ls         ---- 查看有哪些镜像源可用

nrm use taobao ---- 切换镜像源为淘宝
nrm use npm    ---- 切换镜像源为npm主站

nrm test       ---- 测试镜像源的速度


npm run serve


npm run build 打包结果


# 使用less，需要安装下面的包
npm i less-loader less -D           #（@vue/cli 5.0.1，直接安装）

# 使用scss，需要安装下面的包
npm i sass sass-loader -D 









