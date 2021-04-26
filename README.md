# 使用Git和Github的一些经验总结

Git是一种分布式版本控制系统，Github是一个基于Git开发的商业代码托管网站，可以将很多的代码和资料放在这个网站上。两者的配合使用可以很好地提升工作效率，并且可以方便地进行大型项目的团队开发。

## 链接Git和Github

首先需要下载[Git](https://git-scm.com/downloads)软件，下载完成软件之后即可进行安装，一路点击 next 即可，安装完成之后即进行Git的配置。

### Git的配置

配置本地Git环境的时候，首先需要在 git config 中声明 user.name 和 user.email ，因为在以后每次提交（commit）的时候都是使用该信息来进行记录。

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

复制公钥文件内容，进入自己的Github账号，进入 账户 >> Setting >> SSH and GPG keys 一栏，选择 New SSH，其中的 Title 可以任意填写，将刚才复制的公钥文件内容粘贴到 Key 一栏中，点击 add ssh key 即可。



