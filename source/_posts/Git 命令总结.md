### Git 命令总结

推荐以玩游戏学习git的网站：https://learngitbranching.js.org/?locale=zh_CN

首先需要安装git工具，安装教程跳过

```shell
$ git
```

或者

```shell
$ git --version
git version 2.21.0 (Apple Git-122)
```

---

1. #### 创建git仓库

   ```shell
   $ git init
   Initialized empty Git repository in /***/****/**
   ```

   当前文件夹下，会多一个 .git 文件，千万不可手动修改，不然git仓库会被破坏。

2. #### git克隆

   ```shell
   $ git clone https://github.com/***/*** （git仓库地址）
   ```

   

3. #### 创建&切换分支

   ```shell
   $ git checkout -b dev(branch-name)
   Switched to a new branch 'dev'
   ```

   到这里，本地新建了一个 dev 分支，并且已经切换过去了。

   解释一下：这里 `git checkout` 命令加上`-b`参数，表示创建并切换，相当于一下两个命令：

   ```shell
   $ git branch dev
   $ git checkout dev
   Switched to branch 'dev'
   ```

   注意：刚刚git init命令执行完后，直接执行git branch (branch-name)是无效的，创建分支失败，需要先进行一次本地提交。

4. #### 本地添加，提交

   ```	shell
   $ git add .						//本地仓库添加
   $ git commit -m "first commit" // 本地提交
   $ git branch dev
   ```

5. #### 融合分支

   ```shell
   $ git merge dev(target-branch）  //将dev分支合并到当前分支
   ```

6. #### 删除分支

   ```shell
   $ git branch -d dev(branch-nme)  //删除dev分支
   ```

7. #### 查看 git log 日志

   ```shell
   $ git log		//查看log日志 进入日志后，输入q退出查看界面
   ......
   ```

8. #### 关联远程分支,然后推上去

   ```shell
   $ git remote add origin https://......git(url) 			//关联远程分支
   $ git push origin -u dev(branch-name)				//把本地dev分支推到远程仓库并且命名为dev
   
   //另一种，但是不常用
   $ git push origin -u dev:sit            //把本地dev分支推送到远程名为origin到远程仓库，并且创建远程分支为sit，该分支跟踪本地分支dev, -u 选项设置了上游关系，以后可以使用命令 git push 直接推送到该sit分支
   ```

   

