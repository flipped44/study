# git教程

##### 配置git

首先配置自己的用户名和邮箱

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

##### 创建版本库

1. `mkdir 项目名字` 创建项目库
2. `cd 项目名字` 进入项目
3. `pwd`  显示当前目录
4. `git init` 把这个目录变成git可以管理的仓库

##### 把大象放进冰箱需要三步

1. `git add 文件名字`   把文件添加到仓库
2. `git commit -m "本次提交的说明"`  
3. `git status` 查看结果/仓库的状态
4. `git diff` 具体查看改了什么\
5. `git log` 显示最近到最远的提交日志`--pertty=oneline` 输出一串修改的参数
6. `git reset --hard HEAD(id号)`  退回到以前的版本
7. `git reflog` 查看每一个commit id 的命令\
8. `git checkout -- 文件名` 丢弃工作区的修改
9. `git reset HEAD <file>` 可以把暂存区的修改撤销掉(unstage),重新放到工作区

小结:

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD <file>`，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考[版本回退](https://www.liaoxuefeng.com/wiki/896043488029600/897013573512192)一节，不过前提是没有推送到远程库。

##### 远程仓库

1. `ssh-keygen -t rsa -C "youremail@example.com"` 创建SSH key
2. `git remote add origin 仓库链接` 在本地用这个命令关联到远程仓库
3. 



