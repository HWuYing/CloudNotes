最近在用vscode 1.23版本的时候发现outDir不可以使用了，建议这么改吧，直接program采用编译后的文件，然后打开sourceMaps，同时在babel编译的时候自己搞--watch及时生成.map文件便于vscode索引;如果你要编译其他语言，其实可以在package.json当中添加scripts，通过tasks.json来在debug之前进行编译，下面展示出.vscode下的两个文件，此为babel方法，其他类似

.launch.json

```javascript
"configurations": [
    {
      "type": "node",
      "request": "launch",
      "name": "启动程序",
      "program": "${workspaceFolder}/lib/login.js",
      "sourceMaps": true,
      "preLaunchTask": "build" // 等于下面`label`值
    }
  ]
```

tasks.json

```javascript
```