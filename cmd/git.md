# 同步本地和github上的项目

>以下xxx指项目的地址，如果是自己的项目需要先创建才有地址

## 1.设置git账户密钥
参考:https://www.cnblogs.com/xiaoxiaodevlog/p/10704977.html

## 2.下载一个项目到本地
两种方法：
- 下载新项目
>git clone xxx

### 2.1 从git更新到本地

- 初始化(第一次需要)
> git init

- 添加项目(第一次需要)
> git remote add origin xxx

- 本地没有修改过,只有master分之，直接更新
> git pull

#### 2.2 本地代码有修改，多分支

- 先切换到master分支
>git checkout master

- 更新master
>git pull

- 切换到另一分之 A
>git checkout A

- 把Master合并到 A
>git merger master

#### 2.3 本地修改过但只有master

- 直接覆盖本地代码
> git reset --hard

- 更新代码
> git pull

## 3.本地上传到git

- 初始化(第一次需要)
>git init

- 添加项目(第一次需要)
> git remote add origin xxx

- 提交文件(.代表全部提交)
>git add . 

- 提交确认
>git commit -m "first commit"

- 上传
> git push origin master #从本地上传

> git push -u origin master #参数 -u 可以使后面pull和push不加其他参数

- 下载
>git pull

## 4.断点续传
大文件下载用git clone会断.
建一个本地仓库(文件夹)，之后用fetch和checkout解决
```
>git mkdir xxx
>cd xxx
>git fetch https://xxxxx.git
#可以反复用fetch续传，直到下载完毕，出现以下字样:
#*branch HEAD -> FETCH_HEAD
>git checkout FETCH_HEAD
#项目就完整生成在本地了
```

## 5.bug解决
如果想更新本地项目和git项目的地址可以用如下：
>git remote remove origin

之后再本地项目文件夹下通过cmd添加新地址
>git remote add origin xxx

不然会报如下错误：
>fatal: remote origin already exists.

## 6.本地代码回倒某个提交时刻

回到远程仓库的版本
>git reset --hard FETCH_HEAD

查找历史记录版本
>git reflog

回到某个位置，如HEAD@{2}
>git reset --hard HEAD@{2} 

## 参考:
- 全记录
https://blog.csdn.net/weixin_30699831/article/details/101982286?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task

- 远程同步到本地
https://www.cnblogs.com/delav/p/11118555.html
