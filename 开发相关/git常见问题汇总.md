### 如何添加忽略文件？
>git config core.excludesfile .gitignore_list
git status
将未添加到版本库的文件追加到 .gitignore_list 文件中即可

### 如何从暂存区(stage,index)中移除文件？
> git rm --cached file

### git 合并 commit ？
> 使用：git rebase -i HEAD~n

### 非裸仓库(bare)提交失败？
> 修改 .git/confg ，增加如下内容：  
```
[receive]  
    denyCurrentBranch = ignore  
```
或者  
`git config receive.denyCurrentBranch ignore`

### 设置本地仓库与远程仓库之间的关联关系
> git branch --set-upstream-to=origin/develop

### 使用SSH管理git仓库
1. 在 linux 服务器端：
    + 添加 git 用户组：groupadd git
    + 添加 git 用户：adduser git
    + 创建 git 仓库目录：mkdir git-repository
    + 修改 git 目录权限：chown -R git:git git-repository/
1. 在客户端：
    + git remote add origin ssh://git@ip地址/home/git/git-repository/.git
    + git branch --set-upstream-to=origin/master
1. 服务器端更新代码为最新版本
    + git reset --hard
