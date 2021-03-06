#### 一、基本操作01

**1、git init**

初始化，使用后目录添加.git文件，用来管理当前目录下的文件。

**2、git status**

查看git仓库的状态

Git对文件划分状态：

​	工作区：存放新增和修改的文件

​	暂存区：存放下次要提交的文件清单

​	git仓库：存放已提交的文件

**3、git add files**

将工作区里新修改的文件标记一下track,然后生成快照，记录下来，放到暂存区中。并不是直接提交到Git仓库中

​	工作区——>暂存区

**4、git commit -m ["提交说明"]**

将暂存区中的文件(暂存区中的文件消失）提交到Git仓库中

​	暂存区——>Git仓库

#### 二、基本操作02

**1、git help/git help [命令]**

查看命令的用法或作用

**2、git log**

查看项目的历史提交记录

**3、git log -[数字]**

仅查看最近几条提交记录

**4、git commit --amend**

(1)可以修改最近一次的提交说明

(2)可以将新的文件与最近的一次提交当作统一提交（如当你少提交了一个文件时，可以先将少提交的文件git add,然后使用git commit --amend命令，达到统一提交的目的）

**5、git add .**

将新的工作区文件全部添加到暂存区中

**6、git reset HEAD [文件名]**

将暂存区的某个文件移除

**7、git reset --soft HEAD~**

撤销最近一次commit操作，相应的文件重回暂存区

**7.1、git reset --soft [版本号]**

撤销该版本之前的所有commit操作，相应文件重回暂存区

**8、git reset --hard HEAD~**

撤销最近一次add和commit操作，并且对文件的修改也会消失（直接回退到上一个版本）

**8.1、git reset --hard [版本号]**

跳到到指定版本（可以是之前的版本，也可以是之后的版本，实质上是HEAD指针的移动），版本号可通过git log查看

#### 三、Git分支概念

HEAD总是指向最近一次commit的文件，当你再次进行提交时，HEAD指向这次提交的文件，而这次提交的文件指向前一次提交的文件。

#### 四、Git分支的创建、切换、状态

**1、git branch**

展示所有的分支，当前所在分支前有*

**2、git branch [新分支名称]**

创建一个新的分支，该分支指向最后一个commit的对象，但HEAD的指向不变

**3、git checkout [分支名称]**

切换分支，即改变HEAD指向的分支

#### 五、分支的合并

master分支为主分支，一般不用来开发，主要用来合并其他分支
分支的创建与所在目录无关

**1、git checkout -b [新分支名称]**

直接创建一个新的分支，并切换到这个分支，相当于：

​	git branch [新分支名称]

​	git checkout [新分支名称]

**2、git merge [分支名称]**

将主分支合并到该分支上

**3、git branch -d [分支名称]**

删除这个分支

（总结）合并分支的过程：

​	1、切换回master分支上 	git checkout master

​	2、合并master分支与要合并的分支	git merge [次分支名称]

​	3、删除要合并的次要分支	git branch -d [次要分支名称]

#### 六、Git分支的暂存

&emsp;当我们在一个分支修改文件时，如果修改后未提交，则我们无法切换到其他分支，为解决这个问题，使用Git中文件暂存的命令

**1、git stash**

可以使修改后未提交的文件，暂时“隐藏”起来，使得我们可以在此时切换分支

**2、git stash apply**

可以使最近一次暂存的文件复原，得以继续进行工作

**3、git stash apply [暂存编号]**

可以使制定的暂存文件复原

**4、git stash list**

将所有暂存的文件列出来，可以看到它们的暂存编号

#### 七、解决Git分支合并冲突

&emsp;当次要分支同时对同一个文件进行修改后，在合并过程中会出现冲突

解决方法如下：

​	打开有冲突的文件，选择要保留的内容，即可解决冲突。