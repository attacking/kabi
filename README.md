# Chrome插件编写简明步骤


>官网是最可信的参考，这li是链接：[https://developer.chrome.com/extensions/getstarted](https://developer.chrome.com/extensions/getstarted)

###1 编写chrome指定好名称和内容的manifest.json文件

	{
    "manifest_version": 2, //建议设置为2
    "name": "Fill Form",
    "version": "1.2",
    "description": "do it.",
    "browser_action": {
        "default_icon": "icon.png",  // 显示在chrome中的插件图标
        "default_popup": "popup.html"
    },
    "permissions": [
    	"activeTab"
    ],
    "content_scripts": [
        {
            "matches": [
                "https://www.baidu.com/" //匹配到该网页，插件被执行
            ],
            "css": [
                "test.css"
            ],
            "js": [
                "test.js"  //执行脚本
            ]
        }
    ]
	}

###2 编写test.js

	document.querySelector("#kw").value = "谷歌";
    
###3 在chrome中引入插件

> 官网是最可信的参考，这是链接：[https://developer.chrome.com/extensions/getstarted](https://developer.chrome.com/extensions/getstarted)

> 360的文档也是比较不错的：[http://open.chrome.360.cn/extension_dev/overview.html](http://open.chrome.360.cn/extension_dev/overview.html)

> 图灵社区一会员的文章也值得推荐：[http://www.ituring.com.cn/article/60212](http://www.ituring.com.cn/article/60212)

## 编写chrome指定好名称和内容的manifest.json文件
```
{
  "manifest_version": 2, //建议设置为2
  "name": "Super Kit",
  "version": "1.2",
  "description": "do it.",
  "browser_action": {
    "default_icon": "icon.png",  // 显示在chrome中的插件图标
    "default_popup": "popup.html"
  },
  "permissions": [
    "activeTab"
  ],
  "content_scripts": [
    {
      "matches": [
        "//www.baidu.com/" //匹配到该网页，插件被执行
      ],
      "css": [
        "test.css"
      ],
      "js": [
        "test.js"  //执行脚本
      ]
    }
  ]
}
```
## 编写test.js
```
document.querySelector("#kw").value = "谷歌";
```

## 在chrome中引入插件
>提示： manifest.json icon.png test.js等文件都要位于同一文件夹中

步骤：
1. -→chrome自定义按钮-→扩展程序
2. 选中开发者模式，-→加载扩展程序
3. 选中自己刚创建的文件夹，完工
4. 若修改了插件，需要点击重新加载按钮

这便是chrome插件开发的最核心步骤。

## 注意事项：
- html中禁止写script标签，应外部引用
