## git 常用命令
### 修改上一次提交
```
git commit --amend
```

### 覆盖已经push的提交，配合上面的命令
```
push -f
```
### 检测远程仓库是否有代码更新(例如检测远程master分支)
```
git fetch origin master
```
检测远程分支有更新后，合并远程分支更新或者解决冲突即可 `git merge origin/master`
