一、git 基本操作
1、安装git 一直回车
2、配置 user 信息
git config --global user.name 'coliy'
git config --global user.email '651192718@qq.com'

3、创建git仓库：git init 代码管理平台
4、使用git add docker安装Gogs.md 添加到暂存区
5、用git commit告诉Git,把文件提交到仓库：git commit -m 'git 使用教程'
6、修改git使用教程后可以 通过 git diff 和仓库比较文件的修改
7、全部添加文件到仓库：git commit -a -m '全部添加'
8、查看仓库最小信息：git log --pretty=oneline
9、回退上一个版本：git reset --hard HEAD^ 如果回退上上个版本 git reset --hard HEAD^^ 如果退回前100个版本话git reset --hard HEAD~100，如果想退回最新版本 用git reflog 查看版本号，通过git reset --hard 1c74e63 恢复
10、Git撤销文件修改：
    查看git status  可以发现，Git会告诉你，git checkout -- file 可以丢弃工作区的修改
11、删除文件 git rm 文件。
12、修改文件一起提交：git add -u 可以直接添加所有已经追踪的文件，用 -u 有个好处，避免把工作区没准备好的新文件直接加到暂存区了
13、文件重命名 ：git mv
14、查看历史 git log
•    git log --all 查看所有分支的历史
•    git log --all --graph 查看图形化的 log 地址
•    git log --oneline 查看单行的简洁历史。
•    git log --oneline -n4 查看最近的四条简洁历史。
•    git log --oneline --all -n4 --graph 查看所有分支最近 4 条单行的图形化历史。
•    git help --web log 跳转到git log 的帮助文档网页

二、远程仓库
1、创建SSH key ：ssh-keygen -t rsa -C "651192718@qq.com" 一直回车。
2、在github 添加 公钥id_rsa.pub，在github 创建远程仓库。
3、查看远程仓库： git remote -v
4、删除远程仓库： git remote remove origin
5、添加远程仓库 ：
git remote add origin https://github.com/dpjkflyq/-.git
6、把本地仓库推送远程仓库： git push -u origin master
