##ionic angular项目目录结构解析
按照官网教程创建项目之后会生成如下结构树：
![](/assets/824378-20170703130858128-1400330430.png)

hooks：编译cordova时自定义的脚本命令，方便整合到我们的编译系统和版本控制系统中

node_modules ：node各类依赖包

resources ：android/ios 资源（更换图标和启动动画）

src：开发工作目录，页面、样式、脚本和图片都放在这个目录下

www：静态文件

platforms：生成android或者ios安装包路径（ platforms\android\build\outputs\apk：apk所在位置）

plugins：插件文件夹，里面放置各种cordova安装的插件

config.xml: 配置文件

package.json: node安装模块时的依据

tsconfig.json: TypeScript项目的根目录，指定用来编译这个项目的根文件和编译选项

tslint.json：格式化和校验typescript

