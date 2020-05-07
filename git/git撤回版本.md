[](https://blog.csdn.net/xs20691718/article/details/51901161)

### 需要撤回已经push到远程的版本

1. 先在本地退回相应的版本

```js
git reset --hard <版本号> // 注意使用 --hard 时会抛弃当前工作去的commit

git reset --soft <版本号> // 使用 --soft 时会回退到之前的版本，但是会保留commit， 可以重新提交

// git reset --hard head^ 返回上一个版本

```
若此时直接  `git push origin <分支名>`

会提示本版本低于远程的版本

```
 ...
 ! [rejected]        ganyuting -> ganyuting (non-fast-forward)
```

2. 覆盖远程版本，（撤回远程版本）

```
git push origin <分支名> --force
```