Git是一个版本控制工具
----------------------------------------------------------
本地仓库测试
git add 文件名						添加代码
git commit -m "代码功能简介"		提交代码
在本地仓库阶段，提交代码需要两个步骤：add和commit
----------------------------------------------------------
版本管理测试
“我添加了版本一”
利用git log 命令可以查看历史版本操作记录，也可以用git log --pretty=oneline，显示更简单
“我添加了版本二”
git reset --hard HEAD^		回退至上一个版本（多个版本用HEAD~数字）
git reflog					查看版本更新记录（可以根据commitID跳转至所需版本：git reset --hard 3628164）
----------------------------------------------------------
工作区和暂存区
git add命令是把文件的更改提交到暂存区里，git commit命令是把所有在暂存区的更改一次性提交到工作区里
管理修改
每次修改都需要add一次，然后再commit
撤销修改测试
git checkout 文件名			用于当修改没有添加到暂存区里的情况（没有add）
git reset HEAD 文件名		用于当修改已经添加到暂存区里的情况（add之后没有commit）
删除文件
git rm 文件名				用于删除版本库里的文件
git checkout 文件名			用于误删工作区的文件后用版本库的checkout恢复文件
----------------------------------------------------------
远程仓库
ssh-keygen -t rsa -C "denzel_dc@163.com"							创建SSH公钥，添加到GitHub
git remote add origin git@github.com:DenzelVicent/GitLearn.git 		本地仓库和远程仓库绑定（origin是远程仓库的名字）
git push -u origin master 											把本地仓库的文件推送到远程仓库上（master是分支的名字）
git clone git@github.com:DenzelVicent/GitLearn.git 					从远程仓库上下载项目
----------------------------------------------------------
分支管理
git branch 					查看所有分支
git branch 分支名			创新的分支
git checkout 分支名 		切换到新的分支
git checkout -b 分支名 		创建并切换到新的分支
git merge 分支名 			合并某分支到当前分支
git branch -d 分支名 		删除分支
冲突合并
【<<<<<<< HEAD
【Creating a new branch is quick & simple.
【=======
【Creating a new branch is quick AND simple.
【>>>>>>> feature1
Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容，我们修改后重新提交即可
git log --graph				可以看到分支合并图
分支合并策略
git merge --no-ff dev 								合并分支时尽量不必使用fastforward模式，因为会删除历史分支信息
git merge --no-ff -m "merge with no-ff" dev 		因为合并要创建一个新的commit，所以加上-m参数，把commit描述写进去。更快速。
BUG分支
当临时有BUG修复任务时，需要把当前任务现场保存起来（不提交），新建BUG分支
git stash 							保存当前工作现场
git checkout -b BUG1 				创建bug分支
修复完成后，返回工作现场
git stash list 						查看所有保存的工作场景
git stash apply stash@{0}			恢复stash但不删除（如果只有一个stash，可以不带stash代号）
git stash drop stash@{0}			删除stash
git stash pop stash@{0}				恢复的同时删除stash内容 
git branch -D feature-vulcan 		强制删除未合并的分支
----------------------------------------------------------
多人协作
因此，多人协作的工作模式通常是这样：
首先，可以试图用git push origin branch-name推送自己的修改；
如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
如果合并有冲突，则解决冲突，并在本地提交；
没有冲突或者解决掉冲突后，再用git push origin branch-name推送就能成功！
如果git pull提示“no tracking information”，则说明本地分支和远程分支的链接关系没有创建，
用命令git branch --set-upstream branch-name origin/branch-name。
这就是多人协作的工作模式，一旦熟悉了，就非常简单。
#查看远程库信息，使用git remote -v；
#本地新建的分支如果不推送到远程，对其他人就是不可见的；
#从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；
#在本地创建和远程分支对应的分支，使用git checkout -b branch-name origin/branch-name，本地和远程分支的名称最好一致；
----------------------------------------------------------
标签管理
命令git tag <name>用于新建一个标签，默认为HEAD，也可以指定一个commit id；
git tag -a <tagname> -m "blablabla..."可以指定标签信息；
git tag -s <tagname> -m "blablabla..."可以用PGP签名标签；
命令git tag可以查看所有标签。
命令git push origin <tagname>可以推送一个本地标签；
命令git push origin --tags可以推送全部未推送过的本地标签；
命令git tag -d <tagname>可以删除一个本地标签；
命令git push origin :refs/tags/<tagname>可以删除一个远程标签。
----------------------------------------------------------
学习完成