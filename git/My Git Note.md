# 1、本地项目上传到空的远程仓库

1. 克隆下来项目，删除.git文件

2. 在本文件夹下初始化项目：git init，会生成.git文件

3. 绑定远程仓库地址

   ~~~bash
   git remote add origin https://gitee.com/gu097/my-test.git
   ~~~

4. 先把项目上传到本地仓库

   ~~~bash
   git add .
   git commit -m "hell"
   ~~~

5. 如果远程的readme文件不在本地中会报错，所以需要解决：

   ~~~bash
   ! [rejected]        master -> master (fetch first)
   error: failed to push some refs to 'ssh://git@g.hz.netease.com:22222/XXXXX/fastmonkey.git'
   hint: Updates were rejected because the remote contains work that you do
   hint: not have locally. This is usually caused by another repository pushing
   hint: to the same ref. You may want to first integrate the remote changes
   hint: (e.g., 'git pull ...') before pushing again.
   hint: See the 'Note about fast-forwards' in 'git push --help' for details.
   
   #解决方法
   git pull --rebase origin master
   git push origin master
   ~~~

6. 否则就按正常命令：

   ~~~bash
   git push --set-upstream origin master
   ~~~

   

# 2、关于版本控制与暂存区

## 暂存区作用理解

git中使用`git add [] `将文件添加到暂存区。

在本地中，我们将代码托管到本地库中（`.git 文件夹`）

我们修改项目文件，当我们觉得这个版本的开发结束后，或者这个版本的文件需要保存，那么使用`git add `将文件放到暂存区里面，那么就可以将此刻的文件暂时保存起来，以后如果再次修改文件，也不会影响暂存区内的文件。

暂存区内的文件可以删除：`git rm --cached [file]`

放在暂存区内的时候也可以使用`git commit`将暂存区内的所有文件提交，提交后就会形成一个版本。



## 查看日志

可以通过`git reflog`**查看历史版本提交记录。**

通过`git log`查看详细日志。



## 版本穿梭

那么如何返回历史版本呢？使用`git reset --hard [版本号]`返回历史版本。

这个时候，head指针就会指向旧版本文件。

这个是如何做到的：文件.git/Head里的内容就是当前指向的分支，然后.git/refs/heads/master文件就是当前指向的版本号。



# 3、设置远程地址起别名

起别名： git remote add 别名 远程地址

查看别名：git remote -v





