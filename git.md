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
在我们进行了多次提交后，可以使用
```
git log
```
来查看每次提交的细节，使用`git log --pretty=oneline`可以查看简化版的输出信息。其中包含了每次
提交的**commit id**和说明的内容。
git中使用**HEAD**指向当前的版本，**HEAD^**指向上一个版本，**HEAD~10**指向向上10个版本。
通过
```
git reset --hard HEAD^
```
可以将版本回退至上一次提交的版本，同理可回退至前若干个版本。
通过
```
git reset --hard <commit id>
```
可以将版本跳跃至对应的**commit id**的提交版本，但是`git log`不会显示当前版本之后的提交内容，
使用
```
git reflog
```
可以查看我们执行过的每条命令，从而找到我们目标版本的**commit id**。

git管理的是文件的修改，而非文件本身。我们每次使用`git add`会将当前的修改放进暂存区，而后续继续
对文件的修改则需要新的add操作。可以通过
```
git checkout -- <filename>
```
放弃对工作区内文件的修改，通过
```
git reset HEAD <filename>
```
放弃暂存区内的修改。
git中删除操作也是一种修改，从版本库中删除文件可以用`git rm`删除并使用`git commit`提交修改，通过
上述的版本库穿梭、撤销修改的操作也可以实现恢复文件的操作。

# 远程仓库
git的最突出特点之一就是远程仓库，可以将一台电脑的git仓库方便地克隆到其他电脑里。GitHub就是著名的
免费提供git仓库托管服务的网站，注册GitHub账号即可免费获得git远程仓库。本地的git仓库和GitHub仓库间
的传输通过ssh协议进行，所以需要先进行ssh设置。

- 创建ssh key
```
ssh-keygen -t -rsa -C <email>
```
- 在主目录下找到`.ssh`目录，找到**id_rsa.pub**文件
- 登陆GitHub，在**settings->SSH Keys**页面添加**id_rsa.pub**的内容

## 添加远程库
在GitHub上创建一个新的仓库，创建页面会提示使用
```
git remote add origin git@github.com:username/repo.git
```
在本地链接远程库，通过
```
git push -u origin master
```
将本地的master分枝推送到远程，第一次使用是会有验证GitHub服务器的SSH Key的警告，输入yes来将GitHub服务器
的SSH Key添加到本地的信任列表里。

## 从远程库克隆
通过
```
git clone <url>
```
的方式可以将远程库克隆到本地。

# git的分支管理
git将每次提交串成一条时间线，每条时间线被称为一个分支，默认情况下有一条主分支master。多人协作时，为了
不妨碍他人的工作，可以创建新的分支进行修改，在修改完成后再和master分支合并。

通过
```
git branch dev
git checkout dev
```
可以创建一条新的名为`dev`的分支并指向它。也可以使用`git checkout -b dev`一步完成这个操作。
通过`git branch`可以查看所有的分支，当前分支前会有一个`*`号。




## git使用
### git特性
