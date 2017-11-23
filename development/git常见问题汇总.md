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
