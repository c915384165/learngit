# GIT CHEAT SHEET GIT作弊表

## CREATE 创建

Clone an existing repository<br>
复制一个存在的仓库

```sh
$ git clone ssh://user@domain.com/repo.git
$ git clone git@github.com:c915384165/learngit.git

```

使用ssh协议生成密钥

```sh
ssh-keygen -t rsa -C "<your email address>"
cd ~/.ssh
subl id_rsa.pub
```

Create a new local repository<br>
创建一个新的本地仓库

```sh
$ git init
```

设置用户名和邮箱

```sh
$ git config --global user.name "<user name>"
$ git config --global user.email <email for github>
```

## LOCAL CHANGES 本地库修改

Changed files in your working directory<br>
查看工作目录下文件的修改状态

```sh
$ git status
```

Changes to tracked files<br>
查看文件的修改情况

```sh
$ git diff
```

Add all current changes to the next commit<br>
添加文件

```sh
$ git add <file> #（添加文件）
```
Add some changes in <file> to the next commit<br>
提交文件

```sh
$ git commit -m "<message>"  #（提交文件）
```

> \-m: add commit messege

Commit all local changes in tracked files<br>
添加所有更改到提交序列

```sh
$ git add .
```

Commit previously staged changes<br>
对文件添加一些修改并发送到提交序列。 [wait-for][?]

```sh
$ git add -p <file>
```

Commit all local changes in tracked files<br>
提交更改（所有文件？）

```sh
$ git commit -a
```

Commit previously staged changes<br>
提交更改（前边的文件）

```sh
$ git commit
```

Change the last commit<br>
提交更改（最后）

> Don't amend published commits!

```sh
$ git commit --amend
```

stash“储藏”当前工作现场，等以后恢复继续工作。

```sh
$ git stash # 添加一个 stash
$ git stash list # 列表
$ git stash apply stash@{0} # 恢复
$ git stash drop # 删除
$ git stash pop # 恢复并删除
```

载入指定修改时候，使用这个。

```sh
$ git cherry-pick <commit id>
```

## COMMIT HISTORY 提交历史

Show all commits, starting with newest<br>
列出所有提交，从最近一次开始。

```sh
$ git log
$ git log --graph --pretty=oneline
```

> * \\--oneline: 压缩模式，在每个提交的旁边显示经过精简的提交哈希码和提交信息，以一行显示。
> * \\--graph: 图形模式，使用该选项会在输出的左边绘制一张基于文本格式的历史信息表示图。如果你查看的是单个分支的历史记录的话，该选项无效。
> * \\--all: 显示所有分支的历史记录

------

[wait-for]

```sh
$ git reflog
```
------

Show changes over time for a specific file （spicific = 指定的特定的）<br>
查看指定文件的更改

```sh
$ git log -p <file>
```
> Git 假定所有的改变都是针对同一件事情的，因此它把这些都放在了一个块里。你有如下几个选项：
> 
> * 输入 y 来暂存该块
> * 输入 n 不暂存
> * 输入 e 手工编辑该块
> * 输入 d 退出或者转到下一个文件
> * 输入 s 来分割该块
> 在我们这个例子中，最终是希望分割成更小的部分，然后有选择的添加或者忽略其中一部分。


Who changed what and when in <file><br>
看看都谁改了文件啥时候改的（问责么？）

```sh
$ git blame <file> # （blame = 混蛋的该死的）
```

## BRANCHES & TAGS 分支和标签


List all existing branches<br>
列出所有分支(包括远程的)

```sh
$ git branch -av
$ git branch --set-upstream-to <branch-name> origin/<branch-name> # 远程分支与本地分支建立关联
```

Switch HEAD branch<br>
切换HEAD分支

```sh
$ git checkout <branch>
```

Create a new branch based on your current head<br>
新建分支以当前分支指针位置为基础

```sh
$ git branch <new-branch>
```

Create a new tracking branch based on a remote branch<br>
新建一个分支以远程分支为基础

```sh
$ git checkout --track <remote/branch>
```

Delete a local branch<br>
删除本地分支

```sh
$ git branch -d <branch>
$ git branch -D <branch> # 强制删除
```

Mark the current commit with a tag<br>
当前提交添加标签

```sh
$ git tag <tag-name>
```

## UPDATE & PUBLISH 更新和发布

List all currently configured remotes<br>
列出所有最近的远程

```sh
$ git remote -v
```

Show information about a remote<br>
列出信息远程

```sh
$ git remote show <remote>
```

Add new remote repository, named <remote><br>
添加一个新的远程库

```sh
$ git remote add <shortname> <url>
$ git remote add origin git@github.com:c91384165/learngit.git
```

Download all changes from <remote>, but don't integrate into HEAD<br>
从远程库下载所有更改，但是不要融入当前

```sh
$ git fetch <remote>
```

Download changes and directly merge/integrate into HEAD<br>
从远程库下载并整合

```sh
$ git pull <remote> <branch>
```

Publish local changes on a remote<br>
发布本地更改到远程库

```sh
$ git push <remote> <branch>
$ git push -u origin master # 第一次用 -u 参数
$ git push . origin master
```

Delete a branch on the remote<br>
删掉远程库的分支

```sh
$ git branch -dr <remmote/branch>
```

Publish your tags<br>
发布标签

```sh
$ git push --tags
```

## MERGE & REBASE 融合和压缩

Merge <branch> into your current HEAD<br>
融合分支到当前的指针（HEAD）

```sh
$ git merge <branch>
$ git merge --no-ff -m "<message>" <branch name>
```

Rebase your current HEAD onto <branch><br>
压缩当前的指针到分支

> Don't rebase published commits!

```sh
$ git rebase <branch>
```

Abort a rebase<br>
退出压缩

```sh
$ git rebase --abort
```

Continue a rebase after resolving conflicts （resolving = 解决，conflicts = 冲突）<br>
继续一个压缩在解决冲突后

```sh
$ git rebase --continue
```

多个commit压缩成一个

```sh
$ git rebase -i HEAD~[number_of_commits]
$ git rebase -i HEAD~2 # 压缩最后2个commit
```

> 当你提交代码进行代码审查时或者创建一次pull request (这在开源项目中经常发生)，你的代码在被接受之前会被要求做一些变更。于是你进行了变更，并且直到下一次审查之前你没有再次被要求进行变更过。在你知道又要进行变更之前，你已经有了一些额外的commit。理想情况下，你可以用rebase命令把多个commit压缩成一个。


Use your configured merge tool to solve confilicts （configured = 配置， solve = 解决）<br>
使用你指定的融合工具来解决冲突

```sh
$ git mergetool
```

Use your editor to manually solve conflicts and (after resolving) mark files as resolved<br>
使用你的编辑器来手动解决冲突，（和在解决后）标记文件->解决的

```sh
$ git add <resolved-file>
$ git rm <resolved-file>
```

## UNDO 撤销操作

Discard all local changes in your working directory （discard = 丢弃）<br>
丢弃工作目录的所哟本地更改

```sh
$ git reset --hard HEAD
$ git reset --hard HEAD^ # 返回上个版本，如果上两个^^, 
$ git reset --hard HEAD~100 # 返回上100个版本
$ git reset --hard <commit id> # 写前几位即可，不要少于3位
```

Discard local changes in a specific file<br>
丢弃指定文件的本地更改

```sh
$ git checkout HEAD <file>
```

Revert a commit (by producing a new commit with contrary changes) （revert = 恢复，回复，contrary = 相反的）<br>
恢复一次提交

```sh
$ git revert <commit>
```

Reset your HEAD pointer to a previous commit...and discard all changes since then<br>
将head指针重新只想commit id

```sh
$ git reset --hard <commit>
```

...and preserve all changes as unstaged changes （preserve = 保护）<br>
并保护所有改变

```sh
$ git reset <commit>
```

...and preserve uncommitted local changes<br>
并保护未提交的本地更改

```sh
$ git reset --keep <commit>
```

## HELP & DOCUMENTATION 帮助和文档

Get help on the command line<br>
得到命令的帮助

```sh
$ git help <command>
```
