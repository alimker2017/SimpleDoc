# Git文档
## Git常规操作
### 申明自己的名称及邮箱
- 申明用于表示本分布式节点的名称信息等，global表示所有git仓库都使用这个配置，否则只对当前仓库生效
``` shell
git config --global user.name = alimker  
git config --global user.email my_email@myemail.com
```

### 创建版本库
- 创建版本库（如下名称：my_repository_name），并且初始化，初始化会创建.git目录，默认是空仓库
``` shell
mkdir my_repository_name
cd my_repository_name
git init
```

### 将文件加入到暂存区(stage)
``` shell
git add new_files.c
```

### 将暂存区中的文件提交到**本地仓库**的当前选择分支
- 无论是提交新建的文件，还是已修改的文件，都需要**先调用add**
``` shell
git commit -m "some log for commit files"
```

### 查看仓库当前状态
- 调用命令后，第一行 On branch XXX，表示在XXX分支上
``` shell
git status
```

### 查看文件修改详情
- 修改记录表示：+表示新增行，-表示删除行，如果是在某行里面做了修改，记录会有2条，第1条：删除修改前的行内容，第2条：新增修改后的行内容，如果有N行被修改，那么前N行就是被修改前的记录，后N行是被修改后的记录
``` shell
git diff forget_changed_file.c
```

### 查看分支历史修改记录
- 查看当前仓库分支修改历史，查看到的SHA1值可以用来进行跳到指定的版本，查询到的HEAD，表示当前版本
``` shell
git log  //查看分支修改记录
git log --graph    //查看分支修改记录及合并图
```

### 跳转到指定版本
``` shell
git reset --hard [HEAD~NUM|SHA1]  //example: git reset --hard HEAD~10 跳到当前HEAD之前第10个版本
git reset --hard origin/branch_name  //跳转当前分支到远程最新版本
```

### 查看历史命令
``` shell
git reflog
```

### 撤销已修改但还没有提交到暂存区的修改，或者恢复错误删除掉的文件
``` shell
git checkout -- filename    // -- 不能省略，否则就是切换到其他分支了
```

### 撤销已经提交到暂存区的修改
``` shell
git reset HEAD filename
```

### 删除文件
``` shell
git rm filename
```

### 查看分区信息
``` shell
git branch  //查看本地有哪些分支
git branch -a  //查看本地及远程仓库有哪些分支
```

### 创建分支
``` shell
git branch branch_name  //在当前分支上创建branch_name
git checkout branch_name  //切换到branch_name上
git checkout -b branch_name  //在当前分支上创建分支branch_name,并切换到branch_name上
git push origin branch_name  //将新创建的branch_name分支提交到远程仓库中
```
### 切换分支
- **注意，如果切换分支之前，当前分支有修改文件内容，但是没有commit，修改内容会被带到新分支中**
- **如果在切换前的分支(m1)中做了修改，并没有提交，但是在切换后的分支(m2)中把修改提交了，切换前的分支(m1)中的修改会被撤除，导致在之前的分支(m1)中的修改都没了**
``` shell
git checkout branch_name  //从当前分区企鹅蛋到branch_name
```
### 修改本地分支名
``` shell
git branch -m old_branch_name new_branch_name  //修改本地分支名
```

### 删除分支
``` shell
git branch -d branch_name  //删除本地分支branch_name
git branch -D branch_name  //如果本地分支branch_name没有被合并，那么就必须用-D强行删除
git push --delete origin branch_name  //删除远程分支branch_name
```

### 修改远程仓库分支名
1：创建本地分支名，后者修改本地分支名
2：推送新的分支到仓库 git push origin branch_name
3：删除远程分支 git push --delete origin branch_name

### 合并分支
``` shell
git merge branch_name  //将branch_name合并到当前分支上
```

### bug分支
``` shell
git stash  //将当前分区做的修改(可能由于没有修改成功，不能提交的修改)临时存储起来，防止切换分区的时候将修改带到新的分区中
git stash list  //查看临时存储区存储的工作现场
git stash apply  //从临时存储区恢复最近的工作现场，但不删除临时存储区数据
git stash drop  //删除临时存储区存储的工作现场内容
git stash apply stash@{1}  //从临时存储区恢复list为1的现场
```

### 关联Github中的仓库到已经创建的本地仓库（适用于先有项目，然后再加入到Git管理中）
``` shell
git remote add origin git@github.com:my_github_account/mygit_repository_name.git  (SSH方式)
git remote add origin https://github.com/my_github_account/mygit_repository_name.git  (HTTPS方式)
// origin 是git默认的远程库叫法，可以修改成其他名称
git push -u origin master  //关联后第一次推送消息应该使用 -u参数 ，目的是关联分支
git push origin master  //第一次推送后，以后就可以不用-u参数了
```

### 从远程看克隆仓库到本地（适用于项目刚开始就直接上Git）
``` shell
git clone git@github.com:my_github_accout/mygit_repository_name.git  (SSH方式)
git clone https://github.com/my_github_accout/mygit_repository_name.git  (HTTPS方式)
```

### 删除关联的远程库
``` shell
git remote rm origin
```

### 查询远程库信息
``` shell
git remote
git remote -v //显示远程库详情，包含了可以抓取及推送的仓库
```

### 推送分支
``` shell
git push origin branch_name   //推送分支到远程库中的branch_name分支中
```

### 抓取当前分支最新数据
``` shell
git pull
```

### 设定本地分支与远程分支的关联，关联后可以调用pull抓取
``` shell
git branch --set-upstream branch_name origin/branch_name
```
### 下载远程库中的分支
``` shell
git checkout -b branch_name origin/branch_name
```

### 创建标签
``` shell
git tag v1.0  //给当前分支上的commit id创建一个v1.0的标签
git tag v1.1 6655443  //给指定commit id创建一个v1.1的标签
git tag -a v1.2 -m "标签说明文字" 6655443  //打标签的时候写上说明
```

### 查看所有标签
``` shell
git tag
```

### 查看指定标签的详情
``` shell
git show v1.1   //查看标签名=v1.1的标签的详情
```
### 删除标签
``` shell
git tag -d v1.1
```

### 推送标签到远程库
``` shell
git push origin tag_name  //推送指定标签到远程库
git push origin --tags  //推送全部未推送的标签到远程库
```

### 删除远程库中的标签
- 先删除本地标签库，再删除远程库中的标签
``` shell
git tag -d v1.1  //1:先删除本地的标签
git push origin :refs/tags/v1.1  //2:删除远程库中的标签
```

### 给命令设置别名
``` shell
git config --global alias.st status  //设置st表示status  git status = git st
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
  //git log命令的超清晰参数，使用 git lg
```

### 其他说明
- Git版本控制不能跟踪二进制文件的行级修改记录，二进制文件只能记录大小变化
- Git中，HEAD表示当前版本,HEAD^表示上一个版本，HEAD^^表示上上一个版本，HEAD~#（HEAD~2表示上2个版本）表示上#个版本
- 跳转到之前的版本后，不能直接提交修改成最新
- 忽略特殊文件，使用 .gitignore文件描述要忽略的文件github提供了一些常用的忽略文件：https://github.com/github/gitignore
- 每个仓库的配置文件存放在仓库目录下的:.git/config文件中
- 全局配置是放在当前用户家目录下的.gitconfig文件中
- 搭建git，看廖雪峰blog
