## vscode snippets

> 自定义代码片段 [参考-vscode 官网](https://jeasonstudio.gitbooks.io/vscode-cn-doc/content/md/%E5%AE%9A%E5%88%B6%E5%8C%96/%E7%94%A8%E6%88%B7%E5%AE%9A%E4%B9%89%E4%BB%A3%E7%A0%81%E6%AE%B5.html) | [参考-简书](https://www.jianshu.com/p/1f1132df1def)

-   在页面左下角查看当前页面的语言模块（比如是 `JavaScript` 还是 `TypeScript` 等等）。
    ![查看语言模式.png](https://i.loli.net/2019/10/12/vJD8EK6cwQFndxy.png)

-   文件 -> 首选项 -> 用户片段 -> **输入刚刚查看的语言模式** -> 选择对应的语言模式后进入 json 文件。
    ![选择代码块文件.png](https://i.loli.net/2019/10/12/89xgSnFYMENJLj3.png)

-   开始创建

    ```json
        {
        // Place your snippets for javascriptreact here. Each snippet is defined under a snippet name and has a prefix, body and
        // description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
        // $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the
        // same ids are connected.


        // Example: (输入 log就可以选择 consol.log() 的代码片段)
         "Print to console": {                   // key - 可以简要说明片段用意，可以用片段名相同

         	"prefix": "log",                       // 片段名

         	"body": [                              // 片段内容 每一行都要带引号，多行代码的用逗号隔开
         		"console.log('$1');",              // $1 表示光标初始位置
         		"$2"                               // $2 表示按下 tab 键光标跳的位置， 还可以有 $3, $4……
         	],

         	"description": "Log output to console" // 描述片段作用，在选中使用片段的时候片段名后面会显示，没有description的话会显示前面的key
         }

    }
    ```

【注意】字符串里如果包含特殊字符需要 `\` 进行转义

    - 换行： \r 或 \n
    - tab键制表符： \t


### 编写代码片段

- 编写一个引入react的代码块
```json
// javascriptreact.json
{
	"react": {
		"prefix": "react",
		
		"body": [
			"import React, {Components} from 'react';",
			"\nexport default class $1 extends Components {",
			"\n\tconstructor(props) {",
			"\t\tsuper(props);",
			"\n\t\tthis.state = {",
			"\t\t\t$2",
			"\t\t}",
			"\t}",
			"\ntrender() {",
			"\t\treturn $3",
			"\t}",
			"}",
		],
		
		"description": "new component"
	}
}
```

- 编写完成后，返回js文件

- 使用：输入代码片段名export（这是之前的笔记，片段名用react应该更合适） -> 选中代码块
![vscode使用代码片段.png](https://i.loli.net/2019/09/27/MADZuOc6XhxeEsW.png)

- 就会生成对应的代码块
![使用代码片段生成.png](https://i.loli.net/2019/09/27/w9dcvuqyfS4G6i5.png)

- 生成 $1，$2，$3即光标依次跳转的位置


> 小贴士

*vscode插件中有许多其他开发者写好的代码片段插件，可以直接在插件中搜索 `snippets` 找到自己喜欢的代码快片段直接使用*