> 之前说过使用github page发布个人博客 [搭建githubPage的一些记录](https://jade-ting.github.io/2020/01/02/%E6%90%AD%E5%BB%BAgithubPages.html)，但除此之外，github-page还可以发布其他库的项目。

学习参考[從零開始: 用github pages 上傳靜態網站](https://medium.com/%E9%80%B2%E6%93%8A%E7%9A%84-git-git-git/%E5%BE%9E%E9%9B%B6%E9%96%8B%E5%A7%8B-%E7%94%A8github-pages-%E4%B8%8A%E5%82%B3%E9%9D%9C%E6%85%8B%E7%B6%B2%E7%AB%99-fa2ae83e6276) - 可直接查看其中的**建立其他專案Repository**

学习参考[如何用Github的gh-pages分支展示自己的项目](https://www.cnblogs.com/MuYunyun/p/6082359.html)


以下为个人实践成果~

## 一、最简单的html网页

#### 1. 新建一个仓库，先创建一个最简单的 `html` 文件

![image.png](https://i.loli.net/2020/06/12/HRO9LKMXQEB1Tap.png)

#### 2. 点击settings，进入设置，找到 GitHub Pages设置站点源（选择展示哪个分支上的文件）

![image.png](https://i.loli.net/2020/06/12/Tv6MIZg42dSYJ5U.png)

#### 3. 此时我们只有在 `master` 分支上有一个 `index.html` 文件，因此，选择master分支。

![image.png](https://i.loli.net/2020/06/12/oaukIreDbKFmwQl.png)

#### 4. 选择好分支之后，github pages就会显示 `您的网站准备发布在XXX`，点击该网址，就可以看到该网页

![image.png](https://i.loli.net/2020/06/12/k6wazxCTeLsFqOP.png)

#### 5. 可以对比看看，就是我们仓库里的html文件

![image.png](https://i.loli.net/2020/06/12/cmBP37Y6g8xKLAo.png)

---


知道服务器发布原理的同学应该就知道怎么处理复杂项目啦~就可以直接调至 [三、创建gh-pages分支，上传打包后的build文件](#三、创建gh-pages分支，上传打包后的build文件)

`二、完整的复杂项目`中有包含网页加载不出等报错情况


---

## 二、完整的复杂项目
> 现在我们已经知道将html文件上传至github，并设置GitHub pages，就可以将其展示出来。
> 因此GitHub Pages对于我们来说就相当于一个免费的服务器，如果想要展示复杂的项目（如react项目），就可以将打包后的文件上传。

#### 1. 上传复杂的项目，（使用webpack打包的项目）

![image.png](https://i.loli.net/2020/06/12/vt4S81KClu2nkda.png)

#### 2. 重新打开刚刚的网页，此时出现的是 `READNE`的内容，如果没有 `README` 文件就可能是 `404`。这是因为此时应该运行的是打包后的文件 `build` 文件夹里的html文件。因此将网页地址改为 `https://jade-ting.github.io/githubpage-examples/build/`, 在后面加上 `/build/`表示读取build文件夹

![image.png](https://i.loli.net/2020/06/12/3w8o5Ba6t29RlCT.png)


#### 3. 可以看到页面已经出现，但是 main.js报404，也就是没有找到 `main.js` 文件

我们注意到，网页的地址是`https://jade-ting.github.io/githubpage-examples/build/` 表示在`githubpage-examples`仓库下的 `build` 文件夹中，那么 `main.js` 完整的地址应该就是`https://jade-ting.github.io/githubpage-examples/build/main.js`。可以查看该地址，就得到我们的压缩文件 main.js

![image.png](https://i.loli.net/2020/06/12/lgUIebNYFhk6pzJ.png)

但是此时网页报404的地址是 `https://jade-ting.github.io/main.js`，因此找不到该文件。


#### 4. 修改项目webpack的 `publicPath`

原来的 `publicPath` 为 `/` 读取的是 `/main.js`, 因此在发布器上就是根目录地址+main.js

![image.png](https://i.loli.net/2020/06/12/TCUPWrbOSNfkw7V.png)

将`publicPath`改为 `/githubpage-examples/build/`， 重新打包

![image.png](https://i.loli.net/2020/06/12/vVfh9Ct5NqK8ygo.png)

#### 重新上传修改后的文件到github， 打开项目 `https://jade-ting.github.io/githubpage-examples/build/`

![image.png](https://i.loli.net/2020/06/12/84P96ANJ5Z7npKx.png)


如果项目中还是一样的报错，可以稍微等几分钟~githubpages更新有点延迟。如果还是不正确，请打开/build/index.html文件查看引用的路径是不是正确的。

<span id="三、创建gh-pages分支，上传打包后的build文件">

### 三、创建gh-pages分支，上传打包后的build文件

> 上面所说的GitHub Pages的站点源在master分支，github主要用于项目的存储，所以一般会上传整个项目，这样的话网页的地址就会是 `xxx.github.io/xxx/build/`,也是可行的，但总觉得`xxx.github.io/xxx/`会更加美观~（哈哈哈，只能想到这个原因），因此创建 gh-pages分支，将用于发布的 build文件夹里的内容上传到该分支。

#### 方法一：手动上传，将build文件夹中的内容重新连接到仓库，并创建gh-pages分支，上传至gh-pages分支。

#### 方法二：直接将build文件夹内容推至gh-pages分支

```bash
git subtree push --prefix=build origin gh-pages
```

会看到gh-pages分支里是build文件夹里的文件。
![image.png](https://i.loli.net/2020/06/12/KXEgQePr7bS4pO5.png)

#### 进入setting修改GitHub Pages的站点源为 gh-pages

![image.png](https://i.loli.net/2020/06/12/kejwdl4JHtEqFMG.png)

#### 进入`https://jade-ting.github.io/githubpage-examples/`, 会发现没有正确显示页面

![image.png](https://i.loli.net/2020/06/12/rnwZYXdloeSMmWJ.png)

又是main.js资源无法加载的问题，这是因为此时的main.js在仓库的根目录，因此应该是 `https://jade-ting.github.io/githubpage-examples/main.js `。这时候又要修改webpack中的配置啦~

将webpack中的publicPath修改为仓库名
![image.png](https://i.loli.net/2020/06/12/9AXphmgsadWO8uD.png)

#### 重新打包，将打包后的文件上传至gh-pages分支。

```
git add .
git commit -m ''

git subtree push --prefix=build origin gh-pages
```

![image.png](https://i.loli.net/2020/06/12/9AXphmgsadWO8uD.png)


#### 完美~