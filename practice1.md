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

更多有关于 pull 指令的知识可见 [pull 指令](https://www.yiibai.com/git/git_pull.html)链接




## Github的图片问题
可以直接拖动图片到想要的地方去，例如直接把本地的一张图片拖到了这里。![计算机专业课程](https://user-images.githubusercontent.com/82944876/116048451-c46a9280-a6a7-11eb-9244-895b51cc0807.png)



