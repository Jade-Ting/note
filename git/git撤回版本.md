[](https://blog.csdn.net/xs20691718/article/details/51901161)

### 需要撤回已经push到远程的版本

1. 先在本地退回相应的版本

```bash
## 返回上个版本
git reset --hard HEAD^

## 注意使用 --hard 时会抛弃当前工作去的commit
git reset --hard <版本号>

## 使用 --soft 时会回退到之前的版本，但是会保留commit， 可以重新提交
git reset --soft <版本号>


```
若此时直接  `git push origin <分支名>`

会提示本版本低于远程的版本

```bash
 ! [rejected]        ganyuting -> ganyuting (non-fast-forward)
```

2. 覆盖远程版本，（撤回远程版本）

```bash
git push origin <分支名> --force
```

### 取消回滚

当不小心回退到了其他版本（并且比希望回退到的版本早），此时，查看 `git log`，就找不到想回退的版本号。

可以使用 `git reflog(包括撤销的commit记录都在）`

查看到所有的版本号后，再使用 `git reset --hard xxx版本号` 即可。


### 退出git log - 输入 q