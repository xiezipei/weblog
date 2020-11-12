# 日报 20-11-03

## git revert & git reset

如何撤销上一次提交以及已经推送到远程的提交？

可以参考这篇文章：[如何撤销 Git 操作？](http://www.ruanyifeng.com/blog/2019/12/git-undo.html)，里面推荐了几种方法，但目前我推荐用 `git revert`（当然我更推荐用 SourceTree 来操作）。

另外推荐通过这篇文章总结一下 Git 命令：

> “一般来说，日常使用只要记住下图6个命令，就可以了。但是熟练使用，恐怕要记住60～100个命令。”

![最常用的6个git命令](https://user-images.githubusercontent.com/5949351/98065468-a7d76580-1e8f-11eb-9815-c8721ef8517d.png)

[常用 Git 命令清单](https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)


## fix: SourceTree skip husky git pre-commit

问题：项目加入 [husky](https://github.com/typicode/husky) 来规范 git commit message，在 VSCode 命令行、Mac 终端、VSCode Git GUI 都执行成功（如下图，message 不规范会提交失败），但是如果改用 SourceTree 会跳过 husky 的 pre-commit 校验。

![husky拦截成功](https://user-images.githubusercontent.com/5949351/98062622-5f1cae00-1e89-11eb-81a0-47703f9da4e2.png)

将 SourceTree 历史命令视图打开（菜单栏：`查看 -> 显示历史命令`），可以看到 commit 后会有报错提示 ` Can't find node in PATH, trying to find a node binary on your system`，很明显没调用到 Node 环境。

经过一番搜索和尝试，发现以下方法可行：

![](https://user-images.githubusercontent.com/5949351/98062631-62b03500-1e89-11eb-8bb4-3b037fbcf307.png)

传送门：[husky with sourcetree : Can't find node in PATH, trying to find a node binary on your system](https://github.com/typicode/husky/issues/390)