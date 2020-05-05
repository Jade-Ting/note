本地电脑可能会登录了多个github或其他git账户信息，操作的时候可能会出错，此时就需要检查是否连接的远程仓库是不是对应的。

#### 查看用户名和邮箱地址：

```
$ git config user.name “你的github用户名” 
$ git config user.email “你的github账号绑定的邮箱账号”
```

**或全局配置**

```
$ git config --global user.name “你的github用户名” 
$ git config --global user.email “你的github账号绑定的邮箱账号”
```

#### 修改用户名和邮箱地址：

注意：输入的时候用户名和邮箱不用引号

```
$ git config user.name “ name ” 
$ git config user.email “ email ”
```

**或全局配置**

```
$ git config --global user.name “ username ” 
$ git config --global user.email “ email ”
```

如果上面的命令错误，出现了--repalce-all这个东西。

可以尝试使用：

```
$ git config --global --replace-all user.email “ username ”  
$ git config --global --replace-all user.name “ email ”
```

#### window删除/修改本地本地git账号

（一）进入控制面板

（二）选择用户账户

（三）选择管理你的凭据

（四）选择Windows凭据

（五）选择git保存的用户信息

（六）选择编辑或者进行删除操作

（七）完成

![修改普通凭据github信息.png](https://i.loli.net/2020/05/05/SfTmYnIdFw5ateh.png)