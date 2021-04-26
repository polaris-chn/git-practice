# 使用Git和Github的一些经验总结

Git是一种分布式版本控制系统，Github是一个基于Git开发的商业代码托管网站，可以将很多的代码和资料放在这个网站上。两者的配合使用可以很好地提升工作效率，并且可以方便地进行大型项目的团队开发。关于Git的一些基本使用教程，可见[菜鸟教程-Git教程](https://www.runoob.com/git/git-tutorial.html)

## 链接Git和Github

首先需要下载[Git](https://git-scm.com/downloads)软件，下载完成软件之后即可进行安装，一路点击 next 即可，安装完成之后即进行Git的配置。

### Git的配置

配置本地Git环境的时候，首先需要打开Git的 Bash 环境，在本地仓库中 右键 >> Git Bash Here，即可打开 Bash 环境。随后在 git config 中声明 user.name 和 user.email ，因为在以后每次提交（commit）的时候都是使用该信息来进行记录。

```
git config --global user.name "你的用户名"
git config --global user.email "你的用户邮箱"
```

之后可以使用以下指令来查看配置信息。

```
git config --list
```

对于用户名和用户邮箱的配置，就像是给了本地机器一个识别码。Github仓库和本地仓库之间通过 ssh 秘钥进行连接，而Github仓库对于本地机器的识别就是通过这个识别码，类似于一个通行证，有了这个通行证就可以让本地机器给Github仓库进行提交。在完成 user.name 和 user.email 的配置之后，需要配置 ssh 公钥。Github是基于 ssh 协议的Git服务，所以在访问远程仓库（也就是Github仓库）的时候需要使用 ssh 协议，也就是需要产生 ssh 公钥。

```
cd ~/.ssh
```

可以进入 .ssh 文件夹中看是否有 .pub 后缀的公钥文件，如果没有，需要使用以下指令产生公钥。

```
ssh-keygen -t rsa -C "你的用户邮箱"
```

注意此处 ssh 和 -keygen 之间没有空格。随后进入到 .ssh 文件夹查看公钥文件内容。

```
cat ~/.ssh/id_rsa.pub
```

复制公钥文件内容，进入自己的Github账号，进入 账户 >> Setting >> SSH and GPG keys 一栏，选择 New SSH，其中的 Title 可以任意填写，将刚才复制的公钥文件内容粘贴到 Key 一栏中，点击 add ssh key 即可。配置完 user.name 和 user.email 以及 ssh 公钥之后，本地的Git和远程的Github重要可以远程通信了。

### Git和Github的链接

在完成Git的配置以及本地Git和远程Github账号的链接之后，需要将本地的仓库和远程Github中的仓库（repository）进行链接，也就是在本地仓库的任意修改可以通过链接将远程Github仓库中的内容也进行修改，这也是Github这样代码托管网站最大的作用。对于本地仓库和Github仓库的链接，一般有两种方式。

#### Github上已有仓库

可以在本地新建一个文件夹，在该文件夹内打开Git Bash，然后输入以下指令，就可将Github上的仓库复制到新建文件夹中。

```
git clone git@github.com:polaris-chn/git-practice.git
```

其中 clone 之后的内容是Github上仓库的 ssh 地址，这样就把Github上仓库的内容下载下来了。

#### Github上没有仓库

如果Github没有仓库，则本地仓库和Github上仓库的链接比较麻烦。

首先在本地新建文件夹作为本地仓库，进入新建文件夹打开Git Bash输入以下指令初始化本地仓库。

```
git init
```

然后在Github上新建一个仓库，不要在初始化的时候加入README.md文件（其实初始化README.md也可以，后续有相应的解决办法），然后在本地仓库的Git Bash中输入以下指令，建立两个仓库之间的链接。

```
git remote add origin git@github.com:polaris-chn/git-practice.git
```

其中origin是本地仓库，后面的部分是Github仓库的 ssh 地址。至此，Git和Github之间就建立了链接。





## Git的基本使用教程

### 代码同步到远程仓库

在一个空的项目中，一般首先会建立一个 README.md 文件，该文件对于整体项目做一个简要说明。

```
touch README.md
```

在Git中可以使用 vim 编辑器对 README.md 文件进行修改（当然也可以通过其他文本编辑器在本地仓库中修改，或者在Git中设置使用其他的文本编辑器修改，后续会继续说明），修改完成之后使用如下指令添加修改：

```
git add .
```

该指令代表添加全部已经修改的文件，命令效果等同于

```
git add -a
```

随后将修改后的文件提交到本地仓库中，使用如下指令：

```
git commit -m "提交的说明"
```

**注意**此处双引号中的 **提交说明** 一定要有，否则提交可能会出错；并且为了说明此次提交修改了什么，也应该简要体现在 **提交说明** 中。随后将修改提交到远程Github仓库中。

```
git push -u origin master
```

上述指令中 ***-u***，就是创建 upStream 上传流，如果没有这个上传流就无法将代码推送到Github，同时这个上传流只需要在初次推送代码的时候时候，以后就不需要了，也就是指令改成如下形式。

```
git push origin master
```

此外，项目中有了任何修改之后，也都是按照上述的基本流程进行添加，提交，上传。可能有些步骤不完全一样，后续会进行说明。











