- 将要提交的修改存放到暂存区(stage)

```bash
git add .
```

- 查看状态(本次新增/删除/修改了哪些文件)

```bash
git status
```

![git add](https://www.liaoxuefeng.com/files/attachments/919020074026336/0)

- 将暂存区的所有修改一次提交到分支

```bash
git commit -m ''
```

- 撤回commit信息

```bash
git reset --soft HEAD^ // 据说可以撤销commit，写的代码也依旧保留（未亲测待考证）
```

- 修改commit

```bash
git commit --amend
## 此时会进入默认vim编辑器，修改注释后保存就可以了(亲测有用)
```

![git commit](https://www.liaoxuefeng.com/files/attachments/919020100829536/0)

- 提交到远程仓库

```bash
git push origin xxx(分支名称)
```

- 拉取远程仓库代码

```bash
git pull
```

- 暂存到缓存区: 可用于开发过程中临时修复一个bug时，将已经开发的内容暂存至缓存区。

```bash
git stash
```

- 切换分支

```bash
git checkout xxx
```

- 查看分支

```bash
## 本地分支

git branch

## 远程分支

git branch -a
```

- 合并分支

```bash
## Administrator@PC-20191107EDRI MINGW64 /f/test (dev) - 当前分支

## 若当前分支需要合并master分支的内容

git merge master

## 这样master的内容就会被合并到dev的分支上
```

- 解决合并冲突 - 多人开发时，拉取分支新增的内容时可能会出现冲突

```bash
## 查看冲突
< 方法1. vscode中的源代码（git）管理的【合并】一栏就是冲有突的文件
< 方法2. 可以直接在全局搜索中使用 <<< 查找冲突

## 解决冲突

< 可以保留本地修改，也可以保留传入的修改(新拉取的分支内容)

## 保存合并 - 该动作是因为本人需要切换到其他分支

git add .

git commit -m ''
```
