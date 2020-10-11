# git面试题

> 暂时没有提供图示, 如果文字阅读起来困难推荐 [扩展阅读](#扩展阅读:)

## **分支管理模型**

一套完整规范的git分支管理规范, 在多人协作开发中是非常有必要的, 现在主流的git分支管理模型大概有以下几种：

- [git flow](#gitflow)
- [github flow](#githubflow)
- [gitLab flow](#gitlabflow)
- [TBD flow](#tbdflow)

### gitflow
git flow 会有两个长期存在的分支，主分支(master)和开发分支(develop)
- master: 
    - 这里用来做版本发布/上线的分支，这上面的版本是非常稳定了/基本不会进行修改的分支, 当需要发版时候会基于这个分支来打一个tag, 使用tag进行发布.

- hotfix: 
    - 有时候在master或者发布出去后也会出现一些bug和问题, 需要紧急修复时候就会基于master（或者是tag）产生出一个hotfix分支;
    - 当问题修复以后合并回master分支, 并重新打上tag紧急发布.
    - 同时还需要把修复的问题合并回 release 和 develop 分支;

- release:
    - 这是用来于准备发版的分支, 包含本次需要进行发版的最新代码, 到这一个分支后将不会再像里面添加新功能;
    - 这个分支是从develop产生出来的, 很多公司会把这个分支当作提交测试的分支（甚至有两次release分支, 那就测试有两个测试环境, 比如我们公司）;
    - 如果这个分支有存在bug, 可以在上面直接修复;
    - 当bug和问题修复完成, 准备就绪后, 这个分支（release）将会合并到master用于版本发布; 并且需要把在这个（release）分支修复的问题也需要合并回develop分支;

- develop：
    - 存放在开发中最新的代码, 极其不稳定
    - 一般用来给开发人员做的部署自测, 还没有提交给测试人员测试;

- feature：
    - 开发人员进行功能开发的分支, 每次开发新功能的时候会从develop上开出一个新的feature分支;
    - 当这个功能开发完成后, 会将代码合并回develop分支, 保证develop最新代码,所有人都能拉取到;
    - 合并完成后需要删除feature分支, 下次新功能会重新以develop开新的feature

- bugfix：
    - 在协同开发中, 难免会和其他同时遇到一些冲突/问题/或者是有一些bug，就可以以develop开一个bugfix分支;
    - 处理完成以后将bugfix分支合并回develop分支, 并删除bugfix分支;

### githubflow

- github flow相对简单/灵活一些, 上其只存在一个master分支, 并且这个分支使用保持可以发版的状态; 发版时基于master打一个tag；

- 那新功能和问题修复都是基于master开出一个新分支(分支名需要有意义), 处理完成以后通过PR(pull request)提交申请将代码合并回master;

- 当机器人🤖️和管理员检查代码没有问题后才合并到master中;

### gitlabflow
- master
    - 和github flow一样长期只存在一个master分支, 所有的功能/问题修复都是从master上开有意义的新分支进行开发，再合并回master;
- production:
    - 用于做产品在不同环境下的部署分支，如pre-production
    - 简述来说用于像一些预发布/测试版发布之类的
- release:
    - 从master的稳定版本创建release发布分支用于发布产品
    - 可以理解为正式发布的分支

### tbdflow
- 最大的特点是所有开发分支都基于trunk分支, 不存在长期的开发分支
- 要求所有的提交都尽快回到主分支trunk上

#### 扩展阅读: 
- [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
- [github flow](https://githubflow.github.io/)
- [gitlab flow](https://www.jianshu.com/p/0080df2c2d8c)
- [TBD flow](https://trunkbaseddevelopment.com/)

<br>

## **哪些常用的命令**
从初始化到提交
```bash
git init
git add files # git add . or git add -A(--all) or git add -u(--update) files
git commit -m "init:first commit";
git remote add origin xxx;
git push origin master:master;
git tag ...
```
克隆/更新/合并/撤回/切换
```bash
git clone xxx # git clone -b branchName xxx
git pull # git pull = git fetch + git merge
git fecth
git merge / git rebase
git reset / git revert
git checkout branchName/commit_id/tag
```
开分支/删除分支/快速找bug
```bash
git branch newbranchName # 空分支 git checkout --orphan branchName + git rm -rf .
git branch -D deleteBranchName
git push origin --delete deleteOriginBranchName

git bisect

# 暂时先这么列举这儿把
```

<br>

## git中的head是什么？
本身是一个指针,可以看作指向的是当前的分支或commit, 在`.git`目录的`HEAD`中可以看到它指向的内容;

```bash
cat .git/HEAD
ref: refs/heads/master
```

然后这里是指向master分支, 然后打开其实分支就是一个40为的字符串（sha1算法）
```bash
cat .git/refs/heads/master
e12d8ef0e8b9deae8bf115c5ce51dbc2e09c8904
```

当你在切换分支的时候, 上面HEAD的指向就会发生变化

<br>

## 可以删除master分支吗, 为什么？

当然可以删除, 你可以把分支看作盒子上的一个标签而已🏷️, 你删除master的时候其实就相当于从盒子上把标签撕下来, 本身盒子还是在那里的；

只是在git中我们看不到这个盒子, 他以另一种格式存起来来, 当我们重新给它贴上一个新标签就可以看到它来（有一个hash值就行了）.