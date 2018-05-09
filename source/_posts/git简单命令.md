---
title: git简单命令
date: 2018-05-09 15:17:37
tags: git
---
## git init
Git 使用 `git init` 命令来初始化一个 Git 仓库，Git 的很多命令都需要在 Git 的仓库中运行，所以 git init 是使用 Git 的第一个命令。在执行完成 git init 命令后，Git 仓库会生成一个 .git 目录，该目录包含了资源的所有元数据，其他的项目目录保持不变
![git init](http://wwjwwj.oss-cn-beijing.aliyuncs.com/18-5-9/30732083.jpg)
- 使用当前目录作为Git仓库，我们只需使它初始化。`git init`该命令执行完后会在当前目录生成一个 .git 目录。
- 使用我们指定目录作为Git仓库。`git init newrepo`初始化后，会在 newrepo 目录下会出现一个名为 .git 的目录
## git add 
该命令可将该文件添加到缓存，如我们添加以下两个文件 index.html和css/style.css
![git add](http://wwjwwj.oss-cn-beijing.aliyuncs.com/18-5-9/8381105.jpg)
- 可以一个一个地 add `git add index.html`
- 或者一次添加整个目录 `git add .`
## git commit -v
![git commit](http://wwjwwj.oss-cn-beijing.aliyuncs.com/18-5-9/28866872.jpg)
只输入git commit会启动文本编辑器以便输入本次提交的说明。编辑器会显示最后一次运行 git status 的输出，放在注释行里，另外开头还有一空行，供你输入提交说明。 如果想要更详细的对修改了哪些内容的提示，可以用 -v 选项，这会将你所做的改变的 diff 输出放到编辑器中从而使你知道本次提交具体做了哪些修改。退出编辑器时，Git 会丢掉注释行，用你输入提交附带信息生成一次提交。所以，使用git commit -v来提交内容时，会启动文本编辑器要求输入提交说明，此时只需输入说明，然后保存并退出即可，若输入的说明为空，则本次操作不会有结果