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

### 将文件纳入管理体系
``` shell
git add new_files.c
```

### 将纳入管理体系的文件提交到**本地仓库**
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

### 其他说明
- Git版本控制不能跟踪二进制文件的行级修改记录，二进制文件只能记录大小变化
