# project01
# Git学习记录
---------
## Git配置
- git config --global user.name 你的英文名
- git config --global user.email 你的邮箱
- git config --global push.default simple
- git config --global core.quotepath false
- git config --global core.editor "code --wait"
- git config --global core.autocrlf input
1.ps:英文名和邮箱跟 GitHub 无关，不过邮箱要真实存在。
2.保证 `code` 是可以直接在命令行执行的;如果不能执行，你需要安装 VSCode 并配置 PATH。PATH(环境变量的上面设置)里添加VSCode的绝对路径。
3.要设置VSCode里Terminal默认打开Git bash,在` Terminal>Integrated>Shell:Windows ` ,修改settings.json,添加` "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe", 
"editor.fontSize": 18 `
-------
## Git本地仓库
1. `git init` 初始化本地仓库->记得是在对应的项目文件夹下使用
2. `git add`文件名 添加即将commit的文件; ` git add .`添加当前文件夹下文件
3. (可忽视)`code 文件名` 进入VSCode里修改文件
4. 创建`.gitignore`文件，在该文件下所写的文件名均不需要提交,常有`node_modules`、`.DS_Store`、`.idea`、`.vscode`
5. `git commit -m` 字符串：commit提交修改;
   `git commit -v` 进入VSCode修改添加commit备注; -v意思为--verbose
6. `git log`查看当前版本以及之前的记录; `git reflog`可以查看全部修改的日志记录
7. `git reset --hard 代码版本号` :跳回到所属版本的代码进度，ps:版本号是前六位,使用前请把所有代码commit完，否则会消失;
8. `git branch 分支名称`: 创建分支
9. `git checkout 分支名`: 进入该分支; `git checkout`: 查看所有分支;
10. 在哪个分支，commit提交就会提交给当前的分支;若分支之间产生冲突，可以通灵术git stash,也可以合并冲突;
11. `git merge`: 将该分支合并到当前分支;若产生冲突时，根据conflict提示修改;使用git staus -sb 查看哪个文件冲突; 删除带>>>或者====以及要删除的;再git add，重复修改冲突直至可以commit;合并完git branch -d x
-------
## Git远程仓库
1. `ssh-keygen -t rsa -b 4096 -C 你的邮箱`: 生成SSH Key
2. `cat ~/.ssh/id_rsa.pub`: 得到公钥内容-->粘贴到Github上的公钥
3. `ssh -T git@github.com`: 测试配对成功-->yes
4. 新建Github Repo,复制SSH地址
5. `git remote add origin git@SSH地址`: 在本地添加远程仓库地址; origin为远程仓库的默认名字，可以换;
6. `git push -u origin master `: 推送本地当前分支到远程origin的master；只第一次需要，后续写`git push`；如果提示`git push`就运行一下
7. `git push origin x:x`x———>x的上传方式；`git checkout x  git push -u origin x`:第二种
8. `git clone git@hhtps的地址`: 下载他人的库;`cd 目录`;`git add \commit \pull \push`
9. [难记的命令]:(https://stackoverflow.com/questions/1778088/how-do-i-clone-a-single-branch-in-git/7034921#7034921)
