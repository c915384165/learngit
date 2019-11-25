# Git


git是什么？


> 世界最好的（没有之一）分布式版本控制系统。


## git的前世今生

> Linus--Linux之父在2002年用一周时间编写。

# Git入门

### 安装

[git Download](https://git-scm.com/downloads)

#### Mac

```sh
brew install
```
#### Win

> 略


# Git 本地仓库

### 创建版本库 init/add/commit

```sh
cd <folder> # 新建文件夹
git init # 创建版本库（生成.git文件夹）
git add <file> （添加文件）
git commit -m <message>  （提交文件）
git status （当前状态）
git log （日志文件）
git diff （查找改动）
```

> 注意：git只支持文本格式的文件；
> 文本编码用utf-8

### 查看状态 status / log / reflog / diff

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


> 小结：增删改查

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

# Git 远程仓库

## Github入门

### ssh-keygen

```sh
ssh-keygen -t rsa -C "<your email address>"
cd ~/.ssh
subl id_rsa.pub
```

> github也支持别的协议，如https。当ssh不能用时候可以用https。

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

### 从远程库克隆

```sh
git clone git@github.com:c915384165/learngit.git
```
