





### **熟悉完下面git的基本操作可以直接下载[GitHub图形界面程序](https://desktop.github.com/)并安装使用**






## Part 1：本地git

- 第一步：下载[Git](https://git-scm.com/download/)并安装

- 第二步：新建一个空白的本地项目文件，并打开Git Bash

  ![6NIQ61.png](https://s3.ax1x.com/2021/03/12/6NIQ61.png)

- 第三步：要设置自己的身份，比如git提交代码的时候要让别人知道什么人提交了代码，

  设置身份内容有两条，一个是你的邮箱，另一个是你的称呼 ，以后你提交的代码都根据这个来确定是你提交的的了。“Your Name”填你想让别人知道的名字，“email@example.com”换成自己的邮箱。

  自此以后你写的bug就会被人认出来是你写的了。

  输入：

  ```bash
  $ git config --global user.name "Your Name"
  $ git config --global user.email "email@example.com"
  ```

- 第四步（这一步我们应该已经完成了）：从终端进入你想要记录内容更改的文件夹里例如我们进入`gittest`文件夹

- 第五步：Git初始化

  输入：

  ```bash
  $ git init
  ```

  这个文件夹以后的更改就会被记录了。（如果是空文件夹会提示`Initialized empty Git repository in /home/yep/code/gittest/.git/`，告诉你文件夹为空）

- 第六步：现在我们在文件夹里新建一个文件hello.txt,内容是

  ```bash
  Hello World
  ```

- 第七步：保存后，我们使用`git add`命令，告诉git我们把文件添加到仓库缓存区了，在终端输入

  ```bash
  $ git add hello.txt
  ```

  没有提示说明操作成功。

- 第八步：使用`git commit`命令，告诉git我们要把缓存区的所有文件正式提交到仓库：

  ```bash
  $ git commit -m "添加了hello.txt"
  ```

  其中 -m 和后面引号内容是本次提交的说明，也就是描述你每次改了什么。

  结果：

  ```bash
  [master (root-commit) ec4652d] 添加了hello.txt
   1 file changed, 1 insertion(+)
   create mode 100644 hello.txt
  ```

  git commit命令执行成功后会告诉你，`1 file changed`：1个文件被改动（我们新添加的hello.txt文件）；`1 insertions`：插入了两行内容（hello.txt有一行内容）。

  为什么Git添加文件需要`add`，`commit`一共两步呢？因为`commit`可以一次提交很多文件，所以你可以多次`add`不同的文件，比如：

  ```bash
  $ git add file1.txt
  $ git add file2.txt file3.txt
  $ git commit -m "add 3 files."
  ```

  `add`把文件放到了缓存区，然后`commit`正式提交到仓库。

  


## Part 2：Github（个人）

- 第一步：注册账号[GitHub官网](https://github.com)

- 第二步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：

  ```ssh-keygen -t rsa -C "youremail@example.com" ```

  如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有`id_rsa`和`id_rsa.pub`两个文件，这两个就是SSH Key的秘钥对，`id_rsa`是私钥，不能泄露出去，`id_rsa.pub`是公钥，可以放心地告诉任何人。
  打开id_rsa.pub,复制里面的内容。

- 第三步：登陆GitHub，打开“Account settings”，“SSH Keys and GPG keys”页面：
  ![img](https://upload-images.jianshu.io/upload_images/4064394-79cd18224d3a27c6.png?imageMogr2/auto-orient/strip|imageView2/2/w/757/format/webp)

  然后，点“New SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容即可。

- 第四步：用浏览器打开自己的仓库（[这里以我的为例](https://github.com/oliverwang15/test)）并复制这个链接:

  ![6NTsJg.png](https://s3.ax1x.com/2021/03/12/6NTsJg.png)

- 第五步：使用`Git clone`直接从远程仓库克隆下来

  ```bash
  $ git clone https://github.com/oliverwang15/test.git
  ```

- 第六步：把本地库的所有内容推送到远程库上

  ```bash
  $ git push
  ```

----
  或者

- 第五步：将远程仓库和本地仓库关联起来：

  ```bash
  $ git remote add origin https://github.com/oliverwang15/test.git
  ```
  origin就在本地代表了该仓库的名称可以随意指定，但一般定为origin

- 第六步：把本地库的所有内容推送到远程库上

  ```bash
  $ git push -u origin master
  或者
  $ git push origin master
  ```

***


## Part 3：GitHub（团队）

* 第一步：创建团队账号（略）
* 第二步：使用`Git clone`直接从远程仓库克隆下来

  ```bash
  $ git clone https://github.com/Quanti-Algorithm-based-on-Deep-Learning/test.git
  ```

----
  或者

- 第二步：将远程仓库和本地仓库关联起来：

  ```bash
  $ git remote add origin https://github.com/Quanti-Algorithm-based-on-Deep-Learning/test.git
  ```
  origin就在本地代表了该仓库的名称可以随意指定，但一般定为origin

----
- 第三步：把本地库的所有内容推送到远程库上
    ```bash
  $ git add filename
  $ git commit -m "升级了一下版本"
  $ git push origin master
  ```

## part 4：一些基本操作汇总
* 创建仓库命令
  ```bash
  $ git init	初始化仓库
  $ git clone	拷贝一份远程仓库，也就是下载一个项目。
  ```
* 提交与修改
  ```bash
  $ git add	添加文件到仓库
  $ git status	查看仓库当前的状态，显示有变更的文件。
  $ git diff	比较文件的不同，即暂存区和工作区的差异。
  $ git commit	提交暂存区到本地仓库。
  $ git reset	回退版本。
  $ git rm	删除工作区文件。
  $ git mv	移动或重命名工作区文件。
  ```
* 提交日志
  ```bash
  $ git log	查看历史提交记录
  $ git blame <file>	以列表形式查看指定文件的历史修改记录
  ```
* 远程操作
  ```bash
  $ git remote	远程仓库操作
  $ git fetch	从远程获取代码库
  $ git pull	下载远程代码并合并
  $ git push	上传远程代码并合并
  ```


########################### 以下这部分以后可能用到 ################################

## part 5：实现版本回退

现在修改hello.txt里的内容：

``` python
print("Hello World")
print("老板是神经病")
```

因为对工作很不满，下班前添加了第二行，“老板是神经病”,然后提交

``` bash
$ git add hello.txt
$ git commit -m "hello.txt里添加了一句话"
```

提示：

```bash
[master 88d885c] 在hello.txt添加了一句话
 1 file changed, 2 insertions(+), 1 deletion(-)
```

像这样，你不断对文件进行修改，然后不断提交修改到版本库里，就好比玩RPG游戏时，每通过一关就会自动把游戏状态存盘，如果某一关没过去，你还可以选择读取前一关的状态。有些时候，在打Boss之前，你会手动存盘，以便万一打Boss失败了，可以从最近的地方重新开始。Git也是一样，每当你觉得文件修改到一定程度的时候，就可以“保存一个快照”，这个快照在Git中被称为commit。一旦你把文件改乱了，或者误删了文件，还可以从最近的一个commit恢复，然后继续工作，而不是把几个月的工作成果全部丢失。

现在，我们回顾一下hello.txt文件一共有几个版本被提交到Git仓库里了：

版本1：添加了hello.txt

版本2：在hellotxt添加了几句话

到了第二天早上你后悔了，想回到昨天下班前代码的状态

当然了，在实际工作中，我们脑子里怎么可能记得一个几千行的文件每次都改了什么内容，不然要版本控制系统干什么。版本控制系统肯定有某个命令可以告诉我们历史记录，在Git中，我们用git log命令查看：
 输入`git log`命令查看版本情况
 输入：

```bash
$ git log
```

显示了过去所有的修改时间、修改人、修改内容：

```bash
commit 88d885c21216cbedacb1692e08d51afa6d4e32a7 (HEAD -> master)
Author: yepdlpc <mattbaisteins@gmail.com>
Date:   Wed Dec 19 20:13:22 2018 +0800

    在hello.txt添加了一句话

commit ec4652d5d0b8662fc8730d64b42341d1c363a442
Author: yepdlpc <mattbaisteins@gmail.com>
Date:   Wed Dec 19 20:11:42 2018 +0800

    添加了hello.txt
```

yepdlpc和邮箱都是我的。。我们可以看到，最新的提交在最上面，并按时间有近到远。并且每一次提交修改都生成了一个commit id，我们可以认为这个id是当时的这个版本的版本号，这个commit id是我们找回当时版本的`唯一凭据`。

我们只有两次提交，只需要回到`ec645.......`这个commit id时的版本就行。

Git中使用HEAD表示当前版本，也就是`commit 88d885c21216cbedacb1692e08d51afa6d4e32a7`，

`HEAD^`表示上一个版本，`HEAD^^`表示上上一个版本，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`。

现在，我们要把当前版本回退到上一个版本，就可以使用`git reset`命令：

```bash
$ git reset --hard HEAD^
```

`--hard`参数有啥意义？这个后面再讲，现在你先放心使用。

此时我们可以看到hello.txt的文件内容变回了：

```python
print("Hello World")
```

果然被还原了。

还可以继续回退到上一个版本，不过且慢，然我们用`git log`再看看现在版本库的状态：

```bash
Author: yepdlpc <mattbaisteins@gmail.com>
Date:   Wed Dec 19 20:11:42 2018 +0800

    添加了hello.txt
```

最新的那个版本`88d885c21216cbedacb1692e08d51afa6d4e32a7`已经看不到了！好比你从21世纪坐时光穿梭机来到了19世纪，想再回去已经回不去了，肿么办？

办法其实还是有的，只要上面的命令行窗口还没有被关掉，你就可以顺着往上找啊找啊，找到那个commit id是`88d885c21216cbedacb1692e08d51afa6d4e32a7`，于是就可以指定回到未来的某个版本：

```bash
$ git reset --hard 88d885
```

版本号没必要写全，前几位就可以了，Git会自动去找。当然也不能只写前一两位，因为Git可能会找到多个版本号，就无法确定是哪一个了。

我们再看hello.txt的内容：

```python
print("Hello World!")
print("老板是神经病")
```

果然，我胡汉三又回来了。

Git的版本回退速度非常快，因为Git在内部有个指向当前版本的HEAD指针，当你回退版本的时候，Git仅仅是把HEAD从指向某个版本：



![img](https://upload-images.jianshu.io/upload_images/4064394-a7d7e6a6fbe2fc9f.png?imageMogr2/auto-orient/strip|imageView2/2/w/294/format/webp)

head指针

现在，你回退到了某个版本，关掉了电脑，第二天早上就后悔了，想恢复到新版本怎么办？找不到新版本的`commit id`怎么办？

在Git中，总是有后悔药可以吃的。当你用`$ git reset --hard HEAD^`回退到旧版本时，再想恢复到新版本，就必须找到新版本的的commit id。
 Git提供了一个命令`git reflog`用来记录你的每一次命令：

```bash
$ git reflog
```
结果：
   ```
88d885c (HEAD -> master) HEAD@{0}: reset: moving to 88d885c21216cbedacb1692e08d51afa6d4e32a7
ec4652d HEAD@{1}: reset: moving to HEAD^
88d885c (HEAD -> master) HEAD@{2}: commit: 在hello.txt添加了一句话
ec4652d HEAD@{3}: commit (initial): 添加了hello.txt
   ```
