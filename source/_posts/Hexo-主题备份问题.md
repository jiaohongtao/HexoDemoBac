---
title: Hexo 主题备份问题
copyright: true
date: 2019-08-13 15:09:57
tags:
---
一般备份hexo目录是，发现主题并没有提交上去，如下图：
![hexo主题备份问题](https://img-blog.csdnimg.cn/20190813151338961.png)
![lujingxianshi](/images/主题备份.png)

解决方式如下：

1. git rm --cached themes/next/
	>

		rm 'themes/next'

2. git status
	>

		On branch master

		Your branch is up to date with 'origin/master'.

		Changes to be committed:
		  (use "git reset HEAD <file>..." to unstage)

	        deleted:    themes/next

		Untracked files:
	  	(use "git add <file>..." to include in what will be committed)

        themes/

3. git add themes/next/

4. git status
	>

		On branch master
			Your branch is up to date with 'origin/master'.

			Changes to be committed:
		  	(use "git reset HEAD <file>..." to unstage)

		        deleted:    themes/next
		        new file:   themes/next/.all-contributorsrc
		        new file:   themes/next/.editorconfig
		        new file:   themes/next/.eslintrc.json
        		new file:   themes/next/.gitattributes`
				......

5. git commit -m "备份next主题"
	>

		[master 2386fe5] 备份next主题
		 347 files changed, 27937 insertions(+), 1 deletion(-)
		 delete mode 160000 themes/next
		 create mode 100644 themes/next/.all-contributorsrc
		 create mode 100644 themes/next/.editorconfig
		 ......

6. git push origin master
	>

		Enumerating objects: 418, done.
		Counting objects: 100% (418/418), done.
		Delta compression using up to 4 threads
		Compressing objects: 100% (400/400), done.
		Writing objects: 100% (416/416), 761.18 KiB | 3.49 MiB/s, done.
		Total 416 (delta 27), reused 0 (delta 0)
		remote: Resolving deltas: 100% (27/27), completed with 1 local object.
		To https://github.com/jiaoht/HexoDemoBac.git
		   e495fcb..2386fe5  master -> master
