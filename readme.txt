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
feature1分支
Creating a new branch is quick AND simple.