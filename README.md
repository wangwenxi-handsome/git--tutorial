# git_tutorial
注：*代表这条指令是进阶版

## git初始化
```
# 从本地文件夹初始化
git init

# fork(可选) + clone 远程代码库
git clone https://github.com/wangwenxi-handsome/git_tutorial.git
```

## git本地版本控制
<div align=center><img src="https://github.com/wangwenxi-handsome/git_tutorial/blob/main/fig/all-states.png"/></div>

### 记录改动
```
# 查看状态
git status

# 将工作区的改动加入暂存区
git add a.py
git add .    # 将当前目录下的所有改动一次性加入暂存区

# 将暂存区的改动记录到储存库
git commit -m "comment"

# 查看储存库的历史提交记录
git log
```

### 时光机
```
# 撤销工作区的修改
git checkout -- a.py
git checkout -- .    (一键撤销工作区的所有改动)

# 撤销暂存区的修改*
git reset HEAD a.py
git reset HEAD .    (一键撤销暂存区的所有改动)

# 回退到之前的版本(commit)
# HEAD指向当前版本，HEAD^是上一个版本，HEAD^是上上个版本
git reset --hard HEAD^
git reset --hard commitID   # commitID通过git log查看

# 回退失误了怎么办
# 查看所有历史操作
git reflog
```

## 分支操作
```
# 查看已有分支
git branch

# 新建分支
# 新建或切换分支前必须保证工作区是干净的
git checkout -b develop    # 新建并切换到develop分支
git checkout develop    # 切换到develop分支

# 如果工作区不是干净的，但代码还没有改完，希望保留工作区和暂存区的修改，这时怎么办*
git stash   # 将工作区和暂存区修改加入栈
git pop   # 将工作区和暂存区修改弹出栈

# 分支合并
git merge develop   # 将develop合并到master上，需要切换到master分支上执行

# 解决冲突
git status    # 查看哪些文件冲突，并进行修改，解决冲突
git add + git commit    # 提交一个新的commit

# 删除分支
git branch -d develop
```

### 分支合并示意图
<div align=center><img src="https://github.com/wangwenxi-handsome/git_tutorial/blob/main/fig/branch.png"/></div>
<div align=center><img src="https://github.com/wangwenxi-handsome/git_tutorial/blob/main/fig/merge.png"/></div>

### 团队合作方式
<div align=center><img src="https://github.com/wangwenxi-handsome/git_tutorial/blob/main/fig/flow.png"/></div>

## 远程操作
在git clone后，本地会生成一个叫做origin的指针指向远程代码库
```
# 查看已有的远程代码库指针*
git remote -v
git remote add 指针名 地址

# 推送本地代码
git push <远程主机名> <本地分支名>:<远程分支名>
git push origin develop:develop
git push    # 推送当前分支到远程，需要有跟踪关系

# 拉取远程代码
git pull <远程主机名> <远程分支名>:<本地分支名>
git pull origin develop:develop
git push    # 拉取远程分支到本地，需要有跟踪关系
```
