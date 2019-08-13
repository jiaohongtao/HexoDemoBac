---
title: Git总结
date: 2019-08-12 11:10:35
top: 1
tags:
copyright: true
---
> 如有错误，斧正不甚感激

总结来自[廖雪峰老师的官方网站Git教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b0)

1. 配置用户名和密码：
	```
	git config --global user.name "Your Name"
	git config --global user.email "email@example.com"
	```
2. git init：把当前目录变成Git可以管理的仓库
3. git add xx：将文件xx添加到暂存区，可反复多次使用，添加多个文件
4. git commit -m "xx"：将暂存区所有文件提交到仓库
5. git status：查看仓库当前的状态
6. git diff xx：查看xx文件都做过哪些修改操作
7. git log( --pretty=oneline)：显示从最近到最远的提交日志(简行显示)
8. git reset --hard (HEAD^/版本号)：回退到(上一个/某个)版本
9. git reflog：记录所有历史版本号
10. git diff HEAD -- xx：查看工作区和版本库里面最新版本的区别
11. git checkout -- file：丢弃工作区的修改
12. git rm xx：删除xx文件(之后执行git commit提交完成)
13. 配置公钥：
	```
	ssh-keygen -t rsa -C "youremail@example.com"
	 ```
14. 连接远程仓库：
	```
	git remote add origin git@github.com:jiaoht/learngit.git
	```
16. git push -u origin master：把本地库的所有内容推送到远程库上(第一次推送master分支时，加上-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令)
17. git clone git@github.com:jiaoht/gitskills.git：从远程库克隆到本地库
18. git checkout：命令加上-b参数表示创建并切换，相当于以下两条命令：
	- git branch dev：创建分支
	- git checkout dev：切换分支
19. git branch：命令会列出所有分支，当前分支前面会标一个*号
20. git merge：命令用于合并指定分支到当前分支
21. git branch -d xx：删除xx分支
22. git log --graph( --pretty=oneline --abbrev-commit)：命令可以看到分支合并图
23. git merge --no-ff：用普通模式合并，合并后的历史有分支，能看出来曾经做过合并
24. git stash：把当前工作现场“储藏”起来，等以后恢复现场后继续工作
25. git stash list：列出工作现场
26. git stash pop：恢复工作现场的同时把stash内容也删了，相当于：
	- git stash apply：只恢复，不删除stash
	- git stash drop：删除stash
27. git branch -D name：强行删除，删除该分支时前须先切换到其他分支
28. git remote( -v)：查看远程库的信息(更详细的信息)
29. git push origin xx：推送xx分支
30. git checkout -b dev origin/dev：同事创建远程origin的dev分支到本地
31. git branch --set-upstream branch-name origin/branch-name：建立本地分支和远程分支的关联
32. git pull：抓取远程的新提交
33. git tag tagname：新建标签，默认为HEAD，也可以指定commit id
34. git tag -a tagname -m "blablabla..."：指定标签信息
35. git tag：查看所有标签
36. git push origin tagname：推送一个本地标签
37. git push origin --tags：推送全部未推送过的本地标签
38. git tag -d tagname：删除一个本地标签
39. git push origin :refs/tags/tagname：删除一个远程标签

#### 注意事项：
1. HEAD指向的版本就是当前版本.
2. 如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to branch-name origin/branch-name。
3. git rebase操作可以把本地未push的分叉提交历史整理成直线，使得我们在查看历史提交的变化时更容易，因为分叉的提交需要三方对比

---

总结来自来自[易百的Git教程](https://www.yiibai.com/git)

*这一部分属实看的不是很懂，其实上面的大概已经够用了，这部分可不看*

Gitee总结：

 1. echo 'This is my first Git control file ' > mytext.txt：新建的mytext.tex文件，将这句话放到文件中
 2. git status (-s/--short)：简行命令(未跟踪??,修改未暂存区:右M,修改入暂存区:左M,工作区被修改提交到暂存区后工作区中又被修改MM,暂存区A,文件重命名R,文件已从本地存储库中删除D)
3. git add . ：将所有文件暂存
4. git commit -a：加参数-a,直接跳过git add进行提交
5. git commit --amend：修改(覆盖)最后一次提交
6. git mv a b：把a文件命名为b,相当于：
	- mv a b
	- git rm a
	- git add b
7. git log -p -2：p用来显示每次提交的内容差异,仅显示最近两次提交
8. git log --stat：显示每次提交的简略的统计信息
9. git log --pretty=oneline(short/full/fuller/format)：指定使用不同于默认格式的方式展示提交历史，本次为显示在一行
10. git log --pretty=format:"%h %s" --graph：graph用ASCII字符串来显示分支
11. git remote show origin：查看远程仓库信息
12. git remote rename a b：远程仓库重命名
13. git remote rm：远程仓库移除
14. git branch -m oldname newname：重命名分支
15. git config -–add site.name jiaoht：添加配置项
16. git config --[local|global|system] -–unset xx：删除xx配置项
17. git add *Controller：将以Controller结尾的文件的所有修改添加到暂存区
18. git add Hello*：将所有以Hello开头的文件的修改添加到暂存区
19. git add Hello?：将以Hello开头后面只有一位的文件的修改提交到暂存区
20. git add -[u|A|i] [<path>]：
	- u：把<path>中所有跟踪文件中被修改过或已删除文件的信息添加到索引库，省略<path>表示 . ,即当前目录
	- A：把所有跟踪文件中被修改过或已删除文件和所有未跟踪的文件信息添加到索引库，省略<path>表示 . ,即当前目录
	- i：查看被所有修改过或已删除文件但没有提交的文件，并通过其revert子命令可以查看<path>中所有未跟踪的文件，同时进入一个子命令系统
21. git status -uno：只列出所有已经被git管理的且被修改但没提交的文件
22. git diff <file>：比较当前文件和暂存区文件差异
23. git diffgit diff <id1><id2>：比较两次提交之间的差异
24. git diff <branch1> <branch2>：在两个分支之间比较
25. git diff --[staged|cached]：比较暂存区和版本库差异
26. git diff --stat：仅仅比较统计信息
27. git text.txt mydir：将ext.txt 移动到 mydir，相当于：
	- mv test.txt mydir/
	- git rm test.txt
	- git add mydir
28. git log --pretty=format:"%an %ae %ad %cn %ce %cd %cr %s" --graph
	常见的format选项：
		#选项     #说明
		%H      提交对象(commit)的完整哈希字串
		%h      提交对象的简短哈希字串
		%T      树对象(tree)的完整哈希字串
		%t      树对象的简短哈希字串
		%P      父对象(parent)的完整哈希字串
		%p      父对象的简短哈希字串
		%an     作者(author)的名字
		%ae     作者的电子邮件地址
		%ad     作者修订日期(可以用 -date= 选项定制格式)
		%ar     作者修订日期，按多久以前的方式显示
		%cn     提交者(committer)的名字
		%ce     提交者的电子邮件地址
		%cd     提交日期
		%cr     提交日期，按多久以前的方式显示
		%s      提交说明
		--graph 显示分支

29. git log --before={3,weeks,ago} --after={2018-04-18}：
	- --after 仅显示指定时间之后的提交(不包含当前日期)
	- --before 仅显示指定时间之前的提交(包含当前日期)
30. git push --all origin：将本地的所有分支都推送到远程主机
31. git push origin --tags：向远程推送标签
32. git push origin tag_name：推送单个标签
33. git push origin :tag_name：删除单个标签
34. git remote add [shortname] [url]：添加一个新的远程仓库，和简名
35. git rebase：把一个分支的修改合并到当前分支(没怎么看懂)



注意事项：
git fetch和git pull的区别

	git fetch：相当于是从远程获取最新版本到本地，不会自动合并。
	$ git fetch origin master
	$ git log -p master..origin/master
	$ git merge origin/master

	以上命令的含义：
	首先从远程的origin的master主分支下载最新的版本到origin/master分支上
	然后比较本地的master分支和origin/master分支的差别
	最后进行合并

	上述过程其实可以用以下更清晰的方式来进行：
	$ git fetch origin master:tmp
	$ git diff tmp
	$ git merge tmp

	git pull：相当于是从远程获取最新版本并merge到本地
	git pull origin master

	上述命令其实相当于git fetch 和 git merge
	在实际使用中，git fetch更安全一些，因为在merge前，我们可以查看更新情况，然后再决定是否合并。

常用操作：

	为现有的代码库启动一个新的Git仓库：
		cd path：转到该路径下
		git init：创建一个/path/.git目录
		git add . ：将所有现有文件添加到索引
		git commit . -m "a commit message"：将原始状态记录为历史的第一个提交
