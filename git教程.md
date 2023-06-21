# git教程

#### 配置git

首先配置自己的用户名和邮箱

```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

#### 创建版本库

1. `mkdir 项目名字` 创建项目库
2. `cd 项目名字` 进入项目
3. `pwd`  显示当前目录
4. `git init` 把这个目录变成git可以管理的仓库

#### 把大象放进冰箱需要三步

1. `git add 文件名字`   把文件添加到仓库
2. `git commit -m "本次提交的说明"`  
3. `git status` 查看结果/仓库的状态
4. `git diff` 具体查看改了什么\
5. `git log` 显示最近到最远的提交日志`--pertty=oneline` 输出一串修改的参数,`git log --graph --pretty=oneline --abbrev-commit`,这个命令用于查看分支历史。
6. `git reset --hard HEAD(id号)`  退回到以前的版本
7. `git reflog` 查看每一个commit id 的命令\
8. `git checkout -- 文件名` 丢弃工作区的修改
9. `git reset HEAD <file>` 可以把暂存区的修改撤销掉(unstage),重新放到工作区

##### 小结:

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`。

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD <file>`，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考[版本回退](https://www.liaoxuefeng.com/wiki/896043488029600/897013573512192)一节，不过前提是没有推送到远程库。

#### 远程仓库

1. `ssh-keygen -t rsa -C "youremail@example.com"` 创建SSH key
2. `git remote add origin 仓库链接` 在本地用这个命令关联到远程仓库
3. `git push -u origin master` 把本地库的所有内容推送到远程库上,第一次推送加上`-u`参数,git会把本地的`master`分支内容推送到新的`master`分支,并且还会把本地的`master`分支和远程的`master`分支关联起来,在以后得推送或者拉取时就可以简化命令。
4. `git remote -v`查看远程信息,根据名字删除`git remote rm "分支名字"`
5. `git clone '链接' `克隆远程仓库 

#### 分支管理

##### **创建于合并分支:**

1. `git check -b dev` 创建dev分支切换到dev分支,`-b`表示创建并切换,相当于`git branch dev`&`git checkout dev`
2. `git branch`  查看当前分支,`-d 分支名字`表示删除那个分支
3. `git merge` 用于合并指定分支到当前分支
4. `git switch -c 分支名字`  创建并切换到新的dev分支
5. `git remote rm origin` 删除已关联的名为origin的远程库

##### 解决冲突:

git无法自动合并分支时,就必须首先解决冲突,使用`git stasus`命令来查看冲突的文件,手动修改文件,修改完成后,在提交,使用`git log --graph`查看分支合并图

##### 分支管理策略：

合并分支时，加上`--no--ff`参数可以用普通模式合并,合并后会有历史分支,清楚的看到曾经做的合并,`fast forward`合并之后看不出来曾经做过合并

##### bug管理：

- `git stash`命令可以把工作现场"储藏起来"

- `git stash list` 用这个命令查看之前的工作

- 恢复现场有两种方法`git stash apply` & `git stash pop`,  

  `git stash apply` 恢复后stash的内容不会删除,需要`git stash drop`进行删除

  `git stash pop`恢复的同事也会把其中的内容删掉

  `git stash apply stash@{0}`可以多次使用,然后恢复指定的satsh

- `git cherry-pick <commit>`命令可以把提交的修改"复制"到当前的分支,避免重复劳动

在哪个分支上需要修复bug,则需要再那个分支上创建临时分支,修改好临时分支后再进行合并

##### feature分支:

- `git branch -D <name>` 通过这个命令可以强行删除一个没有被合并过得分支

##### 多人协作:

- `git push origin master` 推送到master分支上,`git push origin dev`推送到dev分支上 ,如果推送失败,先用`git pull`抓取新的提交
- `git checkout -b dev origin/dev` 同时创建**origin/dev**分支
- `git pull`把最新的提交从**origin/dev**抓下来

##### Rebase:(变基)

- rebase操作可以把本地未push的分叉提交历史整理成直线
- rebase的目的是使得我们在查看历史提交的变化时更容易,因为分产的提交需要三方对比

#### 标签管理

发布一个版本时,通常现在版本库打一个标签(tag),这样可以更好的让人记住,它是更某个commit绑在一起的

##### 创建标签:

- `git tag <name>` 打一个标签

  如果忘记打标签了,在很久之前的commit上,可以找到之前的commit id,然后打上,使用`git tag <name> <commit id>`打上标签

- `git tag`  查看所有标签

- `git tag -a <tagname> -m "说明" <commit id>` 用-a指定标签名,-m指定说明文字

##### 操作标签:

- `git tag -d <tagname>` 删除打错的标签
- `git push origin <origin>` 推送某个标签到远程,`git push origin --tags` 可以一次性推送
- `git push origin :refs/tags/<tagname>` 删除一个远程标签,(先删除本地的标签)

#### 自定义git

`git config --global color.ui true`  会让命令输出更醒目

##### 忽略特殊文件:

- 忽略某些文件时,需要编写`.gitignore`文件

##### 配置别名:

偷懒方法,极力赞成

- `git config --global alias.st status`  st就表示status

  `git config --global alias.co checkout` 

  `git config --global alias.ci commit`

  `git config --global alias.br branch`

  `--global`参数是全局参数，也就是这些命令在这台电脑的所有Git仓库下都有用。

- `git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"` 丧心病狂的lg配置

- git配置文件都放在`.git/config` 中

##### 搭建git服务器:

1. 安装git:

   `sudo apt-get install git`

2. 创建一个`git`用户

   `sudo adduser git`

3. 创建证书登录

   将电脑上的`id_rsa.pub`公钥复制到`/home/git/.ssh/authorized_keys`文件中

4. 初始化git仓库

   先选定一个目录作为一个git仓库,假定是/srv/sample.git,在/srv目录输入命令:

   `sudo git init --bare sample.git1`]

   Git就会创建一个裸仓库，裸仓库没有工作区，因为服务器上的Git仓库纯粹是为了共享，所以不让用户直接登录到服务器上去改工作区，并且服务器上的Git仓库通常都以`.git`结尾。然后，把owner改为`git`：

   `sudo chown -R git:git sample.git`

5. 禁用shell登录:

   出于安全考虑，第二步创建的git用户不允许登录shell，这可以通过编辑`/etc/passwd`文件完成。找到类似下面的一行：

   ```
   git:x:1001:1001:,,,:/home/git:/bin/bash
   ```

   改为：

   ```
   git:x:1001:1001:,,,:/home/git:/usr/bin/git-shell
   ```

   这样，`git`用户可以正常通过ssh使用git，但无法登录shell，因为我们为`git`用户指定的`git-shell`每次一登录就自动退出。

6. 克隆远程仓库

   通过`git clone`命令克隆远程仓库了，在各自的电脑上运行：

   ```
   $ git clone git@server:/srv/sample.git
   Cloning into 'sample'...
   warning: You appear to have cloned an empty repository.
   ```

