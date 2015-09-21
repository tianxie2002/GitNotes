1.github开启了双因素验证后git push使用https方式验证权限失败          
为命令行创建一个口令:    
https://help.github.com/articles/creating-an-access-token-for-command-line-use/  
Username for 'https://github.com': 用户名  
Password for 'https://用户名@github.com':   
这里的Password项目你将在github后台生成的accesstoken 粘帖进去就行了

2如果你实在想尝试命令操作：​   
显示：defaults write com.apple.finder AppleShowAllFiles -bool true   
隐藏：defaults write com.apple.finder AppleShowAllFiles -bool false 


查看配置    
git config --list

初始化仓库
$ git init  
$ git add *.c  
$ git add README.MD  
$ git commit -m 'initial project version'
	
现有仓库克隆  
$ git clone git://github.com/schacon/grit.git
	
仓库状态
$ git status

跟踪新文件  
$ git add fileName

查看已暂存和未暂存的更新  
$ git diff  
$ git diff --cached  //已经暂存起来的文件和上次提交时的快照之间的差异
	
提交更新  
$ git commit -m "message" // 简单的提交方式  
$ git commit -a -m "message" // 跳过add 步骤 把已经跟踪的文件全部提交
	
移除文件  
$git rm fileName  
$ git rm --cached readme.txt //移除跟踪但不删除文件


移动文件  
$ git mv file_from file_to
	
日志  
$ git log  
$ git log –p -2 // -p 提交内容的差异  -2最近两次  
$ git log --stat//显示简要的增改行数统计  
	
修改最后一次提交  
$ git commit --amend //---第2次提交修改了第一次提交  
$ git commit -m 'initial commit'  
$ git add forgotten_file  
$ git commit --amend   
	
取消已经暂存的文件  
$ git reset HEAD fileName

取消对文件的修改(回退到以前未修改的状态) //很有用 也很危险  
 $ git checkout -- fileName
 
远程仓库的使用

查看当前的远程库  
$ git remote -v // -v 列出远程地址
	
添加远程仓库  
$ git remote add Name git://github.com/paulboone/ticgit.git
	
从远程仓库抓取数据  
$ git fetch [remote-name]  
$ git pull// 合并远程的全部分支到本地（不确定）
	
推送数据到远程仓库  
$ git push origin master //推送 origin 到 master
	
查看远程仓库信息    
$ git remote show origin
	
远程仓库的删除和重命名    
$ git remote rename pb paul// pb 改成 paul  分支对应前缀也会发生变化  
$ git remote rm paul// 貌似删除  

列显已有的标签  
$ git tag  
$ git tag -l 'v1.4.2.*'//搜索标签  
	
新建标签  
$ git tag -a v1.4 -m 'my version 1.4' //新建v1.4标签 消息是 my version 1.4
	
分享标签  
$ git push origin [tagname] //提交 一个标签  
$ git push origin --tags // 推送所有本地标签  
        
删除  
$ git tag -d [tagname] //删除标签  
$ git push origin :refs/tags/tagname //删除远程标签

分支
创建分支  
$ git branch testing // 创建testing  
$ git checkout testing// 切换到testing  
$ git checkout -b iss53 //创建并切换到iss53  
$ git merge hotfix //把hotfix 分支合并到当前分支 	
查看分支  
$ git branch -v//最后一次commit信息  
$ git branch --merged | --no-merged//筛选出你已经（或尚未）与当前分支合并的分支  
 删除  
 $ git branch -D testing  
推送  
$ git push origin serverfix//把当前推送到 serverfix分支  
更新同步  
$ git fetch  
删除远程分支  
git push origin :branchname  
git branch  –r //查看所有分支信息  
//获取远端分支  
$ git checkout -b sf origin/serverfix