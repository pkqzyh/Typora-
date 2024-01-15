# Git学习笔记

## Git基本介绍

### Git概述

+ Git是一个免费的开源的==分布式版本控制工具==,可以快速高效处理从小型到大型的各种项目。

+ *Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。*

+ Git容易学习，占地面积小，性能快。而且有廉价的本地库，，方便的暂存区域和多个工作流分支等特性，性能优于CVS等版本控制工具。

  

### 版本



### 版本控制管理软件基础功能

+ 保存和管理文件(会生成不同版本号，版本号会自动生成)

  ![image-20240115163738452](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115163738452.png)

+ 提供客户端工具进行访问(用户不能直接访问)![image-20240115163320016](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115163320016.png)

  > 版本控制软件主要是为了管理文件的不同版本，我们如果要恢复历史版本，我们怎么才能知道我们到底要恢复哪个文件呢，我们就得知道文件之间的差异，就需要文件比对功能

+ 提供不同版本文件的比对功能(由软件自身提供)

  ![](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115163549436.png)

   

 

### 版本库

版本库其实就是**`Git管理文件的仓库`**，通俗点说就是一个目录，不过在这个目录里面，所有的文件都在被Git管理，包括每个文件的修改和删除，都能找到对应的操作记录，对于新增的文件，要先添加到版本库中才能被Git管理起来。 

### 版本控制

+ 版本控制（Revision control）是一种在开发的过程中用于管理我们对文件、目录或工程等内容的修改历史，方便查看更改历史记录，备份以便恢复以前的版本的软件工程技术。简单来说就是用于管理多人协同开发项目的技术。

+ 简单来说，版本控制可以记录文件的修改记录，用户可以查看历史版本，进行版本切换。
+ 比如我们在做项目的时候，有时候我们对代码进行修改，可能导致原来可以运行的项目无法运行了，这个时候，如果可以回退到之前可以运行的版本就好了，通过版本控制，我们就可以达到这样的效果。

### 版本控制工具

#### 集中式版本控制工具

+ 集中式版本控制系统，版本库是集中存放在**`中央服务器`**的，比如团队协作开发项目的时候，每个人都是用自己的电脑敲代码，**但是开发人员如果想要对文件进行修改的话，他必须要把中央服务器的文件下载到本地，从中央服务器获取最新的版本，才能够开始修改其中的代码**，修改完以后，再把代码推送给中央服务器。

  ![image-20240115212547851](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115212547851.png)

+ ![image-20240115213023780](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115213023780.png)

+ 多个用户同时改写了同一个文件，导致文件内容被覆盖，也就是**`文件冲突问题`**。为了解决文件上次的冲突问题，VSS解决方法 可以通过给文件加锁，限定用户进行修改来解决。 

  + 比如用户1拿了一个文件，要进行修改，就给这个文件加锁，其他用户可以下载，但是不能修改，当用户1修改好了这个文件并上传，其他用户重新下载到本地，这时候才能进行修改文件
  + 但是这样存在缺陷，不同的用户只能串行的进行修改文件

+ CVS SVN的解决方法：一个文件的部分用来以一个用户的修改为准，比如张三，李四，王五都下载了这个文件，但是约束第一行让张三操作，第二行让李四操作，第三行让王五操作，就能够记录下这几个人对文件的修改。

+ ![image-20240115213237552](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115213237552.png)

+ 集中化的版本控制系统诸如 CVS 、SVN 等， 都有一个单一的集中管理的服务器， 保存所有文件的修订版本，而协同工作的人们都通过客户端连到这台服务器，取出最新的文件或者提交更新。
+ 每个人都可以在一定程度上看到项目中的其他人正在做些什么。管理员也可以轻松掌控每个开发者的权限， 并且管理一个集中化的版本控制系统，要远比在各个客户端上维护本地数据库来得轻松容易。
+ 集中式版本控制系统最大的毛病就是必须联网才能工作，如果服务器宕机一小时， 那么在这一小时内， 谁都无法提交更新，也就无法协同工作。

#### 分布式版本控制工具



+ 分布式版本控制系统根本没有“中央服务器”，每个人的电脑上都是一个完整的版本库，这样，你工作的时候，就不需要联网了，因为版本库就在你自己的电脑上。既然每个人电脑上都有一个完整的版本库，那多个人如何协作呢？比方说你在自己电脑上改了文件A，你的同事也在他的电脑上改了文件A，这时，你们俩之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。
+ ![image-20240115214149075](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115214149075.png)
+ 像 Git 这种分布式版本控制工具，客户端提取的不是最新版本的文件快照，而是把代码 仓库完整地镜像下来 (本地库)。这样任何一处协同工作用的文件发生故障， 事后都可以用 其他客户端的本地仓库进行恢复。因为每个客户端的每一次文件提取操作，实际上都是一次 对整个文件仓库的完整备份。
+ 每一个人在自己的本地库上做版本控制
+ 优点
  + 服务器断网的情况下也可以进行开发 (因为版本控制是在本地进行的)
  + 每个客户端保存的也都是整个完整的项目 (包含历史记录，更加安全)

> 实际使用分布式版本控制系统的时候，其实很少在两人之间的电脑上推送版本库的修改，因为可能你们俩不在一个局域网内，两台电脑互相访问不了，也可能今天你的同事病了，他的电脑压根没有开机。因此，**`分布式版本控制系统通常也有一台充当“中央服务器”的电脑`**，但这个服务器的作用仅仅是用来方便“交换”大家的修改，没有它大家也一样干活，只是交换修改不方便而已。



 #### Git工作机制

![img](https://img-blog.csdnimg.cn/img_convert/ccc966fd37ff0a2fa4a660149272384e.png)

一旦代码进入到本地库，就会生成对应的历史版本

工作区:我们写的代码存放的磁盘位置，也就是那个目录

#### Git和代码托管中心

代码托管中心是基于网络服务器的远程代码仓库， 一般我们简单称为远程库。

+ 局域网:GitLab
+ 互联网：GitHub(外网)和Gitee码云(国内网站)

## Git的下载

[Git 历史版本 for Windows_git 2.7.2下载-CSDN博客](https://blog.csdn.net/qq_21137441/article/details/120055538)

[Git - Downloads (git-scm.com) git官网](https://git-scm.com/download)

+ 根据引导界面提示安装即可,点击exe文件以后，点击next进行下一步

+ 接下来进行安装目录选择

![image-20240115215013865](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115215013865.png)

然后一直点击下一步

然后选择Git默认编辑器，Git默认的是Vim,但是这个对新手不友好，这里我选择的是vscode

![image-20240115220348142](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115220348142.png)

后面一直都是点击下一步

![image-20240115220615076](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115220615076.png)

最后点击install安装就可以了

![image-20240115220648962](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115220648962.png)

这样就安装好了

![image-20240115223934951](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115223934951.png)

接下来安装Git的客户端工具

我这里安装的是GitHub Desktop

![image-20240115221038719](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115221038719.png)

出现下面的界面说明安装成功

![image-20240115221203216](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240115221203216.png)

## Git常用命令

| 命令名称                                | 作用                   |
| --------------------------------------- | ---------------------- |
| git config --global user.name 用户名    | 设置用户签名           |
| git config --global user.email 邮箱     | 设置用户签名           |
| **==git init==**                        | **==初始化本地库==**   |
| **==git status==**                      | **==查看本地库状态==** |
| **==git add 文件名==**                  | **==添加到暂存区==**   |
| **==git commit -m "日志信息" 文件名==** | **==提交到本地库==**   |
| **==git reflog==**                      | **==查看历史记录==**   |
| **==git reset --hard 版本号==**         | **==版本穿梭==**       |

### 设置用户名称和邮箱

> + 如果是第一次应用Git，需要设置名称和邮箱，不然无法把文件纳入到版本库进行版本管理。因为多人协作的时间，不同用户可能对同一个文件操作，Git需要区分不同用户的操作，区分的方式就是名称和邮箱
> + 这里设置用户签名和将来登录 GitHub (或其他代码托管中心)的账号没有任何关系。

签名的作用是区分不同操作者身份。用户的签名信息在每一个版本的提交信息中能够看 到，以此确认本次提交是谁做的。Git 首次安装必须设置一下用户签名，否则无法提交代码。

注意： 这里设置用户签名和将来登录 GitHub  (或其他代码托管中心)的账号没有任 何关系。

```git
git config --global user.name  用户名
git config --global user.email  邮箱
```

### 初始化本地库

> Git软件主要用于管理文件的版本信息，但它只是一个软件，不可能安装后就直接将系统中所有的文件全部纳入到它的管理范畴中。并且，软件管理版本信息的主要目就是管理文件的修改和变更，如果将系统中所有文件都进行管理其实意义是不大的。所以一般情况下，**`我们需要指定某一个文件目录作为软件的管理目录。`**因为这个目录主要就作为Git软件的管理文件的版本变化信息，所以这个目录也称之为**==Git软件的版本仓库目录==**。
>
> 我们要进入到指定目录，然后执行git init,创建文件版本库

```git
git init
```

![image-20240116010413856](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116010413856.png)

版本库创建成功后，会在目录中创建.git目录，用于管理当前版本库。

![image-20240116010840676](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116010840676.png)

### 查看本地库状态

```git
git status
```

我们第一次看的时候，工作区没有任何文件

![image-20240116011151691](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116011151691.png)

我们可以新增文件

![image-20240116012016235](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116012016235.png)

![image-20240116012111913](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116012111913.png)

此时文件是红色的，说明文件只是存在于工作区，git还没有追踪过这个文件

### 添加暂存区

```git
git add 文件名
添加到暂存区以后，我们再次查看本地库状态，此时发现文件名变成绿色，是因为这个时候，我们把文件添加到了暂存区，暂存区中的文件是可以删除的
```

![image-20240116012421726](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116012421726.png)

```git
用git rm --cached 文件名就可以删除文件(删除的是暂存区的文件，工作区中的文件还在)
admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
$ git rm --cached test.txt
rm 'test.txt'

```

![image-20240116012800409](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116012800409.png)

删除暂存区的文件后，我们再次查看本地库状态

![image-20240116012855822](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116012855822.png)

### 提交本地库

```git
git commit -m "日志信息"  文件名
```

![image-20240116013317524](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116013317524.png)

``` 
再次查看本地库
git status

admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
$ git status
On branch master
nothing to commit, working tree clean      

```

>  它的意思是我们已经提交过了，并且在我们提交过以后，这个文件既没有新增也没有修改 ,工作树是干净的，我们没有什么东西需要提交

### 修改文件

当我们修改完test.txt文件以后，再次查看本地库状态

![image-20240116014147214](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116014147214.png)

然后通过git add test.txt把修改后的文件添加到暂存区，接着再次查看本地库状态

![image-20240116014339918](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116014339918.png)

接着，把文件提交到本地库

```git
git commit
```

![image-20240116014658303](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116014658303.png)

然后再次查看本地库信息

```git
admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
$ git status
On branch master
nothing to commit, working tree clean

```

查看历史版本

```git
git reflog
```

![image-20240116014809035](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116014809035.png)

当指针指向我们修改的版本时，我们就可以查看此文件

![image-20240116015012270](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116015012270.png)

### 查看历史版本信息

#### 基本语法

```git
git reflog 查看版本信息
git log    查看版本详细信息
```

![image-20240116015333305](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116015333305.png)

#### 版本穿梭

```git
git reset --hard 版本号
```

我们首先，先通过git reflog查看历史版本

![image-20240116020018538](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116020018538.png)

然后通过git reset --hard 版本号  可以重新指向某个版本

```c++
admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
$ git reset --hard 670d6b4
HEAD is now at 670d6b4 second commit
```

然后再看查看历史版本

```c++
admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
$ git reflog
670d6b4 (HEAD -> master) HEAD@{0}: reset: moving to 670d6b4
6be36c3 HEAD@{1}: commit: third commit!
670d6b4 (HEAD -> master) HEAD@{2}: commit: second commit
b7d9632 HEAD@{3}: commit (initial): first commit

```

此时，如果我们要查看文件，就会发现，看到的是第一次修改的时候的文件

```c++
admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
$ cat test.txt
hello pkq!
hello git!


这是我的第一次修改

```

## Git的分支操作

### Git分支概述



### Git分支操作

| 命令名称               | 作用                         |
| :--------------------- | ---------------------------- |
| git branch 分支名      | 创建分支                     |
| git branch -v          | 查看分支                     |
| git checkout 分支名    | 切换分支                     |
| git merge 分支名       | 把指定的分支合并到当前分支上 |
| git branch -d 分支名称 | 删除分支                     |

#### 查看分支

`git branch -v`

```git
admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
$ git branch -v
* master 670d6b4 second commit

```

#### 创建分支

`git branch 分支名`

```c
admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
$ git branch hot-fix

admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
$ git branch -v
  hot-fix 670d6b4 second commit   (刚刚创建的分支，并且把主分支master的内容复制了一份)
* master  670d6b4 second commit

```



#### 切换分支

`git checkout 分支名`

![image-20240116024005195](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116024005195.png)

![image-20240116024116294](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116024116294.png)

这个时候对文件进行修改

```tex
hello pkq!   hot-fix
hello git!

it is hot-fix   pkq  feifijekv
这是我的第一次修改
```

查看本地库状态，添加暂存区

![image-20240116024630345](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116024630345.png)

提交本地库，并且查看文件内容

![image-20240116024707173](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116024707173.png)

查看历史版本

![image-20240116024815995](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116024815995.png)

#### 合并分支

`git merge 分支名`(把指定的分支合并到当前分支上)

![image-20240116025206916](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116025206916.png)

#### 分支冲突

我们先对master中的文件进行修改

这个是修改前文件内容

```git
hello pkq!   hot-fix
hello git!

it is hot-fix   pkq  feifijekv
这是我的第一次修改
```

这个是修改后文件内容

```git
hello pkq!   hot-fix  123					
hello git!        master  test

it is hot-fix   pkq  feifijekv
这是我的第一次修改
```

然后把文件提交到本地库

紧接着切换分支到hot-fix,下面这个是修改前文件内容

~~~html
hello pkq!   hot-fix
hello git!

it is hot-fix   pkq  feifijekv
这是我的第一次修改
~~~

然后接着，我们对文件进行修改,修改后文件内容如下

```
hello pkq!   hot-fix  hot-fix test
hello git!			5136

it is hot-fix   pkq  feifijekv
这是我的第一次修改
```

然后，我们把文件上传到本地库，紧接着切换分支到master `git checkout master`

接下来进行分支合并

![image-20240116031211494](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116031211494.png)

> 这个时候，我们可以发现分支合并失败了。我们可以查看本地库状态
>
> ![image-20240116031325917](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116031325917.png)
>
> 两个分支都对这个文件进行修改，git不知道要保存哪一个，我们可以打开文件看看(这里我用vscode打开)
>
> ![image-20240116031754256](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116031754256.png)
>
> 此时，我们要删除特殊符号，然后保留我们想要留下的内容
>
> ![image-20240116032012678](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116032012678.png)
>
> 紧接着，把文件添加到暂存区`git add test.txt`
>
> 之后，把文件提交到本地库(**==此时使用git commit 命令时不能带文件名==**)
>
> ![image-20240116032404848](https://typorazyh.oss-cn-shenzhen.aliyuncs.com/picgo_imgbed/image-20240116032404848.png)
>
> 接下来查看文件内容(注意:修改的是master中的文件内容，hot-fix分支中的文件内容不会发生改变)
>
> ```
> admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
> $ cat test.txt
> hello git!        master  test
> hello pkq!   hot-fix  hot-fix test
> 
> it is hot-fix   pkq  feifijekv
> 这是我的第一次修改
> 
> ```
>
> 比如看一下hot-fix中的文件内容
>
> ```
> admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (master)
> $ git checkout hot-fix
> Switched to branch 'hot-fix'
> 
> admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (hot-fix)
> $ cat test.txt
> hello pkq!   hot-fix  hot-fix test
> hello git!                      5136
> 
> it is hot-fix   pkq  feifijekv
> 这是我的第一次修改
> admin@DESKTOP-8B1EAMP MINGW64 /d/Git-space/git-demo (hot-fix)
> 
> ```
>
> 
