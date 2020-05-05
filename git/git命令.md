- 将要提交的修改存放到暂存区(stage)

```
git add .
```

- 查看状态(本次新增/删除/修改了哪些文件)

```
git status
```

![git add](https://www.liaoxuefeng.com/files/attachments/919020074026336/0)

- 将暂存区的所有修改一次提交到分支

```
git commit -m ''
```

- 撤回commit信息

```
git reset --soft HEAD^ // 据说可以撤销commit，写的代码也依旧保留（未亲测待考证）
```

- 修改commit

```
git commit --amend
此时会进入默认vim编辑器，修改注释后保存就可以了(亲测有用)
```

![git commit](https://www.liaoxuefeng.com/files/attachments/919020100829536/0)

- 提交到远程仓库

```
git push origin xxx(分支名称)
```

- 拉取远程仓库代码

```
git pull
```

- 暂存到缓存区: 可用于开发过程中临时修复一个bug时，将已经开发的内容暂存至缓存区。

```
git stash
```

- 切换分支

```
git checkout xxx
```

- 查看分支

```
本地分支

git branch

远程分支

git branch -a
```