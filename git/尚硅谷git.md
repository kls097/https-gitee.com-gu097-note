[toc]





# 1、Git

## 1.1、概述

- Git是一个免费的、开源的分布式版本控制系统 ，可以快速高效地处理从小型到大型的各种项目
- Git易于学习，占地面积小，性能 极快 。 它具有廉价的本地 库 ，方便的暂存区域和多个工作
   流分支等特性。 其性能优于 Subversion、 CVS、 Perforce和 ClearCase等 版本控制 工具。
- 官网地址：http://git-scm.com/

## 1.2、版本控制

- 版本控制是一种记录文件内容变化，以便将来查阅特定版本修订情况的系统。
- 版本控制其实最重要的是可以记录文件修改历史记录，从而让用户能够查看历史版本，方便版本切换

## 1.3、版本控制工具

- 集中式版本控制工具   
  - CVS、SVN、VSS
  - 集中化的版本控制系统诸如 CVS、SVN 等，都有一个单一的集中管理的服务器，保存所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新。多年以来，这已成为版本控制系统的标准做法。
  - 这种做法带来了许多好处，每个人都可以在一定程度上看到项目中的其他人正在做些什么。而管理员也可以轻松掌控每个开发者的权限，并且管理一个集中化的版本控制系统，要远比在各个客户端上维护本地数据库来得轻松容易。
  - 事分两面，有好有坏。这么做显而易见的缺点是中央服务器的单点故障。如果服务器宕机一小时，那么在这一小时内，谁都无法提交更新，也就无法协同工作。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251417757.png)

- 分布式版本控制工具
  - Git、Mercurial、…
  - 像Git这种分布式版本控制工具 ，客户端提取的不  最新版本的文件快照，而是把代码仓库完整地镜像下来 (本地库) 。这 样 任何一处协同工作用的文件发生故障，事后都可以用其他客户端的本地仓库进行  恢复。因为每个客户端的每一次文件提取操作，实际上都是一次对整个文件仓库的完整备份 。
- 分布式的版本控制系统出现之后,解决了集中式版本控制系统的缺陷 :
  - 服务器断网的情况下也可以进行开发，因为版本控制是在本地进行的
  - 每个客户端保存的也都是整个完整的项目 ，包含历史记录 更加安全

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251418498.png)

## 1.4、Git简史

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251417030.png)

## 1.5、Git工作机制

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251417951.png)

## 1.6、Git和代码托管中心

代码托管中心是基于网络服务器的远程代码仓库，一般我们简单称为远程库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251417761.png)

# 2、Git安装

- 官网地址：http://git-scm.com/

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251419377.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421350.png)

最好安装在自己电脑开发或者环境目录下

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251422495.png)

Git安装目录名，不用修改，直接点击下一步。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251422305.png)

Git的默认编辑器，建议使用默认的 Vim编辑器，然后点击下一步。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251422600.png)

默认分支名设置，选择让Git决定，分支名默认为 master，下一步。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251422795.png)

修改Git的环境变量，选第一个，不修改环境变量，只在 Git Bash里使用 Git。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251422313.png)

选择后台客户端连接协议，选默认值OpenSSL，然后下一步。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251423649.png)

配置Git文件的行末换行符， Windows使用 CRLF Linux使用 LF，选择第一个自动转换，然后继续下一步。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251424161.png)

选择Git终端类型，选择默认的 Git Bash终端，然后继续下一步。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251424141.png)

选择Git pull合并的模式，选择默认，然后下一步。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251424887.png)

选择Git的凭据管理器，选择默认 的跨平台的凭据管理器 ，然后下一步 。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251424960.png)

其他配置，选择默认设置，然后下一步。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251424345.png)

实验室功能，技术还不成熟， 有已知的 bug，不要勾选，然后点击右下角的 Install按钮，开始安装 Git

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251425432.png)

点击Finsh按钮， Git安装成功！

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251425918.png)

右键任意位置，在右键菜单里选择Git Bash Here即可打开 Git Bash命令行终端。在Git Bash终端里输入 `git --version`查看 git版本，如图所示，说明 Git安装成功。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251425894.png)

# 3、Git常用命令

| 命令名称                             | 作用               |
| ------------------------------------ | ------------------ |
| git config --global user.name 用户名 | 设置用户签名       |
| git config --global user.email 邮箱  | 设置用户签名       |
| **git init**                         | **初始化本地库**   |
| **git status**                       | **查看本地库状态** |
| **git add 文件名**                   | **添加到暂存区**   |
| **git commit m " 日志信息 " 文件名** | **提交到本地库**   |
| **git reflog**                       | **查看历史记录**   |
| **git reset hard 版本号**            | **版本穿梭**       |

## 3.1、设置用户签名

基本语法

- `git config --global user.name` 用户名
- `git config --global user.email` 邮箱

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251425119.png)

并且在自己 `C:\Users\Augenestern` 下有个 `.gitconfig` 文件，打开里面就是我们设置的用户签名

说明：

签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看到，以此确认本次提交是谁做的。Git首次安装必须设置一下用户签名，否则无法提交代码。

注意：这里设置用户签名和将来登录 GitHub（或其他代码托管中心）的账号没有任何关系。

## 3.2、初始化本地库

基本语法：`git init`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251425915.png)

## 3.3、查看本地库状态

基本语法：`git status`

- 首次查看，工作区没有任何文件

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251425697.png)

### 3.3.1、新增文件

语法：`vim hello.txt` ,然后按 i 键进入 INSERT，要想复制粘贴 ，需要先按 esc 键，之后 `yy` 复制，`p` 粘贴

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251426747.png)

文件内容输入完毕，需要先按`:`,输入`wq`，然后才算完成新增文件，再次查看

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251426750.png)

## 3.4、添加暂存区

### 3.4.1、将工作区的文件添加到暂存区

基本语法：`git add 文件名`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251426657.png)

## 3.5、提交本地库

### 3.5.1、将工作区的文件提交到本地库

基本语法：`git commit -m "日志信息" 文件名`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251426169.png)

## 3.6、修改文件

语法：`vim 文件名`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251426538.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251427462.png)

## 3.7、历史版本

### 3.7.1、查看历史版本

基本语法：

- `git reflog` 查看版本信息
- `git log` 查看版本详细信息

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251436308.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251418089.png)

但是我们工作区的 hello.txt 始终只有一个文件存在

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251418452.png)

### 3.7.2、版本穿梭

语法：`git reset --hard 版本号`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251418509.png)

## 3.8、切换版本原理

Git 切换版本，底层其实是移动的HEAD 指针，具体原理如下图所示

HEAD 指针指向 master 分支，master分支指向 first 版本，

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251418740.png)

之后有了 second 版本，master 指针指向 second 版本

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251418983.png)

之后有了third 版本，master 指针指向 third 版本

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251418898.png)

如果我们想穿越回去，只需要让 master 指针指向 first 版本或者 second 版本





# 4、Git分支

## 1.1、什么是分支

- 在版本控制过程中，同时推进多个任务，为每个任务，我们就可以创建每个任务的单独分支
- 使用分支意味着程序员可以把自己的工作从开发主线上分离开来，开发自己分支的时候，不会影响主线分支的运行
- 对于初学者而言，分支可以简单理解为副本，一个分支就是一个单独的副本

## 1.2、分支的好处

- 同时并行推进多个功能开发，提高开发效率。
- 各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可。

## 1.3、分支的操作

| 命令名称            | 作用                         |
| ------------------- | ---------------------------- |
| git branch 分支名   | 创建分支                     |
| git branch -v       | 查看分支                     |
| git checkout 分支名 | 切换分支                     |
| git merge 分支名    | 把指定的分支合并到当前分支上 |

### 1.3.1、查看分支

基本语法：`git branch -v`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251420744.png)

### 1.3.2、创建分支

基本语法：`git branch 分支名`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251420549.png)

### 1.3.3、切换分支

基本语法:`git checkout 分支名`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251420690.png)

### 1.3.4、修改分支

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251420201.png)

### 1.3.5、合并分支

基本语法：`git merge 分支名`

#### ①正常合并不冲突

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251427077.png)

#### ②合并产生冲突

冲突产生的原因：

- 合并分支时，两个分支在同一个文件的同一个位置有两套完全不同的修改。
- 有两套完全不同的修改。 Git无法替我们决定使用哪一个。必须 人为决定新代码内容。

例如，我们首先在 master 分支的倒数第二行进行修改，并将其添加到暂存区，再提交到本地库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251427489.png)

接着，我们去 hot-fix 分支的倒数第一行进行修改，并将其添加到暂存区，再提交到本地库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421814.png)

之后我们在 master 分支上合并 hot-fix 分支，发现产生冲突

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421476.png)

> 解决冲突

1. 编辑有冲突的文件，删除特殊符号，决定要使用的内容

   特殊符号：`<<<<<< HEAD` 当前分支的代码 `=======` 合并过来的代码 `>>>>>>>hot-fix`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421287.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421574.png)

删除完成之后保存，再次添加到暂存区，并再次提交到本地库(注意：此时使用 git commit 命令时候不能带文件名)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421618.png)4# 2、Git团队协作机制

## 2.1、团队内协作

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421836.png)

举个例子：岳不群首先用 git 初始化自己的本地库，写了一套华山剑法，利用
 push 命令将自己的本地库推送到代码托管中心(Github、Gitee)，大弟子令狐
 冲通过 clone 克隆命令完整的复制到自己的本地库，令狐冲修改两招之后将
 自己的本地库再次 push 到代码托管中心，这样岳不群就可以通过 pull 命令
 拉取令狐冲修改的代码 来更新自己的本地库。

## 2.2、跨团队协作

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421095.png)

令狐冲请东方不败改代码，东方不败通过 fork 命令从岳不群的的远程库中拿取代码，再通过 clone  克隆命令到自己的本地库，修改完成后使用 push 推送到在自己的远程库，使用 Pull request 拉取请求给岳不群，岳不群审核完成后使用  merge 命令合并对方的代码到自己的远程库中，再通过 pull 命令到自己的本地库中，这样修改过后的华山剑法岳不群和令狐冲就都可以使用了。

# 5、Github

## 3.1、创建远程仓库

### 3.1.1、Github远程仓库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421730.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421969.png)

### 3.1.2、Gitee远程仓库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421931.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251430775.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421648.png)

## 3.2、远程仓库操作

| 命令名称                               | 作用                                                         |
| -------------------------------------- | ------------------------------------------------------------ |
| git remote -v                          | 查看当前所有远程地址别名                                     |
| git remote add 别名 远程地址           | 起别名                                                       |
| **git push 别名 分支**                 | **推送本地分支上的内容克隆到本地**                           |
| **git clone 远程地址**                 | **将远程仓库的内容克隆到本地**                               |
| **git pull 远程库地址别名 远程分支名** | **将远程仓库对于分支最新内容拉下来后与当前本地分支直接合并** |

### 3.2.1、创建远程仓库别名

#### ①、Gihub

基本语法：

- `git remote -v` 查看当前所有远程地址别名
- `git remote add 别名 远程地址` 起别名

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421752.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421222.png)

注意：起的别名最好和本地库的名称一致

#### ②、Gitee

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421271.png)

### 3.2.2、推送本地分支到远程仓库

基本语法：`git push 别名 分支`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421227.png)

我们输入 gitee 的用户名和密码，会提示推送成功，我们在 gitee 上查看我们的 git-demo 仓库，发现有我们推送的hello.txt 文件

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251428222.png)

### 3.2.3、拉取远程库分支到本地库

语法：`git pull 别名 分支`

我们在远程库进行 hello.txt 的文件修改

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251428501.png)

然后在本地库将远程库的代码 拉取

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421617.png)

### 3.2.3、克隆远程仓库到本地

基本语法：`git clone 远程地址`

我们另一台用户需要克隆我们的远程仓库到他的本地库，由于是使用一台电脑模拟，所以在克隆之前需要在 凭据管理器下删除我们之前的 gitee 凭据

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421916.png)

我们新建一个文件夹 git-clone，然后在此文件夹下右键 git bash here，之后进行克隆

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251428963.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421910.png)

## 3.3、邀请加入团队

### 3.3.1、Gitee

我们在 git-clone(假设这是大弟子令狐冲) 文件夹里面进行代码修改，修改完后添加到暂存区，再提交到本地库，之后 push 到我们的远程库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421080.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251428570.png)

我们在 git-demo 仓库点击管理 -> 仓库成员管理 -> 添加仓库成员 -> 邀请用户

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421774.png)

我们在第二哥 gitee 账号里面可以接收到如下图：

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421507.png)

令狐成成为仓库开发者被拉入团队后，我们再次在令狐冲文件夹使用进行 push

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251429893.png)

push 到远程库成功，我们在远程库查看

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421555.png)

### 3.3.2、Github

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421589.png)

填入想要合作的人

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251429268.png)

复制地址并发给该用户

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251431813.png)

在 atguigulinghuchong这个账号 中的 地址 栏 复制 收到邀请 的 链接 ，点击接受邀请。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421909.png)

## 3.4、跨团队协作

### 3.4.1、Gitee

将远程仓库的地址复制发给邀请跨团队协作的人，比如东方不败。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421297.png)

在东方不败的 Gitee账号里的地址栏复制收到的链接，然后点击 Fork将项目叉到自己的本地仓库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421645.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421838.png)

接下来点击上方的 Pull Requests 请求，并创建一个新的请求 。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421827.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251436683.png)

合并之后我们在岳不群的 git-demo 下就可以看到东方不败的代码

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421879.png)

### 3.4.2、Github

将远程仓库的地址复制发给邀请跨团队协作的人，比如东方不败。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421149.png)

在东方不败的 GitHub账号里的地址栏复制收到的链接，然后点击 Fork将项目叉到自己的本地仓库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421611.png)

东方不败就可以在线编辑叉取过来的文件。编辑完毕后，填写描述信息并点击左下角绿色按钮提交。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421914.png)

## 3.5、SSH免密登录

### 3.5.1、Gitee

在 C盘 User 自己的账户下右键 git bash here，`ssh-keygen -t rsa -C 自己的邮箱签名`

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421547.png)

这样就会生成 .ssh 文件夹，里面有私钥和公钥

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251432025.png)

之后在 gitee 上添加公钥

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421918.png)

这样我们可以借助 ssh 链接来拉取和推送代码，并且不需要进行登录

### 3.5.2、Github

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421843.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251421546.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251432509.png)





# 7、IDEA集成Git

## 7.1、配置Git忽略文

我们的Eclipse 、IDEA都会生成一些无关文件，如图

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433260.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433958.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251437480.png)

我们之所以要忽略他们，是因为他们与项目的实际功能无关，不参与服务器上部署运行。如何忽略他们？

1. 在用户家(C/User/用户名) 下创建 `git.ignore`

```bash
# Compiled class file
*.class

# Log file
*.log

# BlueJ files
*.ctxt

# Mobile Tools for Java (
.mtj.

# Package Files
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar

# virtual machine crash logs, see
http://www.java.com/en/download/help/error_hotspot.xml
hs_err_pid*

.classpath
.project
.settings
target
.idea
*.iml
```

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251437058.png)

1. 在 .gitconfig 文件中引用忽略配置文件(.gitconfig 在家目录中)

```
[user]
	name = Augenestern
	email = .....@qq.com
[core]
	excludesfile = C:/Users/Augenestern/git.ignore
```

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251437529.png)

1. 在 IDEA 里面定位

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433219.png)

## 7.2、IDEA初始化本地库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433648.png)

默认创建的 git 仓库就是我们打开的项目所在的目录，我们添加了 git 仓库之后

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433180.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433897.png)

添加到暂存区就变为了绿色，我们可以写些代码，然后将 project 添加到暂存区

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433862.png)

我们添加到暂存区，再接着进行提交到本地库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433796.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433885.png)

## 7.3、切换版本

我们修改 GitTest 中的代码，再次提交到本地库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433301.png)

在IDEA的左下角，点击 Git，然后点击 Log查看版本，右键选择要切换的版本，然后在菜单里点击 Checkout Revision

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433780.png)

## 7.4、创建分支

右键项目 -> Git -> Branches

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251437043.png)

在弹出的Git Branches框里 点击 New Branch按钮。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251438268.png)

填写分支名称

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251443523.png)

然后再 IDEA的右下角看到 hot-fix，说明分支创建成功，并且当前已经切换成 hot-fix分
 支

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251438101.png)

## 7.5、切换分支

在IDEA窗口的右下角，切换到 master分支 。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433902.png)

## 7.6、合并分支

在IDEA窗口的右下角，将 hot-fix分支合并到当前 master分支。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433302.png)

如果代码没有冲突，分支直接合并成功，分支合并成功以后，代码自动提交，无需手动提交本地库

## 7.7、合并分支冲突

如图所示，如果master分支和 hot-fix分支都修改了代码，在合并分支的时候就会发生冲突。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433090.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251438744.png)

我们现在站在master分支上合并 hot-fix分支，就会发生代码冲突。

点击 Conflicts框里的 Merge按钮，进行手动合并代码。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433428.png)

手动合并完代码以后，点击右下角的 Apply按钮。代码冲突解决，自动提交本地库。

# 8、IDEA集成Github

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433840.png)

Token在哪呢？我们在 Github 点击 Settings -> Develop Settings

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251439797.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251439717.png)

点击 Generate token

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251433095.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434733.png)

## 8.1、分享项目到Github

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434811.png)

这其实就是创建远程库，名字，是否私有，描述等

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434625.png)

## 8.2、push推送本地库到远程库

右键点击项目，可以将当前分支的内容 push 到 GitHub的远程仓库中 。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251440601.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434641.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434250.png)

## 8.3、pull拉取远程库到本地库

注意：push是将本地库代码推送到远程库，如果本地库代码跟远程库代码版本不一致，push的操作是会被拒绝的。也就是说， 要想  push成功，一定要保证本地 库的版本要比远程库的版本高！  因此一个成熟的程序员在动手改本地代码之前，一定会先检查下远程库跟本地代码的区别！如果本地的代码版本已经落后，切记要先  pull拉取一下远程库的代码，将本地代码更新到最新以后，然后再修改，提交，推送！

- 右键点击项目，可以将远程仓库的内容pull到本地仓库 。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251440887.png)

注意：pull是拉取远端仓库代码到本地，如果远程库代码和本地库代码不一致，会自动合并，如果自动合并失败，还会涉及到手动解决冲突的问题。

## 8.4、clone克隆远程库到本地库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434019.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251444869.png)

# 9、IDEA集成Gitee

## 9.1、IDEA安装码云插件

Idea 默认不带码云插件，我们第一步要安装 Gitee插件。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251444354.png)

安装完成重启 IDEA 即可

Idea连接码云和连接 GitHub几乎一样，首先在 Idea里面创建一个工程，初始化 git工程，然后将代码添加到暂存区，提交到本地库。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251444786.png)

## 9.2、分享项目到Gitee

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251444021.png)

## 9.2、push推送到码云远程库

当然我们也可以自己在码云Gitee上创建远程库，然后获取到远程库的 HTTPS/SSH 链接，将我们的代码 push 即可

自定义远程库链接： Define remote，给远程库链接定义个 name，然后再 URL里面填入码云远程库的 HTTPS链接即可，码云服务器在国内，用 HTTPS 链接即可，没必要用 SSH 免密链接

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434857.png)

## 9.3、pull拉取远程库到本地库

我们在远程库修改代码，然后使用本地库 pull 拉取远程库的代码

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434107.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434878.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434095.png)

## 9.4、clone克隆远程库到本地库

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434969.png)

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251434954.png)

# 10、码云复制Github项目

码云提供了直接复制 GitHub 项目的功能，方便我们做项目的迁移和下载 。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251435203.png)

将 GitHub的远程库 HTTPS链接复制过来，点击创建按钮即可。

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251435667.png)

如果GitHub项目更新了以后，在码云项目端可以手动重新同步，进行更新！

![在这里插入图片描述](https://gitee.com/gu097/note/raw/master/img/202110251435933.png)