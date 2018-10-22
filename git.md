# git简介
## git安装
查看是否安装git
`which git`
使用`apt-get`，`yum`，`pacman`等方式安装git，Mac可以使用homebrew进行安装

首先进行用户设置
```
git config --global user.name "name"
git config --global user.email "mail"
```
直接使用
`git config`
会显示更多设置选项

## 创建版本库
版本库也叫仓库(repository，即常说的repo)，其本质上是一个目录文件，其下的所有文件被git
所管理，每个文件的修改、删除都能被git跟踪，从而我们可以在任何时刻追踪文件的历史或将其
还原到某个历史版本。

选择一个我们希望被git管理的目录，然后执行
```
git init
```
即可将该目录变成git可以管理的仓库，可以发现目录下多了一个**.git**目录
使用
```
git status
```
可以方便地查看当前版本库的状态

## 向版本库添加文件
git能跟踪版本库内所有文本文件的每次改动，具体到哪一行增删了哪些词都会记录。对于二进制文件，
git只能跟踪其大小的变化。

使用
```
git add <filename>
```
可以将文件添加到版本库，其中文件名可以使用通配符，如`git add *`可将目录下的所有文件都添加
到版本库，实际上是提交到了暂存区。
使用
```
git commit -m "comment"
```
可以将暂存区的文件提交到版本库，**comment**部分用来解释本次提交的代码改动说明，方便日后查看。
```
git diff
```
可以告诉我们上次提交之后版本库进行了何种修改。

# 版本穿梭

## git使用
### git特性
