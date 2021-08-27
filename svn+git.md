> 💥此MD/PDF/HTML文档由 [@竹梦者也 ](https://www.zjgsuzjx.top/)编辑制作，不可贩卖❌。仅供学习交流使用，下载后切勿随意传播。转载麻烦加上出处~
>
> 📌欢迎在留言区提供修改建议~
>
> 💌本文内容和代码来自于`tianyu`老师的`svn&git`教程
>
> 
>
> ✅2021.7.15	 @竹梦者也(https://www.zjgsuzjx.top) 
>









## 一、版本控制器

为什么需要版本控制器：

> 备份还原、协同修改、权限控制。

**版本控制**是一种记录若干文件内容变化，以便将来查阅特定版本修订情况的系统。

目前主流的版本控制器有两种：`SVN`和`GIT`，后者最强大。

### 一、SVN

#### 1. 概述

`SVN` [subversion]，就是一款实现集中式的版本控制工具软件，通常也称为版本控制器。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/13/15f68d3765374579225fbfb89f15862d.png" alt="15f68d3765374579225fbfb89f15862d.png" border="0" />

> **补充**：bug平台是程序员提交代码测试的地方，会由专门的测试工程师来测试代码，每天上线要及时修bug。常见的平台：禅道。

#### 2. 安装

安装服务端（演示需要）：VisualSVN-Server

https://www.visualsvn.com/downloads/

安装客户端：TortoiseSVN

https://tortoisesvn.net/downloads.zh.html

#### 3. 使用

**服务端**：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/13/58669e32c37bf1996b74836820b94fc9.png" alt="58669e32c37bf1996b74836820b94fc9.png" border="0" width="60%"/>

新建定时备份任务需要`licensing`：

在https://www.visualsvn.com/server/licensing/evaluation/可以免费领取45天的。

> **补充**：备份可以分为本地备份和异地容灾备份。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/c01c331a8e7ed320f863aba50810d550.png" alt="c01c331a8e7ed320f863aba50810d550.png" border="0" width="60%"/>

**仓库地址**：一般格式是https://DESKTOP-XXXXXX/svn/test1/，这个主域名部分是本地电脑的设备名称，可以修改为IP地址以供其它处于统一局域网下的设备访问。查看IP地址方法：在`cmd`里输入`ipconfig`

MAC地址：是指网卡的唯一标识信息。

##### # 仓库检出

右键桌面->SVN checkout

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/c25d066e46bddaa124d53caf4369a76a.png" alt="c25d066e46bddaa124d53caf4369a76a.png" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/3df314c3348f95e9d03034a9579c1720.png" alt="3df314c3348f95e9d03034a9579c1720.png" border="0" />

出现以下图标则表示成功建立本地仓库了。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/1d4c0703c76d2faa47e49aac1c18d4c5.png" alt="1d4c0703c76d2faa47e49aac1c18d4c5.png" border="0" />

如果出现了但是没有绿色的对号，则需要刷新资源管理器。win10操作如下，win7是explorer.exe。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/5a38b7d2a99bd0651aa7e340d892fb97.png" alt="5a38b7d2a99bd0651aa7e340d892fb97.png" border="0" width="60%"/>

SVN版本文件的常用状态：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/efcbc562f88b6b364cfe08f4db592849.png" alt="efcbc562f88b6b364cfe08f4db592849.png" border="0" />

##### # 上传文件

右键有`.svn`的文件夹（如果没有显示，点击上方“查看”->“显示隐藏文件夹”）->`SVN Commit`

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/0090a0abecbc3e19603bd0802e6bdfdf.png" alt="0090a0abecbc3e19603bd0802e6bdfdf.png" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/b86c0396a4b14702a29d48994fbe49a9.png" alt="b86c0396a4b14702a29d48994fbe49a9.png" border="0" />

> 提交后的文件会显示绿色对号，偶尔会不显示，无关紧要。

最后可以在服务器端查看是否提交成功。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/974084cdc778426a7615c3ea46bfd32d.png" alt="974084cdc778426a7615c3ea46bfd32d.png" border="0" />

##### # 更新文件

右键有`.svn`的文件夹（如果没有显示，点击上方“查看”->“显示隐藏文件夹”）->`SVN Update`

##### # 常见问题

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/0cd080888c9b5fcfdc537059ed7eba75.png" alt="0cd080888c9b5fcfdc537059ed7eba75.png" border="0" />

出现这个错误是因为新建了一个仓库，并且指定了另一个用户访问权限，再次在本地检出的时候会默认使用上次记住的用户信息登录，所以会报错。解决方法是**清除缓存**。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/e41f8229135ca5cbaa7d541e254b5193.png" alt="e41f8229135ca5cbaa7d541e254b5193.png" border="0" width="30%"/>

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/4234f5f67fc148ea7b3768449f69b407.png" alt="4234f5f67fc148ea7b3768449f69b407.png" border="0" width="60%"/>

##### # 版本回退

可以将版本回退至以往提交过的版本。

右键当前文件夹空白处或要回退的文件->`TortoiseSVN`->`update to revise`

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/e97478428d59eada65f94a52ab46832c.png" alt="e97478428d59eada65f94a52ab46832c.png" border="0" width="50%"/>

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/599a38558bbbe428c38d6bd7e4160d78.png" alt="599a38558bbbe428c38d6bd7e4160d78.png" border="0" width="50%"/>

##### # 冲突问题解决

当两个用户上传同一个文件名的文件时，会发生文件覆盖问题，所以需要将这两个文件都保存下来。（同一个文件的同一个位置要展示不同的内容）

**解决方案1**：手动处理

点击提交时：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/287b69d438ec07caee672d7b20c2857e.png" alt="287b69d438ec07caee672d7b20c2857e.png" border="0" />

点击OK，然后依次点击如下列图的操作。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/eb1f5f818718ba73e01d46597a0f5954.png" alt="eb1f5f818718ba73e01d46597a0f5954.png" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/778a5aca9ad81ccf794785227f415bd8.png" alt="778a5aca9ad81ccf794785227f415bd8.png" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/c65aa3ce2f100d3fd27e779b2117197d.png" alt="c65aa3ce2f100d3fd27e779b2117197d.png" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/63b7e47b29dc7479b7eb8a84b45e17e2.png" alt="63b7e47b29dc7479b7eb8a84b45e17e2.png" border="0" />

打开`demo.txt`

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/7877a101085205dbaf036bb701c6ee43.png" alt="7877a101085205dbaf036bb701c6ee43.png" border="0" />

> 根据把别人写的放前面，你写的放后面的原则进行修改。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/5557c679700d6b12319bbd2e05249000.png" alt="5557c679700d6b12319bbd2e05249000.png" border="0" />

最后**删除**其它三个文件后再提交。

**解决方案2**：借助SVN工具

修改完文件点击更新，然后依次点击下图操作。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/1d74b03d49c52c1dccaeec6676202fe1.png" alt="1d74b03d49c52c1dccaeec6676202fe1.png" border="0" width="60%"/>

进来后会看到这个界面。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/cd05e613aeb0cba71f86ddab725c6570.png" alt="cd05e613aeb0cba71f86ddab725c6570.png" border="0" width="60%"/>

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/d5108f3c46a690271d14533e63d64509.png" alt="d5108f3c46a690271d14533e63d64509.png" border="0" width="60%"/>

然后点击保存按钮。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/5673d84249e57f70bbf539b133859dc1.png" alt="5673d84249e57f70bbf539b133859dc1.png" border="0" width="60%"/>

然后会发现其它自动生成的三个文件已经消失了，随后提交即可。

**解决方案3**：借助IDE工具

这里使用webstorm

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/40714d1c7a6b6305d4153dfe175ef210.png" alt="40714d1c7a6b6305d4153dfe175ef210.png" border="0" width="30%"/>

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/d6287ee2fd4ad87caf15cda9adb077da.png" alt="d6287ee2fd4ad87caf15cda9adb077da.png" border="0" />

先接受右边的，再接受左边的。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/93d2f8ceb2df75766e8ec9ab2a5de8b5.png" alt="93d2f8ceb2df75766e8ec9ab2a5de8b5.png" border="0" width="70%"/>

点击apply后提交即可。

##### # SVN设置忽略要提交的文件

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/13f95d728909b2f77c865693e410bd49.png" alt="13f95d728909b2f77c865693e410bd49.png" border="0" width="60%"/>

> 输入*.idea是忽略所有idea文件，输入.idea是忽略所有叫这个的文件夹。

##### # SVN锁

目的是给文件上锁，防止他人修改（其实可以被别人解锁，但是提交后会被发现）

右键要上锁的文件。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/836d01798a8863ad9df54aac9506bb1e.png" alt="836d01798a8863ad9df54aac9506bb1e.png" border="0" />

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/a65b38e88263e9b8e22b9f1619ed999a.png" alt="a65b38e88263e9b8e22b9f1619ed999a.png" border="0" width="60%"/>

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/a1f4391de804046698fc9392049d25d7.png" alt="a1f4391de804046698fc9392049d25d7.png" border="0" />

随后再次上传即可。所有人都动不了这个文件了。

##### # IDE内操作SVN

**提交**：

提交之前要设置自动忽略掉.idea等无关文件，如果你是webstorm较新版本（我是2020.1版本），要这样设置：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/23110d37eb35e93476624799a86734a0.png" alt="23110d37eb35e93476624799a86734a0.png" border="0" width="60%"/>

之后新建文件会有提示是否要自动标记，点击取消。可以自己标记文件：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/947afff789c280c5b0ababba28f95980.png" alt="947afff789c280c5b0ababba28f95980.png" border="0" width="30%"/>

然后在右上角的小图标点击提交即可。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/cf928ae9819f0eea1d1f376c1dd08044.png" alt="cf928ae9819f0eea1d1f376c1dd08044.png" border="0" width="40%"/>

**更新**：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/8922eb1e781a649414e7b45b76729c54.png" alt="8922eb1e781a649414e7b45b76729c54.png" border="0" width="40%"/>

**版本回退**：

右键要回退的文件。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/fc0743fec7567be7d0d02bd06dc7b183.png" alt="fc0743fec7567be7d0d02bd06dc7b183.png" border="0" width="30%"/>

在下方会显示历史版本记录，右键需要回退的版本即可。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/faf63f5041ffc7c54a2d2d255182b3e0.png" alt="faf63f5041ffc7c54a2d2d255182b3e0.png" border="0" />

> **补充**：webstorm会给文件显示颜色。以下是常见的颜色及对应的含义。
>
> - 暗红色：新增的文件
> - 亮红色：冲突
> - 蓝色：修改了但没有提交的文件
> - 绿色：文件已经被标识了

##### # 其它操作

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/4da840668a904893d7505b02234c6aaf.png" alt="4da840668a904893d7505b02234c6aaf.png" border="0"  width="60%"/>

##### # 清理SVN任务队列

我们在使用SVN时，有时候会遇到这个常见的报错：`Previous operation has not finished; run 'cleanup' if it was interrupted;`
按照这个提示，我们会去执行`cleanup`操作，但是令人崩溃的是，有时候`cleanup`也会报错，导致你的SVN罢工了，此时你需要清空SVN的内部队列。

具体操作过程如下：

```
1.将sqlite3.exe放到和.svn的同级目录下。
2.启动cmd，cd到仓库目录，执行：sqlite3 .svn/wc.db "select * from work_queue"。
3.你会看到很多的队列。
4.执行：sqlite3 .svn/wc.db "delete from work_queue"。
5.清空完毕。重新右键文件夹空白处执行cleanup，OK了！
```

> 一般只有任务太多的时候才会遇到这个问题

### 二、Git

#### 1. 简介

由linux之父林纳斯花了10天写出来的**分布式**版本控制工具。至今全球最为常用，一直被模仿，从未被超越。

Git是目前世界上最先进的**分布式**版本控制（没有之一）。

#### 2. 安装

没有window版安装包，但是有移植版。官网：https://git-scm.com/downloads

安装完成后，右键打开菜单栏找到“`Git`”->“`Git Bash`”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/3f05664e62e067a64114ef922f7b2c33.png" alt="3f05664e62e067a64114ef922f7b2c33.png" border="0" width="50%"/>

#### 3. 配置

安装完成后，还需要最后一步设置，在命令行输入：

`git config --global user.name "Your Name"` 

`git config --global user.email "email@example.com"`

> 建议手打，不要复制粘贴。
>
> **备注**：以上两步的名字和邮箱可随意配置，但最好使用自己的邮箱。

`git config user.name` 用于查看配置的姓名

`git config user.email` 用于查看配置的邮箱

因为Git是分布式版本控制系统，所以每个机器都必须自报家门：你的名字和Email地址。

#### 4. Linux的命令

**新建文件夹**：`mkdir xxx`

**新建文件**（Visual editor）：`vi x.txt`

输入 `i` 进入编辑模式

`ESC + ：+ wq` 保存并退出

`ESC + ：+ q!` 不保存并退出

**进入xxx目录**：`cd xxx`

**返回上一级目录**：`cd ..`

**列出当前文件夹中所有文件**：`ls`

**显示当前目录**：`pwd`

**显示文件内容**：`cat x.txt`

**清屏**：`clear`

#### 5. 分区介绍

git一共分为了三个区，工作区、版本区、暂存区。

- **工作区**（working Directory）：简单的理解——你在电脑里能看到的目录。
- **暂存区**（stage）：介于工作区和版本区中间，工作区到版本区的“必经之路”，隐藏在`.git`中
- **版本库**（Repository）：工作区有一个隐藏目录`.git`，准确的来说这个不算工作区，而是Git的版本库。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/a4b9d5d19ceb91b0f08a2b885d48c524.png" alt="a4b9d5d19ceb91b0f08a2b885d48c524.png" border="0" width="50%"/>

#### 6. 创建版本库

##### # 初始化版本库

使用`git init`命令。

创建成功会提示：`Initialized empty Git repository in c:/Users/xxx/Desktop/demogit/.git/`

> 目录上多出一个`.git`的文件夹,这个文件夹是Git来跟踪管理版本库的，不要去修改和删除这个文件里的内容。

##### # 添加指定文件到暂存区中

使用`git add x.xx`或`git add *`或`git add .`命令，若没有任何提示，代表交成功了。(后两者为全部添加)

- 若未初始化，会提示`fatal: Not a git repository (or any of the parent directories): .git`
- 失败会提示`fatal: pathspec 'x.txt' did not match any files`
- 可能会出现警告：`warning: LF will be replaced by CRLF in xxxxx` 

**警告原因**： `linux`和`window`的换行符不一致导致的。

**警告解决方式**：执行命令`git config --global core.autocrlf false`（意思为不进行自动转换）

**查看文件是否添加成功**：`git status`

1. 红色表示在工作区。

2. 绿色表示在暂存区。

3. 没有任何显示代表所有文件位于版本区。

##### # 提交暂存区所有文件到版本区

使用`git commit -m 'xxx'`命令。（引号里写提交注释）

提交成功会提示：

```
[master (root-commit) 88bbb64]
 first commit1 file changed, 
2 insertions(+)create mode 100644 x.txt
```

> 如果只输入`git commit`会出问题，这时需要`ESC  + ：+  q!` 退出就好

#### 7. 差异对比

`git diff` : 比较暂存区与工作区

`git diff --cached` : 比较版本区与暂存区

`git diff master` : 比较版本区与工作区

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/5304664e00951ebc0c8884b9b9850f6c.png" alt="5304664e00951ebc0c8884b9b9850f6c.png" border="0" width="50%"/>

#### 8. 查看日志和版本号

`git log`：显示从最近到最远的所有提交日志

`git reflog`：显示每次提交（`commit`）的`commit id`

#### 9. 版本操作

Git有三种版本操作：版本回退、版本穿梭、版本撤销。

##### # 版本回退

`git reset --hard HEAD^`，版本回退（回退一次提交）

`git reset --hard xxxxxx` ，回退到指定`xxxxxx`的`commit id`版本

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/935e72a07e9b125b715a71d710aabad4.png" alt="935e72a07e9b125b715a71d710aabad4.png" border="0" width="50%"/>

##### # 版本穿梭

`git reset HEAD`，用**版本库中**的文件去替换**暂存区**的全部文件。

`git checkout -- x.txt`，用**暂存区**指定文件去替换**工作区**的指定文件（<u>危险</u>）

`git checkout HEAD x.txt`，用**版本库**中的文件替换**暂存区**和**工作区**的文件（<u>危险</u>）

##### # 版本撤销

`git rm --cached x.txt`，从**暂存区**删除文件

#### 10. 删除文件

删除文件：`git rm x.txt`

> 删除的文件必须是经过git托管的，也就是在**缓存区**和**版本区**。
>
> **备注**：和手动删除的区别在于，Git命令删除会同时删除缓存区和版本区的文件。

删除文件夹：`git rm -r xxxx`

> 删除的文件夹必须有东西，不然自动忽略。文件夹也要经过Git托管。
>
> **注意**：仓库不能嵌套

#### 11. git完整图示

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/cc71c23c849286ea276644e9d618a13a.png" alt="cc71c23c849286ea276644e9d618a13a.png" border="0" width="50%"/>

#### 12. 分支

##### # 概念

分支是指将一个项目划分为若干个部分，每个部分都代表着不同的代码质量。一般分为主分支、开分分支、测试分支、里程碑分支。

**主分支**：`master`

代码经过了开发人员单元测试，以及测试人员详细的一套测试通过之后，确定没问题

**开发分支**：`dev`

开发人员所有的代码提交到此分支

**测试分支**：`test`

测试人员用的（由开发人员进行完单元测试的代码会放入此分支）

**里程碑分支**：`tags`

是完成品，比如v1.0.0

##### # 命令

`git checkout -b dev` ，创建dev分支，并切换到dev分支

`git branch` ，查看当前分支

`git checkout master` ，切换分支

`git merge dev` ，合并dev分支到当前分支

`git branch -d dev`  ，删除指定分支

`git diff branch1 branch2`  ，显示出两个分支之间所有有差异的文件的详细差异

`git diff branch1 branch2 --stat` ，显示出两个分支之间所有有差异的文件列表

`git diff branch1 branch2 xxx` ，显示指定文件的详细差异

> 注意1：在**新建**分支的时候，必须要在`master`分支上有文件，不然切换过去后`master`会消失。
>
> 注意2：在分支**合并**的时候，必须要先将两个分支上的文件都已经上传至版本区。
>
> 注意3：在**新建**分支的时候，确保`master`的文件已经上传至版本区。
>
> 注意4：在**新建**分支时，主分支上的文件会全部复制一份到新建的分支上。

#### 13. 版本冲突

合并分支时，如果在同一个文件，在同一个地方，都修改了或新增内容会引起版本冲突。

##### # 手动修改

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/0e2d90ef9486ffdb055a8ee292551c9c.png" alt="0e2d90ef9486ffdb055a8ee292551c9c.png" border="0" width="50%"/>

随后手动删除修改：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/32db4f6fab816f09b68fa4a4d993394b.png" alt="32db4f6fab816f09b68fa4a4d993394b.png" border="0" width="20%"/>

> 解决版本冲突最好的办法是借助IDE解决，简单且高效。

#### 14. Git与SVN总结

**SVN**：

- 优点：只有两个区，交互模型简单，命令不多

- 缺点：过于依赖中间人、对分支操作很不友好、无论是存储文件还是处理文件效率都不高。

**Git**：

- 优点：有本地库，不会依赖服务端。

- 缺点：操作繁琐

**总结**：

> Git在GitHub平台奔溃的情况下，依然可以在本地处理好分支、版本回退、版本穿梭等一系列操作，这也分布式的优势所在。而SVN在服务器端崩溃的情况下无法进行提交等一系列操作，这也是集中式劣势所在。

补充：[git常用命令总结 (zjgsuzjx.top)](https://www.zjgsuzjx.top/md/git常用命令总结.html)

## 二、GitHub

### 一、概念

#### 1. 含义

GitHub是一个Git项目托管网站，也目前全球最大的开源社区。

#### 2. 作用

能够分享你的代码或者其他开发人员配合一起开发。

`GitHub`是一个基于`Git`的代码托管平台，`Git`并不像`SVN`那样有一个中心服务器。目前我们使用到的`Git`命令都是在本地执行，你就需要将数据放到一台其他开发人员能够连接的服务器上。

#### 3. 界面功能介绍

<img src="https://img.zjgsuzjx.top/img/images/2021/07/14/366f75a91c06e9c6a118220f9066c6c4.png" alt="366f75a91c06e9c6a118220f9066c6c4.png" border="0" width="50%"/>

### 二、使用

#### 1. 关联

1. `git init`
2. `git add .`
3. `git commit -m "first commit"` 
4. 在GitHub上创建一个远程仓库
5. `git remote add origin https://github.com/你的用户名/仓库名.git` (HTTPS)

> **备注1**：如果此步关联错了，解决办法如下。
>
> 暴力解决：删除.git文件夹，重新建立本地仓库。
>
> 优雅解决：`git remote remove origin`，再在重新关联仓库。
>
> **备注2**：`origin` 可以随便起名，只是起到一个名字作用。
>
> **注意**：新建仓库时不要选增加`REDEME.md`

#### 2. 推送

1. `git push -u origin master` （首次加-u）
2. 根据提示输入用户名密码
3. 我们第一次推送`master`分支时，加上了`-u`参数，Git不但会把本地的`master`分支内容推送到远程新的`master`分支，还会把本地`master`分支和远程的`master`分支关联起来，在以后的推送时可以简化命令`git push origin master`。

> **备注**：正常情况下，成功推送一次后，电脑会记住和账号与密码，下次推送时不会再提示输入。若在电脑不能够自动记住GitHub的账户和密码，需执行以下命令解决：`git config --global credential.helper store`
>
> **备注2**：如果报错`OpenSSL SSL_read: Connection was reset`，那么需要输入`git config --global http.sslVerify "false"`
>
> **备注3**：如果想修改之前保存的用户名和密码，可以删除后再次登录新的信息。控制面板->用户账号->Windows凭据->git://github.com删除即可。

#### 3. 拉取

- 第一种拉取方式：`git pull origin master`（常用）

将远程仓库的master分支上代码版本复制/合并到本地master分支上

- 第二种拉取方式：`git fetch origin master:tmp`

新建一个`tmp`分支，将远程仓库的master分支上代码版本复制到`tmp`分支上，不会自动合并。

#### 4. 克隆

`git clone https://github.com/xxx.git` (HTTPS)

> **注意**：不能直接下载压缩包，因为不是仓库（没有`.git`）

#### 5. 分支操作

在GitHub上可以在仓库里手动新建分支。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/15/6cc4bbb2f9d9981bb8155c7ed41d1138.png" alt="6cc4bbb2f9d9981bb8155c7ed41d1138.png" border="0" />

此时再克隆时，会克隆所有的分支，但是用`git branch`命令是查看不到的。可以用`git checkout xxx`直接切换到该分支。（切过去之后再用`git branch`就能看到了）

如果GitHub仓库又新建了一个分支，可以用`git pull`拉取所有的分支。

站在哪个分支上push哪个分支的内容，GitHub只有该分支会有这个内容。

#### 6. webstorm操作

用webstorm打开含有.git的文件夹，可以查看并操作分支。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/15/867123c5011a048ce89f522d1909a993.png" alt="867123c5011a048ce89f522d1909a993.png" border="0" />

> 用webstorm打开后自动生成.idea文件夹，需要忽略。新建一个`.gitignore`文件，里面输入`.idea`，就可以忽略了。

可以在webstorm提交文件至GitHub。

<img src="https://img.zjgsuzjx.top/img/images/2021/07/15/3810c722279b0cbe812dc9f9f653174e.png" alt="3810c722279b0cbe812dc9f9f653174e.png" border="0" width="40%"/>

或者

<img src="https://img.zjgsuzjx.top/img/images/2021/07/15/898bc2b135ced0203cb4932756cdf79f.png" alt="898bc2b135ced0203cb4932756cdf79f.png" border="0" />

> 可能会遇到网络问题push不上去，检查是否关闭了翻墙软件，是否能正常网速访问GitHub，不能就改host文件，参考网络教程。

遇到冲突时，webstorm会提示合并操作。

其它常用操作：

<img src="https://img.zjgsuzjx.top/img/images/2021/07/15/c45a43ee348e5a7e48e5163b0aa259e4.png" alt="c45a43ee348e5a7e48e5163b0aa259e4.png" border="0" width="30%"/>

#### 7. GitHub其它功能

<img src="https://img.zjgsuzjx.top/img/images/2021/07/15/db768168d3c48e89596c3c2a7d423805.png" alt="db768168d3c48e89596c3c2a7d423805.png" border="0" />



## 三、番外之提交规范

- 每次提交之前：先更新, 再提交。
- 敏感时间点，一定及时更新文件。
- 多提交，避免“只关注写代码，不关注提交”的现象。
- 每次提交必须书写清晰明了的提交说明。
- 不要提交不能通过编译的代码。
- 不要提交自己不明白的代码。
- 慎用锁定功能（尽量避免使用锁，不轻易解锁上锁的文件）。
- 不要提交本地自动生成的文件、文件夹。















