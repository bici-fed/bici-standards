# Git分支规范

![image.png](https://i.loli.net/2020/02/17/BXSfk4N8IgJtodw.png)

Git 是目前最流行的源代码管理工具， GitHub、Bitbucket、GitLab等云服务平台都是基于 Git，团队目前 Git 分支管理的规范基于 [Git Flow](http://nvie.com/posts/a-successful-git-branching-model/)。

## Why Git Flow

![image.png](https://i.loli.net/2020/02/17/AnlU6mgJOFxZ9qk.png)

分支管理有多种策略，Git Flow 是流传最广的 Git 分支管理实践，也是最契合团队的实践，为什么？

**因为 Git Flow 围绕的核心概念是版本发布（release）**。所以 Git Flow 适用于持续集成的，有较长版本发布周期的项目，也同样适用于 Sass 类项目。

## 分支

Git Flow 中包含 5 个分支，**master, develop, feature, release, hotfix**，我们先来简单了解下各分支。

### master

master 是主分支，也是用于部署生产环境的分支，所以必须确保 master 分支是最稳定的分支，如何确保稳定性？

- 任何时候都不能在 master 分支上修改代码
- 只能由 develop，release 和 hotfix 合并
- 提交到 master 分支的合并必须经过审核，测试

### develop

develop 分支是开发分支，分支中包含的是下个版本需要发布的内容，需要保证 develop 始终是最新完成的分支，因为新功能的开发分支是基于 develop 创建的。

### feature

feature 分支是以 develop 为基础创建的功能分支，开发一个新功能时，需要从 develop 创建该分支，功能完成后合并到 develop 并删除分支。

### release

release 分支是预上线分支，在发布提测阶段，所有的缺陷修复都在 release 分支上完成。实际的开发中，当有新功能开发完成后，首先会合并到 develop 分支，进入提测时，创建 release 分支，测试完成后，需要合并 release 分支到 develop 分支和 master 分支，此时 master 为最新分支，用于上线。

### hotfix

hotfix 分支用于线上紧急缺陷修复，也叫做补丁分支。当你需要通过 hotfix 分支修复线上问题时，流程应该是：从 master 创建 hotfix 分支，完成修复后，合并 hotfix 分支到 master 和 develop，并删除 hotfix 分支。
