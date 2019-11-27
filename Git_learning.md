# Git版本控制

## 简介

git是什么？

> 分布式版本控制系统

如何安装?

> 下载地址：[git Download](https://git-scm.com/downloads)
> 步骤略

设置用户名和邮箱

```sh
git config --global user.name "<user name>"
git config --global user.email <email for github>
```

## Git 本地仓库

创建版本库 

```sh
cd <folder> # 新建文件夹
git init # 创建版本库（生成.git文件夹）
```

### 添加文件

```sh
git add <file> #（添加文件）
```


### 提交文件

```sh
git commit -m <message>  #（提交文件）
```

### 查看

```sh
git status #（当前状态）
git log #（日志文件）
git diff #（查找改动）
```

> 注意：git只支持文本格式的文件；
> 文本编码用utf-8


### Git 回到未来（版本切换） reset

当需要返回到之前的版本，需要reset命令

```sh
git reset --hard HEAD^ # 返回上个版本，如果上两个^^, 
git reset --hard HEAD~100 # 返回上100个版本
git reset --hard <commit id> # 写前几位即可，不要少于3位
git log # 查修改历史
git reflog # 查命令历史
```

> ==reflog==和==log==两个命令查询修改历史，reset --==hard== HEAD^ 到指定的版本。hard的功能暂时不讲。


### 工作区vs缓冲区

工作区 working Directory：

缓冲区 stage（index）：

#### add的作用

工作区-> stage（缓存区）

#### commit的作用

stage -> master branch

#### 版本库 Repository

.git

### 如何取消最近的修改 checkout

checkout \---\--- \<file name>

将返回至最近一次add或commit之前的状态。

> checkout还有切换分支的功能，后续内容会介绍。
> \---\---不能省略。


### 删除文件 rm

```sh
git rm
```



### 小结：增删改查

* 创建版本库（.git）init
* 删除

    * 删除文件：rm
* 改
    * 取消修改 checkout \---\--- <file>
    * add：添加至缓存区
    * commit：提交修改
    * reset：返回指定版本
        * \---\---hard HEAD^ (~100)
        * \---\--- \<commit id>
* 查
    * diff
    * status
    * log
    * reflog

缓冲区/工作区的概念

## 02 Git 远程仓库

### SSH 协议
在使用github远程库前，需要了解协议。
github支持多种传输协议，包括ssh和https等。
这里介绍下ssh协议。
使用ssh协议前首先生成密钥。
生成密钥的命令，打开终端使用ssh-keygen命令。
#### ssh-keygen

```sh
ssh-keygen -t rsa -C "<your email address>"
cd ~/.ssh
subl id_rsa.pub
```
github设置有ssh相关选项，将生成的公钥复制后提交即可使用。


将生成的公钥复制后添加到Github中。（具体操作略）


### 从本地推送

#### 网页新建远程库（Create a new repo）

#### 关联一个远程库

```sh
git remote add origin git@github.com:c91384165/learngit.git

```

#### 推送

```sh
git push -u origin master # 第一次用 -u 参数
```

如果想把当前文件夹所有的都推出去

```sh
git push . origin master
```


### 从远程库克隆

```sh
git clone git@github.com:c915384165/learngit.git
```

### 从远程库合并

```sh
git pull
```

### 远程分支与本地分支建立关联

当提示`no tracking information`时候。

```sh
git branch --set-upstream-to <branch-name> origin/<branch-name>
```
## 03 分支

### About branch

* What is branch?
* Why we use branch?
* How we use branch?
* When & where we use branch?

#### what

仅为个人见解如下：
条条大路通罗马。
branch就像一条路。可能是大路，也可能是小路。
当路不好走，我们就要修路。
但为了保证交通正常，必须有其他的路可走。
这样修路时，别的路也能走，不影响交通。
修好的路可能是高速路，八车道。
以后就用新路走。
但是如果路修坏了，挖到坑了，或者挖不通。
原来的路还能用。
我们还有时间想别的办法。

#### why

当几个人共同开发一个软件的时候。为了提高效率，同时避免出错。

### 创建分支

```sh
git branch <branch name> # 创建分支
git switch -c <branch name> # 创建并切换分支
git branch # 查看分支
```
### 切换分支
```sh
git switch <branch name>
```
checkout也可以切换/创建分支，但是容易弄混，这个新命令更好用。
### 合并分支

```sh
git merge <branch name> # 将<name>融入当前分支。
git merge --no-ff -m "<message>" <branch name>
```
融合分支有时会遇到冲突。比如两个文件都提交过修改，但是改的内容不同。可以通过修改文件的方式保证融合。

### 删除分支

```sh
git branch -d <branch name> # 删除分支

```

### 查看分支

```sh
git log --graph --pretty=oneline
```

### stash(藏匿)

#### git stash

stash“储藏”当前工作现场，等以后恢复继续工作。

```sh
git stash # 添加一个 stash
git stash list # 列表
git stash apply stash@{0} # 恢复
git stash drop # 删除
git stash pop # 恢复并删除
```

#### git cherry-pick （摘樱桃）

需要载入其他修改时候，使用这个。

```sh
git cherry-pick <commit id>
```
