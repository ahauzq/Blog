# vscodeEdit

对于前端来说 vscode 是一个十分强大的开发软件,其插件系统以及强大的插件生态圈使得我们的开发变得更加快捷。

看下我目前的安装的插件
<br>![avatar](https://raw.githubusercontent.com/ahauzq/Blog/master/png/ve1.png)
<br>![avatar](https://raw.githubusercontent.com/ahauzq/Blog/master/png/ve2.png)

用户设置

````javascript
{
    // 窗口失去焦点自动保存
    "files.autoSave": "onFocusChange",
    // 控制字体系列。
    // "editor.fontFamily": "pingfang,Menlo, Monaco, 'Courier New', monospace",
    // 字体大小
    "editor.fontSize": 16,
    // tab锁紧
    "editor.tabSize": 4,
    // 行高
    //"editor.lineHeight": 18,
    // 通过使用鼠标滚轮同时按住 Ctrl 可缩放编辑器的字体
    "editor.mouseWheelZoom": false,
    // 行太长自动换行
    "editor.wordWrap": "on",
    //Windows bash终端"terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
    // 主体
    //"workbench.colorTheme": "Monokai",
    "workbench.iconTheme": "vs-seti",
    //eslint设置
    "eslint.autoFixOnSave": true,
    //"prettier.singleQuote": true,
    // 开启 eslint 支持
    "prettier.eslintIntegration": true,
    "eslint.validate": [
        "javascript",
        "javascriptreact",
        {
            "language": "vue",
            "autoFix": true
        }
    ],
    "prettier.tabWidth": 4,
    "prettier.printWidth": 120,
    // 编辑粘贴自动格式化
    // "editor.formatOnPaste": true,
    // "editor.detectIndentation": false,
    // 保存自动化
    "editor.formatOnSave": true,
    // 空格变成......
    "editor.renderWhitespace": "all",
    "window.zoomLevel": 0,
    //"javascript.format.insertSpaceBeforeFunctionParenthesis": true,
    // 使用插件格式化 html
    "vetur.format.defaultFormatter.html": "js-beautify-html",
    //让vue中的js按编辑器自带的ts格式进行格式化
    "vetur.format.defaultFormatter.js": "vscode-typescript",
    // 格式化插件的配置
    "vetur.format.defaultFormatterOptions": {
        "js-beautify-html": {
            // 页面属性对齐方式
            "wrap_attributes": "force-aligned",
        }
    },
    //"html.format.wrapAttributes": "force-expand-multiline",
    "javascript.implicitProjectConfig.experimentalDecorators": true,
    "files.associations": {
        "*.css": "postcss",
        "*.pcss": "postcss",
    },
    "markdown.styles": []
}
```
````
