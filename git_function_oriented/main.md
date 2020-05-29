# Git 功能

## 本地切换分支

```sh
# 本地创建远程分支，绑定 up-stream，并切换
git checkout --track remotes/origin/branch-one
# 验证
git branch -vva
```

## 新建仓库

```sh
git remote add origin <ssh/http link>
# 设置本地的同名 branch master 的 upstream 到 origin 的 master
git branch --set-upstream-to=origin/master
# 查看结果
git branch -vva

git fetch

git rebase

git push
```

这里有一点想说如果我在 branch A 操作 rebase，那么 A 的 ahead 就会放到后边。