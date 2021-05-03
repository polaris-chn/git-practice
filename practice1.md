# 对于Git的一些练习和总结

## Git的本质

Git是一种分布式版本控制器	

## Git的pull指令

```git pull``` 命令用于从远程获取代码并合并本地的版本，其本质就是 ```git fetch```和 ```git merge FETCH_HEAD```的简写，命令格式如下：

```
git pull <远程主机名> <远程分支名> : <本地分支名>
```

如果当前分支只有一个追踪分支，连远程主机名都可以省略，即：

```
git pull
```

更多有关于 pull 指令的知识可见 [pull 指令](https://www.yiibai.com/git/git_pull.html)




## Github的图片问题
可以直接拖动图片到想要的地方去，例如直接把本地的一张图片拖到了这里。![计算机专业课程](https://user-images.githubusercontent.com/82944876/116048451-c46a9280-a6a7-11eb-9244-895b51cc0807.png)



## Git的文件夹问题

第一，Git似乎无法上传空文件夹，但是有时候新建了项目，暂时没有文件，先将目录架构提交，这个时候可以使用如下解决办法。在空文件夹中建立.gitkeep（文件名任意）文件，并写入一段话（话任意），例如：

```
# ignore everything in this directory
# except this file !.gitkeep
```

就是为了让文件夹中有一个新文件，这样就可以上传了。

第二，如果新文件夹中只有一个文件夹，那么在Github中就不会显示出这个文件夹，就会直接显示这个文件夹中的文件，打破文件目录关系，这个时候也可以新建一个`README.md`文件或者加上另一个文件夹就可以恢复原来的文件目录关系了。