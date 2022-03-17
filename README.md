# Git-Github
练习和学习Git和Github的使用
# Git

## 1.版本控制及分类

> 什么是版本控制

版本控制(Revision control )是一种在开发的过程中用于管理我们对文件、目录或工程等内容的修改历史，方便查看更改历史记录，备份以便恢复以前的版本的软件工程技术。

- ·实现跨区域多人协同开发
- ·追踪和记载一个或者多个文件的历史记录
- ·组织和保护你的源代码和文档
- ·统计工作量
- ·并行开发、提高开发效率
- ·跟踪记录整个软件的开发过程
- ·减轻开发人员的负担，节省时间，同时降低人为错误

简单说就是用于管理多人协同开发项目的技术。

没有进行版本控制或者版本控制本身缺乏正确的流程管理，在软件开发过程中将会引入很多问题，如软件代码的一致性、软件内容的冗余、软件过程的事物性、软件开发过程中的并发性、软件源代码的安全性，以及软件的整合等问题。

> ​	版本控制的分类

**1.本地版本控制**

在本地对文件的每一个版本进行快照，如RCS

<img src="https://github.com/ysh1356542512/Git-Github/blob/master/pic/image-20220316205014889.png"  />

**2.集中版本控制**

多个开发者在同一台服务器上对文件项目的每一个版本进行快照，如SVN

<img src="https://github.com/ysh1356542512/Git-Github/blob/master/pic/image-20220316205242105.png" style="zoom:67%;" />

**3.分布式版本控制**

1和2的结合，既可以在本地对文件进行版本管理，也可以在服务器上进行版本控制，如Git

<img src="https://github.com/ysh1356542512/Git-Github/blob/master/pic/image-20220316205544016.png"  style="zoom:80%;" />

> **Git与SVN最主要区别**

SVN是集中式版本控制系统，版本库是集中放在中央服务器的，而工作的时候，用的都是自己的电脑，所以首先要从中央服务器得到最新的版本，然后工作，完成工作后，需要把自己做完的活推送到中央服务器。集中式版本控制系统是必须联网才能工作，对网络带宽要求较高。

![image-20220316210210578](https://github.com/ysh1356542512/Git-Github/blob/master/pic/image-20220316210210578.png)

Git是分布式版本控制系统，没有中央服务器，每个人的电脑就是一个完整的版本库，工作的时候不需要联网了，因为版本都在自己电脑上。协同的方法是这样的∶比如说自己在电脑上改了文件A，其他人也在电脑上改了文件A，这时，你们两之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。Git可以直接看到更新了哪些代码和文件!

Git是目前世界上最先进的分布式版本控制系统。

## 2.安装Git

[Git官网](https://git-scm.com/download/win)

**小技巧**：你在下载东西的时候可能会发现下载速度很慢，这是因为这是国外的资源且国内没有对应的CDN，这时候你可以去找相应的镜像，而淘宝镜像一般都有

[Git淘宝镜像](http://npm.taobao.org/mirrors/git-for-windows/)

## 3.Linux命令

- cd —— 改变目录
- cd.. —— 回退到上一个目录，直接cd进入默认目录
- pwd —— 显示当前所在的目录路径。
- ls(II) —— 都是列出当前目录中的所有文件，只不过IK(两个II)列出的内容更为详细。
- touch —— 新建一个文件如touch index.js 就会在当前目录下新建一个index.js文件。
- rm —— 删除一个文件, rm index.js 就会把index.js文件删除。
- mkdir —— 新建一个目录,就是新建一个文件夹。
- rm -r —— 删除一个文件夹, rm -r src删除src目录
- mv —— 移动文件, mv index.html src index.html是我们要移动的文件, src是目标文件夹.当然.这样写必须文件和文件夹在同一目录下。
- reset —— 重新初始化终端/清屏。
- clear —— 清屏
- history —— 查看命令历史
- help —— 帮助
- exit —— 退出
- #—— 表示注释

## 4.Git命令

> Git 基本命令

```
git init 
git status 
git add 
git commit 
git push 
git reset 
git rm 
git diff 
git branch 
git checkout 
git log 
git reflog 
git merge 
git rebase （-i） 
git fetch 
git stash 
git revert 
git cherry-pick
```

**命令用法**

> 在linux下参数有两种用法，甚至在很多命令行也是这样：1.双横线后面加参数的全称，2.单横线加参数的首字母

**git status **—— 查看状态

- git status 显示暂存区状态
- git status -s 精简方式显示

**git add **—— 移至暂存区

- git add . 将所有“没被忽略”的文件的修改添加到暂存区（有些文件被.gitignore过滤了）
- git add * 将所有文件的修改（不管.gitignore）都添加到暂存区

**rm **—— 删除

- rm [文件名] 是linux命令，仅仅只是删除工作区文件的命令（此时还没有add）

- git rm [文件名] 会删除暂存区或者分支上的文件，工作区的文件也会被删除（相当于rm后再git add）

- git rm --cached 是从git取消对本文件的追踪（不会删除工作区文件）。当你不想对本文件进行版本控

  制了，就用本命令

**git commit **—— 提交

- git commit -m "[提交描述]" 直接提交信息

- git commit -s 会弹出一个vim编辑器（linux的一个文本编辑器），按i进入insert插入模式，输入一些

  commit文本后按Esc进入一般模式（vim编辑器的一种模式），按“:”键输入命令“wq”按回车会自动保存

  后退出，如果输入“q”表示不保存退出。这个git commit命令实际上和git commit -m 命令是等效的。

- git commit -a -m "[提交描述]"相当于执行git commit -m前先执行git add .

**git branch **—— 分支

- git branch [名称]新建一个分支

- git branch -r 列出远程分支

- git branch 列出本地分支，并且在当前分支前面加*号

- git branch -a 列出所有分支包括本地远程

- git branch -d [名称] 删除本地分支

- git branch -d -r [名称] 删除远程分支

- git branch -m [旧名称] [新名称] 分支重命名

- git branch -vv 查看本地仓库和远程仓库的对应关系

- git branch --set-upstream-to=[远程分支名] [本地分支名]这样设置本地和远程分支的对应关系（因为本

  地分支可能是你起的别名，没必要和远程分支同名）

**git checkout** —— 切换分支

- git checkout -b [名称]新建一个分支并切换到该分支上

- git checkout [名称]切换分支

- git checkout -q [名称]无提示切换分支

- git checkout -f [名称]强制切换（如果工作区有修改，则丢弃本次修改，强制切换到分支）

- git checkout [某次版本的hash码]这样是没有意义的（一般HEAD指针指向的是分支名），仅仅可以通

  过这个方法去看“那次版本的文件的内容”，但是不推荐在这里commit（这算是在游离的分支）

- git checkout -b [新建分支名] [要对映的远程分支] 一个快捷的用法，可以快速建立映射。本地如果直接

  创建一个分支，则是在当前分支上分离出一个分支（内容和原分支相同）

**git log **—— 查看日志和变化

- git log 显示所有分支的提交历史记录（把所有分支的提交汇总了），如果一个屏幕显示不下，可以按回

  车浏览下部，按q退出浏览

- git log -p 会显示每次提交的差异细节（常用，方便）

- git log --stat 显示每次提交的统计信息（行数变化，修改过哪些文件）

- git log --oneline --graph [你要比较的n个分支] 这几个参数组合有妙用：oneline表示单行显示，graph

  表示显示左方的图形化。这样就能看到详细的提交信息了

**git diff **—— 查看工作区和暂存区的区别，即add前后

- git diff [文件名] 显示工作区和暂存区文件的差异，如果没有add过（暂存区没有它），则对比的是最近

  一次版本和工作区的差异。

- git diff [分支名] [文件名] 对比工作区的文件和分支的文件的差别

- git diff --cached [文件名] 对比暂存区和git仓库的区别（就是暂存区和最近一次commit的差异）

- git diff [哈希码] [文件名] 对比工作区和git仓库中某次提交的区别

- git diff --cached [哈希码] [文件名] 对比暂存区和git仓库中某次提交的区别

- git diff [哈希码] [哈希码] 对比任意两次提交（可以来自不同分支呀，因为每次提交都有唯一的哈希码）

  

  上述diff命令可以不指定文件名，则对全部文件操作。

  上述哈希吗可以换成相对引用（“HEAD^^”或者“HEAD~2”这样的）

**git reset**

- git reset --hard [哈希码] 强制回退到某次commit（工作区会恢复为和那次commit一样的状态，暂存区

  会清空）

- git reset --soft [哈希吗] 软回退到某次commit（工作区和暂存区内容保留不动，实际上是分支指针的移

  动）

reset和checkout的区别：git checkout [哈希吗]只是将本地文件恢复到那次commit的状态，这是

HEAD指针指向的不是分支而是某一个commit，是不能再提交的（提交没有意义），但是reset是

“HEAD所在的分支”的头指针回退到历史commit上，是可以提交的，相当于回溯。checkout [哈希码] 的

作用只是浏览。

**git revert** [哈希码] 新增一个commit，内容是抵消之前的修改（等价于回退，但是与reset不同的是，

reset会真的删除一些commit，而revert会保留之前的任何commit，新增一个commit）

**git reflog** 可以理解为显示本地操作记录

**git remote**

- git remote 查看现有的仓库有哪些（一般只有一个origin仓库，这是默认的名称）

- git remote -v 可以查看仓库的地址

**git push**

- git push [远程主机名/仓库名] [本地分支名]:[远程分支名] 会将某个分支推送到远程分支上

  如：git push origin master这里省略了远程分支名，表示将本地的master分支推送到origin仓库。

  如：git push origin :master这里省略的本地分支名，是删除远程分支master的命令，等价于：git

  push origin --delete master

- git push [远程主机名/仓库名]表示将当前分支推送到[远程主机名]的对应分支。

- git push如果只有一个主机则[远程主机名]可以省略，如果有多个远程主机，则需要git push -u origin

  master先上传一次，这样会将本地的master分支推送到origin主机，同时指定origin为默认主机，后面

  就可以不加任何参数使用git push了。这里的-u就是--set-upstream

- git push [origin 分支名] 会上传本地的分支到服务器。

**git merge**

- 参数--commit（默认）自动生成一个提交，包含两个节点合并的结果。

- 参数--no-commit为了防止合并失败，先不提交，让用户手动提交

将当前分支向[分支名]合并，并生成一个合并后的commit

如果有冲突则要先fix conflicts，git会列出冲突的文件，我们需要打开这些文件一个一个地合并（git自

动帮我们合并了全部，我们只用删掉不需要的部分即可），然后重新commit就行了（这时不用再

merge了）

**git rebase**

rebase和merge的区别：rebase是将你当前的修改作为[分支名]之后的修改（正如其名：在..基础上）

然后不产生提交，而merge是产生了一个新的提交

**git stash**

- git stash 等同于git stash save，能够将所有未提交的修改（工作区和暂存区）快照至堆栈中，用于后续恢复当前工作目录。
- git stash list 查看当前stash中的内容
- git stash pop 将当前stash中的内容弹出，并应用到当前分支对应的工作目录上。相当于回退
- git stash apply [stash名字] 将堆栈中的内容应用到当前目录如：git stash apply stash@{1}
- git stash drop [stash名字]
- git stash clear 清空stash列表
- git stash show 查看堆栈中最新保存的stash和当前目录的差异



