# Git文档
## Git常规操作
### 申明自己的名称及邮箱
- 申明用于表示本分布式节点的名称信息等，global表示所有git仓库都使用这个配置
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

### 查看历史修改记录
- 查看当前仓库修改历史，查看到的SHA1值可以用来进行跳到指定的版本，查询到的HEAD，表示当前版本
``` shell
git log
```

### 跳转到指定版本
``` shell
git reset --hard [HEAD~NUM|SHA1]  //example: git reset --hard HEAD~10 跳到当前HEAD之前第10个版本
```

### 查看历史命令
``` shell
git reflog
```

### 撤销已修改，但为及提交到暂存区的修改，包括错误删除后要恢复
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

### 其他说明
- Git版本控制不能跟踪二进制文件的行级修改记录，二进制文件只能记录大小变化
- Git中，HEAD表示当前版本,HEAD^表示上一个版本，HEAD^^表示上上一个版本，HEAD~#（HEAD~2表示上2个版本）表示上#个版本
- 跳转到之前的版本后，不能直接提交修改成最新
