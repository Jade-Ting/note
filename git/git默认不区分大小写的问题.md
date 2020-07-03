> 一时兴起，话有点多，可以直接看解决方法，哈哈哈哈哈哈。

### 故事发生在很久很久以前
甘某某修改/添加代码时，发现，某个文件名起的不规范，于是修改。改完后直接推到github上。

但是！！！github自动构建失败了，原因是找不到路径，？？？？？

机智过人的她马（找）上（了）发（很）现（久）文件名的问题！

<div style="color: #0B99A3; font-size: 16px; font-weight: 600">git默认不区分文件名大小写。</div>

吼吼吼吼~


### 解决方法

1. 使git对文件名大小写敏感

```bash
git config core.ignorecase false
```

这时甘某某发现，再改变文件名大小写，就会看到git有记录。

于是她兴高采烈的 `git add .` | `git commit -m '我太聪明了'` | `git push`

啊啊啊，啥? 仓库里面不是改了文件名，而是增加了改过的文件，原来的也在那，变成两个文件！！！

所以，这个方法只能再手动删除下远程原来的文件了😢


2. 使用命令修改文件名

```bash
git mv oldFileName newFileName

# 如果是好几层文件夹里的文件

git mv path/oldFileName path/newFileName

# 如果报错，，嗯嗯嗯，那就强制执行吧

git mv path/oldFileName path/newFileName --force

```