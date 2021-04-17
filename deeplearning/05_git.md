## 版本控制_GIT

### 常用指令

```bash
工作区-->暂存区-->版本库
 $ git init  //通过git init命令把这个目录变成Git可以管理的仓
 $ git add readme.txt  //把文件添加到仓库
 $ git commit -m "wrote a readme file"  //git commit告诉Git，把文件提交到仓库：
 
 $ git status //掌握仓库当前的状态
 $ git diff readme.txt  //查看具体修改 ，然后Git add /git commit 进行提交
 $ git diff HEAD -- readme.txt  //工作区和版本库里面最新版本的区别
 
 
 $ git log //查看历史记录，--pretty=oneline参数，对输出数据进行简化
 $ git reset --hard HEAD^ //回退到上一个版本,也可以直接写版本号
 $ git reflog //记录你的每一次命令
 
 $ git checkout -- readme.txt //可以丢弃工作区的修改,文件回到最近一次git commit或git add时的状态
$ git rm test.txt 
$ git commit -m "remove test.txt" //版本库中删除该文件


$ git remote add origin git@github.com:michaelliao/learngit.git
git remote add <shortname> <url>  //添加远程仓库
$ git push -u origin master //本地库的所有内容推送到远程库
$ git clone git@github.com:michaelliao/gitskills.git //远程库克隆一个本地库

$ git branch dev
$ git checkout dev //创建dev分支，然后切换到dev分支
$ git branch //查看当前分支
$ git switch master //切换到master分支
$ git merge dev //git merge命令用于合并指定分支到当前分支
$ git branch -d dev  //删除dev分支

$ git merge feature1 //文件存在冲突，必须手动解决冲突后再提交
$ git status //告诉我们冲突的文件,修改后进行提交
$ git log --graph命令可以看到分支合并图

//配置用户名和密码
git config --global user.name  "username"  
git config --global user.email  "email"
git config  user.name  "username"  
git config  user.email  "email"
```

### Git 介绍

git  是一个分布式版本控制系统 ，能够实现对多个版本文件的统一管理。

![image-20201209151711401](images\image-20201209151711401.png)

**Git 管理的文件**![image-20201209151926993](images\image-20201209151926993.png)

### GIT 指令集

#### 总流程图

在线练习平台：https://learngitbranching.js.org/?locale=zh_CN

![image-20201209153107534](images\image-20201209153107534.png)

![image-20201209154520668](images\image-20201209154520668.png)

#### 创建/修改 版本库（add&commit）

```bash
git init  # 创建git 管理库
$ git config --global user.name "name"
$ git config --global user.email "email.com"  ##在git中添加用户名和用户，方便记录每个施加修改的人

touch 1.py
git add 1.py // git add .   #添加文件
git commit -m "create 1.py" #提交改变
git status  #查看版本库的状态
```

#### 记录修改 (log & diff)

```bash
git log #查看历史记录，--pretty=oneline参数，对输出数据进行简化
git diff  #unstaged 部分与commit的区别
 $ git diff readme.txt  #查看具体修改 ，然后Git add /git commit 进行提交
 $ git diff HEAD -- readme.txt # staged & unstaged 工作区和版本库区别
```

#### 回到从前 (reset & checkout)

```bash
$ git add 2.py
$ git commit --amend --no-edit   # "--no-edit": 不编辑, 直接合并到上一个 commit
$ git log --oneline    # "--oneline": 每个 commit 内容显示在一行
$ git reset --hard HEAD    
$ git reset --hard 904e1ba

$ git checkout c6762a1 -- 1.py
$ git checkout -- readme.txt //可以丢弃工作区的修改,文件回到最近一次git commit或git add时的状态
```

#### 分支（branch & merge & stash）

``` bash
$ git log --oneline --graph
$ git branch dev    # 建立 dev 分支
$ git branch        # 查看当前分支
$ git checkout dev
$ git checkout -b  dev  #创建和切换到新建的分支
$ git checkout master   # 切换至 master 才能把其他分支合并过来
$ git merge dev         # 将 dev merge 到 master 中
```

